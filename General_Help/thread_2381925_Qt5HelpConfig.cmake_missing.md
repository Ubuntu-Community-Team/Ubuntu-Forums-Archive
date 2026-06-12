---
title: "Qt5HelpConfig.cmake missing"
date: 2018-01-06
forum: General Help
---

### Post by babakflame on 2018-01-06
Dear Fellows

 I am trying to install paraview according to this link:

[https://www.paraview.org/Wiki/ParaView:Build_And_Install](https://www.paraview.org/Wiki/ParaView:Build_And_Install)

What I did was first building and installing cmake and qt5 which are the prerequisites, as:

```
cd $HOME
wget http://www.cmake.org/files/v3.9/cmake-3.9.6.tar.gz
tar xvfz cmake-3.9.6.tar.gz
cd cmake-3.9.6
./configure --prefix=$HOME/software
make
make install
```


and qt5 from this link:
[https://www.ics.com/blog/how-compile-qt-source-code-linux](https://www.ics.com/blog/how-compile-qt-source-code-linux)

Then I started installing paraview:

At the final stages (95% configuring), this error pops up:

```

CMake Error at /usr/lib/x86_64-linux-gnu/cmake/Qt5/Qt5Config.cmake:26
 (find_package):
   Could not find a package configuration file provided by "Qt5Help" with any
   of the following names:

     Qt5HelpConfig.cmake
     qt5help-config.cmake

   Add the installation prefix of "Qt5Help" to CMAKE_PREFIX_PATH or set
   "Qt5Help_DIR" to a directory containing one of the above files. 


```

would anybody help me how I can resolve this issue? (My ubuntu version is 16.04)
Regards

---

### Post by babakflame on 2018-01-06
Dear Fellows

For the people who might have the same issue as me. I used apt-file command to search for related and missed packages as described in this link:

[https://askubuntu.com/questions/374755/what-package-do-i-need-to-build-a-qt-5-cmake-application](https://askubuntu.com/questions/374755/what-package-do-i-need-to-build-a-qt-5-cmake-application)

 Regards

---

