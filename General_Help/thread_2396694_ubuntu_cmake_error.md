---
title: "ubuntu cmake error"
date: 2018-07-19
forum: General Help
---

### Post by n0nename on 2018-07-19
[B]hi 
i have some problem while cmake
this is the message about cmake error[/B]

[COLOR=#000000][FONT=Gulim]-- The C compiler identification is GNU 5.4.0[/FONT][/COLOR]
[COLOR=#000000][FONT=Gulim]-- The CXX compiler identification is GNU 5.4.0[/FONT][/COLOR]
[COLOR=#000000][FONT=Gulim]-- Check for working C compiler: /usr/bin/cc[/FONT][/COLOR]
[COLOR=#000000][FONT=Gulim]-- Check for working C compiler: /usr/bin/cc -- works[/FONT][/COLOR]
[COLOR=#000000][FONT=Gulim]-- Detecting C compiler ABI info[/FONT][/COLOR]
[COLOR=#000000][FONT=Gulim]-- Detecting C compiler ABI info - done[/FONT][/COLOR]
[COLOR=#000000][FONT=Gulim]-- Detecting C compile features[/FONT][/COLOR]
[COLOR=#000000][FONT=Gulim]-- Detecting C compile features - done[/FONT][/COLOR]
[COLOR=#000000][FONT=Gulim]-- Check for working CXX compiler: /usr/bin/c++[/FONT][/COLOR]
[COLOR=#000000][FONT=Gulim]-- Check for working CXX compiler: /usr/bin/c++ -- works[/FONT][/COLOR]
[COLOR=#000000][FONT=Gulim]-- Detecting CXX compiler ABI info[/FONT][/COLOR]
[COLOR=#000000][FONT=Gulim]-- Detecting CXX compiler ABI info - done[/FONT][/COLOR]
[COLOR=#000000][FONT=Gulim]-- Detecting CXX compile features[/FONT][/COLOR]
[COLOR=#000000][FONT=Gulim]-- Detecting CXX compile features - done[/FONT][/COLOR]
[COLOR=#000000][FONT=Gulim]-- Looking for pthread.h[/FONT][/COLOR]
[COLOR=#000000][FONT=Gulim]-- Looking for pthread.h - found[/FONT][/COLOR]
[COLOR=#000000][FONT=Gulim]-- Looking for pthread_create[/FONT][/COLOR]
[COLOR=#000000][FONT=Gulim]-- Looking for pthread_create - not found[/FONT][/COLOR]
[COLOR=#000000][FONT=Gulim]-- Looking for pthread_create in pthreads[/FONT][/COLOR]
[COLOR=#000000][FONT=Gulim]-- Looking for pthread_create in pthreads - not found[/FONT][/COLOR]
[COLOR=#000000][FONT=Gulim]-- Looking for pthread_create in pthread[/FONT][/COLOR]
[COLOR=#000000][FONT=Gulim]-- Looking for pthread_create in pthread - found[/FONT][/COLOR]
[COLOR=#000000][FONT=Gulim]-- Found Threads: TRUE  [/FONT][/COLOR]
[COLOR=#000000][FONT=Gulim]-- Found CUDA: /usr/local/cuda-8.0 (found suitable exact version "8.0") [/FONT][/COLOR]
[COLOR=#000000][FONT=Gulim]-- Found OpenCV: /usr (found version "3.2.0") [/FONT][/COLOR]
[COLOR=#000000][FONT=Gulim]-- Found CUDA: /usr/local/cuda-8.0 (found version "8.0") [/FONT][/COLOR]
[COLOR=#000000][FONT=Gulim]CMake Error at /usr/share/cmake-3.5/Modules/FindPackageHandleStandardArgs.cmake:148 (message):[/FONT][/COLOR]
[COLOR=#000000][FONT=Gulim]  Could NOT find PythonLibs (missing: PYTHON_LIBRARIES PYTHON_INCLUDE_DIRS)[/FONT][/COLOR]
[COLOR=#000000][FONT=Gulim]  (Required is at least version "2.7")[/FONT][/COLOR]
[COLOR=#000000][FONT=Gulim]Call Stack (most recent call first):[/FONT][/COLOR]
[COLOR=#000000][FONT=Gulim]  /usr/share/cmake-3.5/Modules/FindPackageHandleStandardArgs.cmake:388 (_FPHSA_FAILURE_MESSAGE)[/FONT][/COLOR]
[COLOR=#000000][FONT=Gulim]  /usr/share/cmake-3.5/Modules/FindPythonLibs.cmake:265 (FIND_PACKAGE_HANDLE_STANDARD_ARGS)[/FONT][/COLOR]
[COLOR=#000000][FONT=Gulim]  yolo++/CMakeLists.txt:24 (find_package)

[B]my python version is 2.7.5
How can i solve the problem
please help me.
[/B][/FONT][/COLOR][COLOR=#000000][FONT=&amp]
[/FONT][/COLOR]

---

### Post by steeldriver on 2018-07-19
Hello and welcome to the forums

It would be helpful to include information about the software that you are trying to build

My *guess *is that you need to install the python-dev package

---

