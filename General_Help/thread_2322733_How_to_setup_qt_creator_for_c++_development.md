---
title: "How to setup qt creator for c++ development ?"
date: 2016-04-30
forum: General Help
---

### Post by startas on 2016-04-30
How to setup qt creator for c++ development ? Basically what i want to do is some general c++ opengl programming, and i want to useqt creator as an ide. I'm using ubuntu 16.04, i dont need all that qt bloatware and thousands of useless libraries, all i need is c++ ide, so i have downloaded and installed qt-creator-opensource-linux-x86_64-3.6.1 from qt website. I have chosen to create a simple c++ non qt application,, after that i chose to use cmake as my build system, and then it created cmake file and first main.cpp file. My problem is that i cant add new files to my project - i can only build, lean and run my project, all the add files, add existing files and other options are grayed out. Am i missing some configuration or what ?

---

### Post by T.J. on 2016-05-02
> **startas said:**
> How to setup qt creator for c++ development ? Basically what i want to do is some general c++ opengl programming, and i want to useqt creator as an ide. I'm using ubuntu 16.04, i dont need all that qt bloatware and thousands of useless libraries, all i need is c++ ide, so i have downloaded and installed qt-creator-opensource-linux-x86_64-3.6.1 from qt website. I have chosen to create a simple c++ non qt application,, after that i chose to use cmake as my build system, and then it created cmake file and first main.cpp file. My problem is that i cant add new files to my project - i can only build, lean and run my project, all the add files, add existing files and other options are grayed out. Am i missing some configuration or what ?



QtCreator is an "incomplete" editor, except for Qt projects, naturally,  If you want to use QtCreator, try switching to qmake instead of cmake.

[https://forum.qt.io/topic/28190/qt-creator-2-7-non-qt-project-can-t-add-files/2](https://forum.qt.io/topic/28190/qt-creator-2-7-non-qt-project-can-t-add-files/2)

I recommend CodeBlocks or Eclipse  over QtCreator.


As a general rule, you should use the versions from the repository rather than downloading the website version. The version in the repository will get maintenance patches. The website version won't unless you do it yourself, and doesn't always have a security signature.

---

