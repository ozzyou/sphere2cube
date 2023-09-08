sphere2cube [![PyPI version](https://badge.fury.io/py/sphere2cube.svg)](https://pypi.python.org/pypi/sphere2cube) [![PyPI](https://img.shields.io/pypi/pyversions/sphere2cube.svg)](https://pypi.python.org/pypi/sphere2cube)
===========

`sphere2cube` is a Python script to map equirectangular (cylindrical
projection, skysphere) map into 6 cube (cubemap, skybox) faces. See also
[`cube2sphere`](https://github.com/Xyene/cube2sphere). This is a slightly
adjusted repository to process multiple inputs at once.

Usage
=====

    $ sphere2cube -h
    usage: sphere2cube [-h] [-v] [-r <size>] [-R <rx> <ry> <rz>] [-p <pattern>]
                       [-o <dir>] [-f <name>] [-b <path>] [-t <count>] [-V]
                       [<source>]

    Maps an equirectangular (cylindrical projection, skysphere) map into 6 cube
    (cubemap, skybox) faces.

    positional arguments:
      <source>              source equirectangular image folder

    optional arguments:
      -h, --help            show this help message and exit
      -v, --version         show program's version number and exit
      -r <size>, --resolution <size>
                            resolution for each generated cube face (defaults to 1024)
      -R <rx> <ry> <rz>, --rotation <rx> <ry> <rz>
                            rotation in degrees to apply before rendering cube
                            faces (z is up)
      -F <angle>, --fov <angle>
                            field of view of camera used for rendering cube faces
      -p <pattern>, --path <pattern>
                            filename pattern for rendered faces: default is
                            "face_%n_%r", where %n is replaced by the face number
                            and %r by the resolution
      -o <dir>, --output-dir <dir>
                            directory to save rendered faces to (it must already
                            exist)
      -f <name>, --format <name>
                            format to use when saving faces, i.e. "PNG" or "TGA"
      -b <path>, --blender-path <path>
                            filename of the Blender executable (defaults to
                            "blender")
      -t <count>, --threads <count>
                            number of threads to use when rendering (1-64)
      -V, --verbose         enable verbose logging

Supported output formats depend on the Blender installation, but will
generally be TGA, IRIS, JPEG, MOVIE, IRIZ, RAWTGA, AVIRAW, AVIJPEG, PNG,
BMP, and FRAMESERVER.

`sphere2cube` can be run in a headless environment (e.g., a server).

Example
========

    $ sphere2cube <input_folder> -o <output_folder> -b <blender executable> -f PNG

This loops over all panoramic images in `input_folder` and stores them per image in the `output_folder`.

Installation
============

Clone the directory and run `pip install ./sphere2cube`. It requires a Python 3
installation, and at least [Blender 2.8](https://www.blender.org/).

It assumes that Blender is installed and the `blender` executable is
listed in the system PATH environment variable. If it is not possible
for PATH to be edited (as in the case of an unprivileged user), the path
to the `blender` executable may instead be passed through the `-b` flag.
