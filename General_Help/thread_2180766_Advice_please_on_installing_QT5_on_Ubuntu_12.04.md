---
title: "Advice please on installing QT5 on Ubuntu 12.04"
date: 2013-10-14
forum: General Help
---

### Post by dragonfly41 on 2013-10-14
Is there fast track for installing QT5 on Ubuntu 12.04?

I did find this ...  [http://qt-project.org/wiki/Building-Qt-5-from-Git](http://qt-project.org/wiki/Building-Qt-5-from-Git)

but I would like to use a simpler PPA command if possible.

I already have QT 4.8.1 installed.

I need QT5 for building cmake-2.8.10.2-Linux-i386

cmake-2.8.10.2 in turn is needed to build some packages.

This is the error message I see when trying to build a package.

[COLOR=red]CMake Error at CMakeLists.txt:415 (FIND_PACKAGE):
  By not providing "FindQt5Core.cmake" in CMAKE_MODULE_PATH this project has
  asked CMake to find a package configuration file provided by "Qt5Core", but
  CMake did not find one.[/COLOR]

So .. back to installing QT5.

===========================================

[Later Edit]

 [FONT=FreeSans]I found this article ..[/FONT]
  [[FONT=FreeSans]http://www.ubuntuask.com/q/answers-how-can-i-install-qt-5-x-on-12-04-lts-279421.html[/FONT]]("http://www.ubuntuask.com/q/answers-how-can-i-install-qt-5-x-on-12-04-lts-279421.html")

  sudo apt-add-repository ppa:ubuntu-sdk-team/ppa
sudo apt-get update 
sudo apt-get install qtdeclarative5-dev
 [FONT=FreeSans]
[/FONT][FONT=FreeSans]And then download [/FONT]
[URL="http://download.qt-project.org/official_releases/qt/5.1/5.1.1/qt-linux-opensource-5.1.1-x86-offline.run"][COLOR=#0057ae][U]
Qt 5.1.1 for Linux 32-bit (417 MB)[/U][/COLOR][/URL] 

Make the downloaded file (with *.run extension) executable

Then run as executable installer.
 
Qt 5.1.1 installed in /opt/Qt5.1.1

 ...

I have to yet to complete the build of cmake-2.8.10.2 but since I've now got Qt Creator 5.1.1 installed I should be nearly home and dry.

---

