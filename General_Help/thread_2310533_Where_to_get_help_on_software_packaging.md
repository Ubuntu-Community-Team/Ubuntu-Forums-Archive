---
title: "Where to get help on software packaging?"
date: 2016-01-20
forum: General Help
---

### Post by lads on 2016-01-20
I have been having all sorts of trouble trying to package a Qt programme for Ubuntu. I opened threads [here at the Forums]("http://ubuntuforums.org/showthread.php?t=2309766") and [over at AskUbuntu]("http://askubuntu.com/q/721348/177437"), but no follow ups have came up.

I understand that packaging is something much closer to the Debian community. But that community I do not know very well. Which medium or media would be most appropriate to ask help regarding packaging?

Thank you.

---

### Post by kc1di on 2016-01-20
Have you read the packaging guide found [here?]("http://packaging.ubuntu.com/html/packaging-new-software.html")

---

### Post by dragonfly41 on 2016-01-20
As I understand the OP has already read the packaging guide (there is a link in one of his posts).

I've started researching the same subject on packaging but I have not progressed yet to actually deploying a first package. 
  Others more experienced (Qt5) developers might chip in. 

Since you are using Qt 5 ([COLOR=#333333]/usr/lib/x86_64-linux-gnu/qt5/bin/qmake .. from your pastebin post[/COLOR])  some of my notes might be relevant. 
  My interests are to package for Ubuntu and Android.

But first what version of Qt 5 do you have?

Run ..  

qmake --version
qtchooser -list-versions
qtchooser -print-env

and post the outputs.

...

On Ubuntu 14.04 I've jumped through the many hoops of installing
[LIST]
[*]python 3.4
[*]Qt 5.5.1 (installed from 5.5.1 source into /opt/qt55)
[*]PyQt
[*]eric6 IDE (requires Qt 5.5.1)
[*]pyqtdeploy
[/LIST]

and I've read about differences between pyqtdeploy and pyinstaller for cross platform development.

Although you are not aiming for cross platform perhaps you should look at pyqtdeploy GUI to deploy Qt app to Linux?

Some reading matter ..

[http://www.pyinstaller.org/](http://www.pyinstaller.org/)

[https://plashless.wordpress.com/2014/05/07/comparing-pyinstaller-and-pyqtdeploy/](https://plashless.wordpress.com/2014/05/07/comparing-pyinstaller-and-pyqtdeploy/)

[http://pyqt.sourceforge.net/Docs/pyqtdeploy/tutorial.html](http://pyqt.sourceforge.net/Docs/pyqtdeploy/tutorial.html)

[https://plashless.wordpress.com/2014/09/16/deploying-pyqt-python-qt-apps-cross-platform-using-pyqtdeploy/](https://plashless.wordpress.com/2014/09/16/deploying-pyqt-python-qt-apps-cross-platform-using-pyqtdeploy/)


Note:
I did install Ubuntu SDK IDE but I see that when this launches I get an older version of Qt Creator (Qt Creator 3.5.0 based on Qt 5.4.2).
Because I'm trying eric6 IDE I need a later version and my combination is Qt Creator 3.6.0 based on Qt 5.5.1.
I don't yet know how to update Ubuntu SDK IDE.   I'm sticking with my own built version of Qt 5.5.1/PyQt.

Conclusion after all the above ramble: 
Upgrade to Qt 5.5.1 and try pyqtdeploy GUI.
And seek advice from more experienced packagers (I'm learning).

---

### Post by lads on 2016-01-20
Hi dragonfly41, thanks for replying.

Here is the output you required:

```
$ qmake --version
QMake version 3.0
Using Qt version 5.2.1 in /usr/lib/x86_64-linux-gnu

$ qtchooser -list-versions
4
5
default
qt4-x86_64-linux-gnu
qt4
qt5-x86_64-linux-gnu
qt5

$ qtchooser -print-env
QT_SELECT="default"
QTTOOLDIR="/usr/lib/x86_64-linux-gnu/qt5/bin"
QTLIBDIR="/usr/lib/x86_64-linux-gnu"
```

The particular issue I am bumping into is the wiring between *debuild* and *qmake*, I do not thing the Qt version is the problem. For some reason, *debuild* is invoking *qmake* when there is already a *Makefile* in the folder, and worse, does it without passing the correct arguments.

So back to the initial question: where could I get help regarding the workings of *debuild*, for instance?

Thanks.

---

### Post by dragonfly41 on 2016-01-20
> [COLOR=#000000]So back to the initial question: where could I get help regarding the workings of [/COLOR]*debuild, for instance?*

  I haven't reached that stage in my learning.

But I did find this ...

[http://www.ezwebgallery.org/creating-and-uploading-a-new-debian-ubuntu-package/](http://www.ezwebgallery.org/creating-and-uploading-a-new-debian-ubuntu-package/)


> Remove from your source code any files that are not really useful for compiling the source 
(DO remove the Makefile, DO NOT remove the .pro file! You MUST remove any possible .o files, 
the executable, and the .pro.user file).

debuild -S -sa


Also I learn more from

man debuild

and 

[https://wiki.debian.org/IntroDebianPackaging](https://wiki.debian.org/IntroDebianPackaging)

---

### Post by lads on 2016-01-21
> **dragonfly41 said:**
> 
But I did find this ...

[http://www.ezwebgallery.org/creating-and-uploading-a-new-debian-ubuntu-package/](http://www.ezwebgallery.org/creating-and-uploading-a-new-debian-ubuntu-package/)


Thank you dragonfly41, that guide led me in the right way. Basically, you cannot use the *rules* file in the same way for a Qt programme. I left the details at [AskUbuntu]("http://askubuntu.com/a/723707/177437").

Cheers.

---

### Post by dragonfly41 on 2016-01-21
Well that is one deep pothole I can now avoid when I reach that stage in the road of packaging a Qt 5.5.1 app.

Perhaps now mark this thread as [Solved] .. see Thread Tools above.

---

### Post by lads on 2016-02-09
Dear all,

I would like to get back to the initial question: which community or medium would be most appropriate to get help regarding packaging? 

For five weeks now, I have been trying to make a Qt programme available from my PPA, but I just keep going from problem to problem (right now [the Launchpad 32-bit build environment is invoking 64-bit programmes]("http://ubuntuforums.org/showthread.php?t=2312938")). There are many guides out there, but all tailored to a strict case, that seems very far from a typical Qt application (and perhaps other kinds of applications). I probably need to get in contact with folk that regularly package programmes for Debian/Ubuntu. But where?

Thank you once again.

---

### Post by howefield on 2016-02-09
> **lads said:**
> I would like to get back to the initial question: which community or medium would be most appropriate to get help regarding packaging? 

I'd suggest the [mailing list]("https://lists.ubuntu.com/mailman/listinfo/ubuntu-devel") or IRC : #ubuntu-packaging on Freenode

---

### Post by lads on 2016-02-10
> **howefield said:**
> I'd suggest the [mailing list]("https://lists.ubuntu.com/mailman/listinfo/ubuntu-devel")

Thank you howefield. I have been getting valuable feedback from the list, even if the package still fails to compile.

Cheers.

---

### Post by dragonfly41 on 2016-02-10
I've installed debreate to try at some point with a Qt 5.5 app ..

[http://debreate.sourceforge.net](http://debreate.sourceforge.net)

---

### Post by ian-weisser on 2016-02-10
Lots of QT-related packaging goes on at Debian.
Good people to ask, and usually quite friendly.
Have you looked at [http://pkg-kde.alioth.debian.org/qtkde.html](http://pkg-kde.alioth.debian.org/qtkde.html) ?

---

### Post by mc4man on 2016-02-10
maybe you should take a look at how it's packaged & the rules/control/install files for the repo pgmodeler
[https://launchpad.net/ubuntu/+source/pgmodeler](https://launchpad.net/ubuntu/+source/pgmodeler)

---

### Post by lads on 2016-02-16
> **mc4man said:**
> maybe you should take a look at how it's packaged & the rules/control/install files for the repo pgmodeler
[https://launchpad.net/ubuntu/+source/pgmodeler](https://launchpad.net/ubuntu/+source/pgmodeler)

Thanks for bringing this up. I wish I had known about this PPA before I started.

---

