---
title: "cmake issue"
date: 2015-11-16
forum: General Help
---

### Post by elm3 on 2015-11-16
Good afternoon everyone,

I'm trying to build a program ([pygimli]("http://www.pygimli.org/")) using cmake, on 14.04 but up to know failed to do so.

I obtain the following issue:
"CMake Error at CMakeLists.txt:17 (project):
  No CMAKE_C_COMPILER could be found.

  Tell CMake where to find the compiler by setting the CMake cache entry
  CMAKE_C_COMPILER to the full path to the compiler, or to the compiler name
  if it is in the PATH.


CMake Error at CMakeLists.txt:17 (project):
  No CMAKE_CXX_COMPILER could be found.

  Tell CMake where to find the compiler by setting the CMake cache entry
  CMAKE_CXX_COMPILER to the full path to the compiler, or to the compiler
  name if it is in the PATH.


CMake Error: CMAKE_C_COMPILER not set, after EnableLanguage
CMake Error: CMAKE_CXX_COMPILER not set, after EnableLanguage
"

in ~/.zshrc I export CC to gcc and CXX to g++
cmake -D CMAKE_C_COMPILER=GCC -D CMAKE_CXX_COMPILER=g++ ../trunk
doesn't work 

I don't get why Cmake doesn't get the proper one when it compile, I'm forcing it...

Any idea on it ?

Thanks a lot

e

---

### Post by elm3 on 2015-11-16
Has been solved by myself.

Thanks

e

---

### Post by oldos2er on 2015-11-16
It would be most helpful if you would post the solution, and mark the thread 'Solved' under Thread Tools.

---

