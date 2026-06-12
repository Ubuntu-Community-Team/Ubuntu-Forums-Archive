---
title: "Can't Install qtbase5-dev 5.6.1"
date: 2017-07-13
forum: General Help
---

### Post by taiden2 on 2017-07-13
Hi guys!


I'm quite new using ubuntu and I'm trying to install Paraview 5.4 because I'm learning OpenFOAM (CFD software). When I try to install it, installation breaks and returns an error saying that I need qtbase5-dev version 5.6. 


I installed qtbase5-dev from synaptic but it's an older version and synaptic doesn't recognise v-5.6.1 which is that I need. 

Sorry for my bad english and thanks a lot!!:D

Diego.

---

### Post by dragonfly41 on 2017-07-13
It is true that the Synaptic version lags behind.   In my Ubuntu 16.04 Synaptic Qt5 is version 5.5.1.

I would bypass Synaptic and download Qt 5.6 online installer (open source, not the commercial free trial) from [here]("https://info.qt.io/download-qt-for-application-development").

Another approach is to install conda ([miniconda]("https://conda.io/miniconda.html") is the lighter version of Anaconda) and install Qt 5.6 in its own environment via conda,

---

### Post by monkeybrain20122 on 2017-07-13
You can install openfoam with bundled paraview from ppa see [https://openfoam.org/download/4-1-ubuntu/](https://openfoam.org/download/4-1-ubuntu/)
You can also get a docker image from the same site.

---

### Post by taiden2 on 2017-07-14
> **dragonfly41 said:**
> It is true that the Synaptic version lags behind.   In my Ubuntu 16.04 Synaptic Qt5 is version 5.5.1.

I would bypass Synaptic and download Qt 5.6 online installer (open source, not the commercial free trial) from [here]("https://info.qt.io/download-qt-for-application-development").

Another approach is to install conda ([miniconda]("https://conda.io/miniconda.html") is the lighter version of Anaconda) and install Qt 5.6 in its own environment via conda,

Thanks for the reply. 
You are right, I'm using Ubuntu 16.04 LTS and Synaptic QT5 versions is 5.5.1. I tryed to install Qt 5.6 open source version as you said but I still have this problem:

```

CMake Error at CMake/ParaViewQt.cmake:65 (find_package):
  Could not find a configuration file for package "Qt5" that is compatible
  with requested version "5.6".


  The following configuration files were considered but not accepted:


    /usr/lib/x86_64-linux-gnu/cmake/Qt5/Qt5Config.cmake, version: 5.5.1
    /usr/lib/x86_64-linux-gnu/cmake/Qt5/Qt5Config.cmake, version: 5.5.1


Call Stack (most recent call first):
  Qt/Widgets/CMakeLists.txt:203 (pv_find_package_qt)



```

> 
[COLOR=#000000]You can install openfoam with bundled paraview from ppa see [/COLOR][https://openfoam.org/download/4-1-ubuntu/](https://openfoam.org/download/4-1-ubuntu/)
[COLOR=#000000]You can also get a docker image from the same site.
[/COLOR][COLOR=#000000]
Thanks for your reply! 
I have installed OpenFOAM with Third-Parties but I want to upgrade to Paraview 5.4 insted of Paraview 5.0.1 installed by default.[/COLOR]

---

### Post by monkeybrain20122 on 2017-07-14
[COLOR=#000000]
> I have installed OpenFOAM with Third-Parties but I want to upgrade to Paraview 5.4 insted of Paraview 5.0.1 installed by default.[/COLOR]


If you install from the link I posted you should get at least Paraview 5.3 (probably upgraded to 5.4 now) Paraview is patched in OF so if you just install paraview it may not work with OF. 

I have compiled paraview 5.4 against qt5.9.1 in Ubun16.04 but I also compiled qt from source and it took a long time.

I don't know whether that qt5.6 you downloaded is just the binaries, you need also the shared libraries to compile other applications. If it has the shared libs, you still need to configure paraview to see them since your downloaded qt is not in the default location, or paraview will try to just use the system version of qt which doesn't work.

Here is my cmake line for building paraview
```
cmake -DCMAKE_INSTALL_PREFIX=$HOME/opt/paraview -DCMAKE_BUILD_TYPE=Release -DBUILD_SHARED_LIBS=ON -DPARAVIEW_USE_MPI=ON -DPARAVIEW_BUILD_QT_GUI=ON \
-DPARAVIEW_ENABLE_CATALYST=ON -DPARAVIEW_ENABLE_XDMF3=ON \
-DVTK_RENDERING_BACKEND=OpenGL2 -DVTK_SMP_IMPLEMENTATION_TYPE=OpenMP \
-DPARAVIEW_QT_VERSION=5 -DQt5_DIR=$HOME/opt/qt5/lib/cmake/Qt5 -DQT_QMAKE_EXECUTABLE=$HOME/bin/qmake-qt5 -DPARAVIEW_ENABLE_FFMPEG=ON \
-DPARAVIEW_USE_VISITBRIDGE=ON -DPARAVIEW_ENABLE_PYTHON=ON -DBUILD_EXAMPLES=ON -DPARAVIEW_INSTALL_DEVELOPMENT_FILES=ON ..
```


Note the cmake options that specify where paraview should look for qt
```
-DPARAVIEW_QT_VERSION=5 -DQt5_DIR=$HOME/opt/qt5/lib/cmake/Qt5 -DQT_QMAKE_EXECUTABLE=$HOME/bin/qmake-qt5


```

I installed qt 5.9.1 in $HOME/opt/qt5 and made a symlink of $HOME/opt/qt5/bin/qmake to $HOME/bin/qmake-qt5 

Adjust your paths according to where your qt-5.6 is.

---

### Post by dragonfly41 on 2017-07-14
I would follow advice from @monkeybrain20122 who clearly has experience in installing Paraview.

But to try to answer your earlier question about Qt5 ..

```
Could not find a configuration file for package "Qt5" that is compatible
  with requested version "5.6".
```

I would uninstall/purge Qt5 installations before starting a fresh Qt5 installation since there
may be conflicts across versions. 

The miniconda approach does allow different versions of Qt5 to be installed. But miniconda has its own quirks.

[FONT=Verdana]
[/FONT]

---

### Post by monkeybrain20122 on 2017-07-15
I just found out that you can download a precompiled binary for Paraview. [https://www.paraview.org/download/](https://www.paraview.org/download/). Type of Download > Paraview binary installer (actually no installation required). Operating System > Linux 64 bits 


Just untar and go to bin and click paraview. To use it with OF you would need to configure OF to detect it , which you would have to do anyway if you are not using the bundled version in OF. You don't have to worry about qt and cmake. :)

---

