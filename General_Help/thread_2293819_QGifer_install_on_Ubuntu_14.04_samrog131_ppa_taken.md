---
title: "QGifer install on Ubuntu 14.04 samrog131 ppa taken down"
date: 2015-09-07
forum: General Help
---

### Post by budworthtdog2 on 2015-09-07
[FONT=Liberation Mono, monospace]I recently did a fresh install of Ubuntu 14.04 64bit. I tried installing QGifer but ran into a problem with the install process. All of the install instructions I can find for installing it as are follows. [/FONT] 



 [FONT=Liberation Mono, monospace]$ sudo add-apt-repository ppa:samrog131/ppa
$ sudo apt-get update
$ sudo apt-get install qgifer[/FONT]
 

 [FONT=Liberation Mono, monospace]I know these commands have worked in the past but the issue is that samrog131 took down the ppa I need. I have found forums of people having issues installing software that requires the samrog131 ppa but none of which pertained to QGifer in particular. The only .deb download for QGifer I could find is a 32 bit version but I have a 64bit install. [/FONT] 

 

 [FONT=Liberation Mono, monospace]Anyone have any advice for getting this installed? [/FONT]

---

### Post by XBNCPRk on 2015-09-07
Have you looked through [http://ubuntuforums.org/showthread.php?t=2289581](http://ubuntuforums.org/showthread.php?t=2289581) ? Youre not the only one to run into this issue apparently...

It looks as though hes taken down his ppa for good as he no longer uses *buntu.

---

### Post by budworthtdog2 on 2015-09-07
Yeah I saw that thread. While they were dealing with the same issue in the sense that samrog took down his PPAs they were having issues with installing FFmpeg, For kicks I tried installing the PPA they were talking about in that thread to see if it would then let me install QGifer but it did not.

---

### Post by XBNCPRk on 2015-09-07
It looks though as though qgifer itself hasnt been updated in almost two years...unless theres very pressing reasons not to, you may wish to avoid problems with any current/future compatibility for dependencies and just switch to a supported editor.  (I know, not the best answer to give, but most likely the easiest now and in the future.)

---

### Post by mc4man on 2015-09-07
There is a fork that's active, you should be able to build it pretty easy (not sure I want to ppa it...
[https://github.com/Apkawa/QGifer](https://github.com/Apkawa/QGifer)
If you need help ask

---

### Post by coldraven on 2015-09-08
> **mc4man said:**
> There is a fork that's active, you should be able to build it pretty easy (not sure I want to ppa it...
[https://github.com/Apkawa/QGifer](https://github.com/Apkawa/QGifer)
If you need help ask

I used git clone to get the folder but I cannot find out which version of qt is installed. Synaptic shows a lot of qt related things, some are version 4:4.8 and some are 5.2.1. That's a bit confusing, is 4:4.8 version 4.4 or 4.8?

```
qmake --version
qmake: could not exec '/usr/lib/x86_64-linux-gnu/qt4/bin/qmake': No such file or directory

```

---

### Post by mc4man on 2015-09-08
> **coldraven said:**
> I used git clone to get the folder but I cannot find out which version of qt is installed. Synaptic shows a lot of qt related things, some are version 4:4.8 and some are 5.2.1. That's a bit confusing, is 4:4.8 version 4.4 or 4.8?

```
qmake --version
qmake: could not exec '/usr/lib/x86_64-linux-gnu/qt4/bin/qmake': No such file or directory

```
I think it'll use qt4  - here, (14.04),  I have both qt4 & qt5, qt5 is the default for qmake but it seems to use the qt4 qmake - 

> -- Found Qt4: /usr/bin/qmake-qt4 (found version "4.8.6") 

So install qt4-qmake, screen show here

---

### Post by coldraven on 2015-09-09
Thanks mc4man, I installed qmake  but I'm getting another error.
I'm following the instructions in the README.md file, I installed all the follwing
> Requirements
============

 * Qt version 4.8.0, or higher.
 * OpenCV (core, highgui, imgproc) version 2.3 or higher.
 * giflib version 4.1 or higher.
 * CMake version 2.6 or higher.




```
qmake --version
QMake version 2.01a
Using Qt version 4.8.6 in /usr/lib/x86_64-linux-gnu


coldraven@happy:~$ cd QGifer/
coldraven@happy:~/QGifer$ cd build/

coldraven@happy:~/QGifer/build$ cmake .. -DCMAKE_INSTALL_PREFIX="/usr/local/" -DQUIET_MODE=ON
-- The CXX compiler identification is unknown
CMake Error: your CXX compiler: "CMAKE_CXX_COMPILER-NOTFOUND" was not found.   Please set CMAKE_CXX_COMPILER to a valid compiler path or name.
CMake Error at CMakeLists.txt:51 (FIND_PACKAGE):
  By not providing "FindOpenCV.cmake" in CMAKE_MODULE_PATH this project has
  asked CMake to find a package configuration file provided by "OpenCV", but
  CMake did not find one.

  Could not find a package configuration file provided by "OpenCV" with any
  of the following names:

    OpenCVConfig.cmake
    opencv-config.cmake

  Add the installation prefix of "OpenCV" to CMAKE_PREFIX_PATH or set
  "OpenCV_DIR" to a directory containing one of the above files.  If "OpenCV"
  provides a separate development package or SDK, be sure it has been
  installed.


-- Configuring incomplete, errors occurred!
See also "/home/coldraven/QGifer/build/CMakeFiles/CMakeOutput.log".
See also "/home/coldraven/QGifer/build/CMakeFiles/CMakeError.log".
```

If I attempt to install libopencv-dev it wants to also install lots of other stuffbut not opencv-config.cmake that's mentioned above.

---

### Post by mc4man on 2015-09-09
> **coldraven said:**
> Thanks mc4man, I installed qmake  but I'm getting another error.
I'm following the instructions in the README.md file, I installed all the follwing
-- The CXX compiler identification is unknown

try installing 
```
sudo apt-get install build-essential
```
Otherwise  a very temp build for 14.04 [will be here]("https://launchpad.net/~mc3man/+archive/ubuntu/quick-tests1"), may move [to here]("https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media") if it works ok.
Small possible issue - the source only provides a 128x128 .xpm icon, is ok in unity, may be too big for menu type env. I've no interest in creating some .png's or a .svg.

---

