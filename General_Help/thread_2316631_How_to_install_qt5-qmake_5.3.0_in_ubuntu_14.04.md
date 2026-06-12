---
title: "How to install qt5-qmake 5.3.0 in ubuntu 14.04"
date: 2016-03-09
forum: General Help
---

### Post by Ashfaqur Rahman on 2016-03-09
I am trying to install [stellarium]("http://stellarium.org/") 0.14.2 from source. All instructions are given [here]("http://stellarium.org/wiki/index.php/Compilation_on_Linux"). When I ran cmake it encounters an error saying qt5-qmake isn't installed. I installed qt5-default for qt5-qmake via apt-get . it installed qt5-qmake version 5.2.1. But now its showing that I need 5.3.0 to successfully compile stellarium.

```

CMake Error at CMakeLists.txt:216 (MESSAGE):
  Found Qt5: /usr/lib/x86_64-linux-gnu/qt5/bin/qmake (found unsuitable
  version "5.2.1", required is "5.3.0")


-- Configuring incomplete, errors occurred!
See also "/home/anonymous/Downloads/stellarium-0.14.2/builds/unix/CMakeFiles/CMakeOutput.log".

```

I have installed qt5-qmake 5.3.0 deb package from here. But it didn't solve my problem. /usr/lib/x86_64-linux-gnu/qt5/bin/qmake still contain the old version of qmake. So how can I upgrade version to 5.3.0?

TIA!

---

### Post by QDR06VV9 on 2016-03-09
Not sure why you are compiling, when you could just add a PPA to get the same version.
[https://launchpad.net/~stellarium/+archive/ubuntu/stellarium-releases](https://launchpad.net/~stellarium/+archive/ubuntu/stellarium-releases)
Kind Regards

---

### Post by Ashfaqur Rahman on 2016-03-09
Oops! I didn't notice. Thanks for the reply!

But still out of curiosity I want to know how can I upgrade qmake. May help future.

---

### Post by howefield on 2016-03-09
Not a Cafe thread, so moved to the "*General Help*" forum.

---

### Post by Ashfaqur Rahman on 2016-03-09
Actually I thought it was a silly question to ask and wasn't appropriate for "General Help". Also I quickly asked the question, didn't give that much effort to make a good post. So I posted it there.

 @[**[COLOR=#990303][B]howefield**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=186490")

---

### Post by howefield on 2016-03-09
No worries, you are asking for support so the thread goes to a support forum. Possibly [Packaging and Compiling Programs]("http://ubuntuforums.org/forumdisplay.php?f=44") would have been a better fit, but we'll leave it here for now. :)

---

### Post by dragonfly41 on 2016-03-09
Recently I found that the Ubuntu Qt5 package in software centre was too early a version for my needs on Ubuntu 14.04.

I installed Qt 5.5.1 using PPA here (although you could use the Qt installer from Qt downloads site).

[https://launchpad.net/~beineri/+archive/ubuntu/opt-qt551-trusty](https://launchpad.net/~beineri/+archive/ubuntu/opt-qt551-trusty)

You might find that you have two versions of Qt 5 so either uninstall the earlier version or use qtchooser to switch between versions.

Running qmake --version

returns ...
QMake version 3.0
Using Qt version 5.5.1 in /opt/qt55/lib

---

### Post by Ashfaqur Rahman on 2016-03-09
I have added the repository but which package should I install for qmake? qt55base?

---

### Post by dragonfly41 on 2016-03-09
In fact I installed the complete Qt 5.5.1 framework

deb [http://ppa.launchpad.net/beineri/opt-qt551-trusty/ubuntu](http://ppa.launchpad.net/beineri/opt-qt551-trusty/ubuntu) trusty main 
deb-src [http://ppa.launchpad.net/beineri/opt-qt551-trusty/ubuntu](http://ppa.launchpad.net/beineri/opt-qt551-trusty/ubuntu) trusty main

---

### Post by Ashfaqur Rahman on 2016-03-10
After adding the repository I have tried to install the whole repository. Shouldn't the qt55-meta package install the whole repository? If I try to install qt55-meta its showing unable to locate!

---

### Post by dragonfly41 on 2016-03-10
I added my suggestion to your thread since you are going through the same steps I followed initially as a Qt beginner.

I found that Ubuntu 14.04 Software Centre version of Qt lags behind the mainstream Qt development.

I now follow the threads in Qt Forum .. 

Here is one example thread .. [https://forum.qt.io/topic/63499/how-and-where-to-start-qt5/13](https://forum.qt.io/topic/63499/how-and-where-to-start-qt5/13)
It is always helpful to follow Qt beginners' threads since you learn from their issues.

Looking through my /opt/qt55 installation notes I first hit on this thread ...

[http://askubuntu.com/questions/279421/how-can-i-install-qt-5-x-on-12-04-lts](http://askubuntu.com/questions/279421/how-can-i-install-qt-5-x-on-12-04-lts)

This should explain the installation process (just adapt for 14.04).


[Later edit]

It occurs to me that you may have missed the link "Read about installing"

**Adding this PPA to your system**

[COLOR=#333333][FONT=Ubuntu]You can update your system with unsupported packages from this untrusted PPA by adding**ppa:beineri/opt-qt551-trusty** to your system's Software Sources. ([Read about installing]("https://launchpad.net/+help-soyuz/ppa-sources-list.html"))  [/FONT][/COLOR]

---

