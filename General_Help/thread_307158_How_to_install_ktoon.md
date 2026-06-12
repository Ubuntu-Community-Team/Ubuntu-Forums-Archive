---
title: "How to install ktoon???"
date: 2006-11-26
forum: General Help
---

### Post by johann_p on 2006-11-26
I have used ktoon on my previous distro and I would love to use it with Ubuntu Edgy too. Unfortunately, there is no package available with synaptic, so I have to compile it.

Now, when I do the ./configure step I get the following error message:
 *  You're using Qt 3
 *  Please install Qt >= 4.1 or set QTDIR to Qt4 installation path

However, synaptic tells me I have libqt4* packages installed (in addition to libqt3). I have no idea how this parallel use of qt3 and qt4 works. 

I tried to do the following:
export QTDIR=/usr/share/qt4
export PATH $QTDIR/bin:$PATH

after wich the configure step succeded.

However, the make step aborts with the following error:
/usr/include/qt4/QtCore/qhash.h: In member function ‘bool DActionManager::insert(DAction*)’:
/usr/include/qt4/QtCore/qhash.h:326: error: ‘QHash<K, V>::iterator::operator bool() const [with Key = QString, T = DAction*]’ is private
dactionmanager.cpp:43: error: within this context
make[3]: *** [.obj/dactionmanager.o] Error 1
make[3]: Leaving directory `/disk1/Install/ktoon-0.8/src/dlib/dgui'
make[2]: *** [sub-dgui-make_default] Error 2
make[2]: Leaving directory `/disk1/Install/ktoon-0.8/src/dlib'
make[1]: *** [sub-dlib-make_default] Error 2
make[1]: Leaving directory `/disk1/Install/ktoon-0.8/src'
make: *** [sub-src-make_default] Error 2


Frustration!!!

Is there a way to get this to run under Edgy?

---

### Post by xtingray on 2006-11-26
Hello, My name is Gustavo Gonzalez and i am the development director of the KToon project.
Our application is still beta, so the best way you could try KToon is compiling it.
KToon 0.8.0 requires Qt 4.1.4 and ffmpeg compiled in "shared" mode.

More info:
[http://ktoon.toonka.com/documentation/index.php?title=Compiling_KToon_using_QT4](http://ktoon.toonka.com/documentation/index.php?title=Compiling_KToon_using_QT4)
[http://ktoon.toonka.com/documentation/index.php?title=Installing_FFMPEG_for_KToon](http://ktoon.toonka.com/documentation/index.php?title=Installing_FFMPEG_for_KToon)

If you have doubts about it, please email us to: ktoon at toonka dot com

---

### Post by johann_p on 2006-11-27
> **xtingray said:**
> 
KToon 0.8.0 requires Qt 4.1.4



Hmm, it seems I do not have much of a choice when installing Qt via packages -- if I install qt4 in Edgy it automatically is version 4.2.0. 

So, what will happen if I install Qt4.1.1 *in addition* via configure/make/install? This will probably use different directories than the package install or might overwrite things so I am  bit scared trying it out. (Assuming that the compile will work).

In any case, I am a bit surprised that a different *minor* version of Qt does make that much of a difference.

---

### Post by b4k4 on 2006-11-28
I found a debian package, but Gdebi says libc6 is unsatisfied. I am using dapper, which says it has libc6 2.3.6-0ubuntu20, whereas the deb requires 2.3.6-6. Frustrating.

[http://packages.debian.org/unstable/graphics/ktoon]("http://packages.debian.org/unstable/graphics/ktoon")

---

### Post by ajeetraj on 2007-07-23
I just installed Ktoon and it is crashing just after I open it. I see a box which splashes and then it disappears....I tried to run it through the terminal and I get this messge:

> 
deepu@easter-sunday:~$ ktoon
[Initializing DApplication]
[Initializing DConfig]
[Initializing DConfigDocument]
*********Init configuration file : "/home/deepu/.ktoon/ktoon.cfg"
ktoon is crashing with signal 11 :(
ASSERT failure in QCoreApplication: "there should be only one application object", file kernel/qcoreapplication.cpp, line 402
Aborted (core dumped)


Can someone help me out with it? thank you so much!

---

### Post by higashi on 2007-08-28
> **ajeetraj said:**
> I just installed Ktoon and it is crashing just after I open it. I see a box which splashes and then it disappears....I tried to run it through the terminal and I get this messge:



Can someone help me out with it? thank you so much!
I had the same problem with stopmotion. Try re-installing it.

---

### Post by Somtin on 2007-08-31
Hi, I am using Ubuntu Feisty, and I downloaded the debian package from the unstable repo. I am getting the same error as ajeetraj. Tried reinstalling, did not fix the problem. Any hints?

Somtin

---

### Post by higashi on 2007-09-01
here, try typing this in your terminal:

```
wget http://download.berlios.de/ktoon/ktoon0.8-ubuntu6.06.tar.gz
tar xzf ktoon0.8-ubuntu6.06.tar.gz
cd ktoon
./ktoon
```

---

