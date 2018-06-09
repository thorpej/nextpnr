nextpnr -- a portable FPGA place and route tool
===============================================

Supported Architectures
-----------------------

- iCE40

Prequisites
-----------
 
 - CMake 3.3 or later
 - Modern C++11 compiler, clang recommended (`clang-format` required for development)
 - Qt5 or later (`qt5-default` for Ubuntu 16.04)
 - Python 3.5 or later, including development libraries (`python3-dev` for Ubuntu)
 - Boost libraries (`libboost-dev` or `libboost-all-dev` for Ubuntu)
 - Icestorm, with chipdbs installed in `/usr/local/share/icebox`
 - Latest git Yosys is required to synthesise the demo design
 
Building
--------

 - Use CMake to generate the Makefiles (only needs to be done when `CMakeLists.txt` changes)
    - For a debug build, run `cmake -DCMAKE_BUILD_TYPE=Debug .`
    - For a debug build with HX1K support only, run ` cmake -DCMAKE_BUILD_TYPE=Debug -DICE40_HX1K_ONLY=1 .`
    - For a release build, run `cmake .`
 - Use Make to run the build itself
    - For all targets, just run `make`
    - For just the iCE40 CLI binary, run `make nextpnr-ice40`
    - For just the iCE40 Python module, run `make nextpnrpy_ice40`
    - Using too many parallel jobs may lead to out-of-memory issues due to the significant memory needed to build the chipdbs

Running
--------

 - To run the CLI binary, just run `./nextpnr-ice40` (you should see command line help)
 - To start the UI, run `./nextpnr-ice40 --gui`
 - The Python module is called `nextpnrpy_ice40.so`. To test it, run `PYTHONPATH=. python3 python/python_mod_test.py`

Notes
-------
 
 - All code is formatted using `clang-format` according to the style rules in `.clang-format` (LLVM based with 
 increased indent widths and brace wraps after classes).
 - To automatically format all source code, run `make clangformat`.