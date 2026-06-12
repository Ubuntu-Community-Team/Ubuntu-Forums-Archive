---
title: "Help installing fatrat download manager 16.04"
date: 2016-05-06
forum: General Help
---

### Post by insane9 on 2016-05-06
Hi all, can anyone give me a helping hand. I'm trying to install fatrat download manager. It uses 'cmake' to install the software.

Source of software: [https://github.com/LubosD/fatrat](https://github.com/LubosD/fatrat)

I get the following error:

```
:~/Desktop/fatrat-master$ cmake . -DWITH_BITTORRENT=ON -DWITH_SFTP=ON
-- Could NOT find Boost
CMake Error at CMakeLists.txt:18 (find_package):
  By not providing "FindQt5Svg.cmake" in CMAKE_MODULE_PATH this project has
  asked CMake to find a package configuration file provided by "Qt5Svg", but
  CMake did not find one.


  Could not find a package configuration file provided by "Qt5Svg" with any
  of the following names:


    Qt5SvgConfig.cmake
    qt5svg-config.cmake


  Add the installation prefix of "Qt5Svg" to CMAKE_PREFIX_PATH or set
  "Qt5Svg_DIR" to a directory containing one of the above files.  If "Qt5Svg"
  provides a separate development package or SDK, be sure it has been
  installed.




-- Configuring incomplete, errors occurred!
See also "/home/simon/Desktop/fatrat-master/CMakeFiles/CMakeOutput.log".
```

Anyone?? Thanks!

---

### Post by vasa1 on 2016-05-06
> **insane9 said:**
> Hi all, can anyone give me a helping hand. I'm trying to install fatrat download manager. It uses 'cmake' to install the software. ...
Please *edit* your question to include the source of this software.

The newest version from [http://fatrat.dolezel.info/download](http://fatrat.dolezel.info/download) is from 2011. The latest source code is supposedly available from [http://git.dolezel.info/](http://git.dolezel.info/) but that link gives me a 404.

---

### Post by insane9 on 2016-05-06
Added source of software. Thanks Vasa1

---

### Post by leunam12 on 2016-05-06
Hopefully you made a backup of your hard drive (root and home) before attempting to install this. Sometimes that kind of failed installation puts a lot of trash in your system that is very hard to clean. I am talking from experience.

---

