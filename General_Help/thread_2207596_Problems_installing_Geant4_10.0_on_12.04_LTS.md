---
title: "Problems installing Geant4 10.0 on 12.04 LTS"
date: 2014-02-24
forum: General Help
---

### Post by ad00165 on 2014-02-24
Hi Everyone,

I'm relatively new to linux, I used it sporadically a few years ago so have forgot most of what i learned last time.

The problem I'm having is installing Geant4 10.0 on a clean Ubuntu install in a Oracle VirtualBox environment.

I initially tried the install instructions provided by the Geant group, [here]("http://geant4.web.cern.ch/geant4/UserDocumentation/UsersGuides/InstallationGuide/fo/BookInstalGuide.pdf"), however this did not work, citing errors with cmake
CMake Error at /usr/share/cmake-2.8/Modules/FindPackageHandleStandardArgs.cmake: 91 (MESSAGE)

After some searching I found another [walkthrough]("http://www.postcheers.com/blog/programmazione/geant4-10/") which suggested using synaptic, going through their recommendations I encountered a similar error (though slightly different due to the additional arguments. 

root@BeamsVB:/opt# ls
geant4  geant4_10  geant4-build  Qt5.2.0  VBoxGuestAdditions-4.3.6
root@BeamsVB:/opt# cmake -DCMAKE_INSTALL_PREFIX=/opt/geant4_10_00-install -DGEANT4_INSTALL_DATA=ON -DGEANT4_USE_OPENGL_X11=ON -DGEANT4_USE_QT=ON /opt/geant4_10/ 
-- The C compiler identification is GNU
-- The CXX compiler identification is GNU
-- Check for working C compiler: /usr/bin/gcc
-- Check for working C compiler: /usr/bin/gcc -- works
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
-- Check for working CXX compiler: /usr/bin/c++
-- Check for working CXX compiler: /usr/bin/c++ -- works
-- Detecting CXX compiler ABI info
-- Detecting CXX compiler ABI info - done
-- Found EXPAT: /usr/lib/i386-linux-gnu/libexpat.so 
CMake Error at /usr/share/cmake-2.8/Modules/FindPackageHandleStandardArgs.cmake:91 (MESSAGE):
  Could NOT find Qt4 (missing: QT_QMAKE_EXECUTABLE QT_MOC_EXECUTABLE
  QT_RCC_EXECUTABLE QT_INCLUDE_DIR QT_LIBRARY_DIR QT_QTCORE_INCLUDE_DIR
  QT_QTCORE_LIBRARY QT_QTGUI_INCLUDE_DIR QT_QTGUI_LIBRARY
  QT_QTOPENGL_INCLUDE_DIR QT_QTOPENGL_LIBRARY QT_UIC_EXECUTABLE)
Call Stack (most recent call first):
  /usr/share/cmake-2.8/Modules/FindPackageHandleStandardArgs.cmake:252 (_FPHSA_FAILURE_MESSAGE)
  /usr/share/cmake-2.8/Modules/FindQt4.cmake:1171 (FIND_PACKAGE_HANDLE_STANDARD_ARGS)
  cmake/Modules/Geant4InterfaceOptions.cmake:112 (find_package)
  CMakeLists.txt:83 (include)




-- Configuring incomplete, errors occurred!

Does anyone here have any experience or recommendations, make, cmake, c++ compiler and all the other programs should be up to date, either via synaptic or apt-get.

Cheers,
Alan

---

### Post by steeldriver on 2014-02-24
I don't have any experience with geant but the first thing to check is that the qt4 development libraries are installed (libqt4-dev)

---

### Post by ad00165 on 2014-02-24
I've redone everything but with 13.10 + latest updates, Qt4 seems to have sorted itself out.

However, this is the error now

CMake Error at /usr/share/cmake-2.8/Modules/FindPackageHandleStandardArgs.cmake:108 (message):
  Could NOT find EXPAT (missing: EXPAT_LIBRARY EXPAT_INCLUDE_DIR)
Call Stack (most recent call first):
  /usr/share/cmake-2.8/Modules/FindPackageHandleStandardArgs.cmake:315 (_FPHSA_FAILURE_MESSAGE)
  /usr/share/cmake-2.8/Modules/FindEXPAT.cmake:50 (FIND_PACKAGE_HANDLE_STANDARD_ARGS)
  cmake/Modules/Geant4OptionalComponents.cmake:71 (find_package)
  CMakeLists.txt:78 (include)




-- Configuring incomplete, errors occurred!



Looking into expat, i have 2.1.0-4 installed but i can not find any of the files mentioned [here]("http://hypernews.slac.stanford.edu/HyperNews/geant4/get/installconfig/1425.html?inline=-1")

This is what is apparently installed
/.
/usr
/usr/bin
/usr/bin/xmlwf
/usr/share
/usr/share/doc
/usr/share/doc/expat
/usr/share/doc/expat/changelog.Debian.gz
/usr/share/doc/expat/copyright
/usr/share/man
/usr/share/man/man1
/usr/share/man/man1/xmlwf.1.gz

---

### Post by steeldriver on 2014-02-24
You probably need the expat **development **package (libexpat1-dev?) as well as / instead of the regular runtime package

---

### Post by ad00165 on 2014-02-24
Hi,

10 hours in and it finally works, at least for the examples it provides!  Thanks for the tip steeldriver, I used the same approach for all the latter errors.

Alan

---

### Post by benpietras on 2014-09-29
I leave this here, mainly as a guide to my forgetful future self.

To install Geant4 10.0 on 14.04 (64 bit)

download  [FONT=arial]patch_geant4.10.00.p02.tar.gz and [/FONT][FONT=arial]geant4.10.00.p02.tar.gz[/FONT]
[FONT=arial]make a dir[/FONT]
[FONT=arial]untar patch_geant4.10.00.p02.tar.gz and geant4.10.00.p02.tar.gz in said dir[/FONT]
[FONT=arial]mkdir g4install  & g4build[/FONT]
[FONT=arial]cd g4build[/FONT]
[FONT=arial]sudo apt-get install cmake build-essential libgl1-mesa-dev libqt4-dev libXmu-dev zlibc libxerces-c-dev root-system
cd g4build[/FONT]
[FONT=arial]cmake -DCMAKE_INSTALL_PREFIX=/yourpath/g4install -DGEANT4_INSTALL_DATA=ON -DGEANT4_USE_GDML=ON -DGEANT4_USE_QT=ON -DGEANT4_USE_OPENGL_X11=ON /yourpath/geant4.10.00.p02
(if fails, rm -rf * in g4build before rerunning cmake)
make -j4 (the four is replaced by your number of processor cores)
make install

If all went well, add this to your ~/.bashrc
 
if [ -f /yourpath/g4install/share/Geant4-10.0.2/geant4makegeant4make.sh ]; then
    . /yourpatht/g4install/share/Geant4-10.0.2/geant4makegeant4make.sh 
fi

Ciao



[/FONT]

---

### Post by andrew186 on 2015-01-02
[**[COLOR=#000000]benpietras[/COLOR]**]("http://ubuntuforums.org/member.php?u=1847384") thank you very much for posting your instructions. They put me in the right direction for getting graphics to work with a fresh 14.04 and fresh geant install.

I wanted to just add here another version, updated for Geant4 10.1.0 and 14.04 (64-bit)

my computer is a Intel® Core&#8482;2 CPU 6420 @ 2.13GHz × 2, with Intel® G33 graphics card.
Here are a few changes I am making to [**[COLOR=#000000]benpietras[/COLOR]**]("http://ubuntuforums.org/member.php?u=1847384") instructions
   -adding -DGEANT4_USE_SYSTEM_EXPAT=OFF, since geant couldn't find this, and this is the option to have the geant compile this for you. (see reccomendation for this here: [http://geant4.web.cern.ch/geant4/UserDocumentation/UsersGuides/InstallationGuide/html/ch02s03.html](http://geant4.web.cern.ch/geant4/UserDocumentation/UsersGuides/InstallationGuide/html/ch02s03.html))
   -changing the .bashrc lines (see reccomendation for this here: [http://geant4.web.cern.ch/geant4/UserDocumentation/UsersGuides/InstallationGuide/html/ch03.html](http://geant4.web.cern.ch/geant4/UserDocumentation/UsersGuides/InstallationGuide/html/ch03.html))

After fresh 14.04 Install:

download geant4.10.01[FONT=arial].tar.gz[/FONT]
[FONT=arial]make a dir[/FONT],  let's call it [FONT=arial]/yourpath/geant4.10.01[/FONT]
[FONT=arial]untar [/FONT][FONT=arial]geant4.10.01[FONT=arial].tar.gz[/FONT] in said dir[/FONT][FONT=arial][/FONT]
[FONT=arial]mkdir g4install  & g4build[/FONT]
[FONT=arial]cd g4build[/FONT]
[FONT=arial]sudo apt-get install cmake build-essential libgl1-mesa-dev libqt4-dev libXmu-dev zlibc libxerces-c-dev root-system
cd g4build[/FONT]
[FONT=arial]cmake  -DCMAKE_INSTALL_PREFIX=/yourpath/g4install -DGEANT4_INSTALL_DATA=ON  -DGEANT4_USE_GDML=ON -DGEANT4_USE_QT=ON -DGEANT4_USE_OPENGL_X11=ON [/FONT][FONT=arial]-DGEANT4_USE_SYSTEM_EXPAT=OFF /yourpath/geant4.10.01
(if fails, rm -rf * in g4build before rerunning cmake)
make -j4 (the four is replaced by your number of processor cores)
make install

If all went well, add this to your ~/.bashrc
 
if [ -f /yourpath/g4install/bin/geant4.sh ]; then
    . /yourpatht/g4install/[/FONT][FONT=arial][FONT=arial]bin/geant4.sh[/FONT] 
fi

-Andrew[/FONT]

---

### Post by kalamaster2 on 2015-05-04
It works also for me. 
Intel(R) Core(TM) i7-2677M CPU @ 1.80GHz x4 

Ciao
----
Massimo

---

### Post by medooo on 2015-07-24
dear all 

thank you for this beneficial discussion ,
actually , I have tried to install the geant4.10.01.p02 with the same way you described here but still gives me as following :

/g/geant4.10.01.p02-build$ cmake -DCMAKE_INSTALL_PREFIX=/home/mamdouh/g/g4install -DGEANT4_INSTALL_DATA=ON -DGEANT4_USE_GDML=ON -DGEANT4_USE_QT=ON -DGEANT4_USE_OPENGL_X11=ON /home/mamdouh/g/geant4.10.01.p02
CMake Error at /usr/share/cmake-2.8/Modules/FindPackageHandleStandardArgs.cmake:108 (message):
  Could NOT find EXPAT (missing: EXPAT_LIBRARY EXPAT_INCLUDE_DIR)
Call Stack (most recent call first):
  /usr/share/cmake-2.8/Modules/FindPackageHandleStandardArgs.cmake:315 (_FPHSA_FAILURE_MESSAGE)
  /usr/share/cmake-2.8/Modules/FindEXPAT.cmake:50 (FIND_PACKAGE_HANDLE_STANDARD_ARGS)
  cmake/Modules/Geant4OptionalComponents.cmake:92 (find_package)
  CMakeLists.txt:99 (include)


-- Configuring incomplete, errors occurred!
See also "/home/mamdouh/g/geant4.10.01.p02-build/CMakeFiles/CMakeOutput.log".


please anyone can help me on this .

thank you so much

---

