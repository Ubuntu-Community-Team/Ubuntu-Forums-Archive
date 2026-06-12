---
title: "Need help compiling/installing Qavimator"
date: 2008-02-19
forum: General Help
---

### Post by kopilo on 2008-02-19
Hi there I'm trying to instal qavimator, which is required to be compiled from svn.
( [http://www.qavimator.org/](http://www.qavimator.org/) )

I've managed to download a copy of qavimator over svn/subversion but have been having trouble compiling.

I started out by installing the following for qmake.
```

sudo apt-get install libqt3-headers libqt3-mt libqt3-mt-dev qt3-designer qt3-dev-tools qt3-qtconfig g++

```

then when I ran ./sudo compile it responded with,
```
./compile: line 9: /bin/qmake: No such file or directory
make: *** No targets specified and no makefile found.  Stop.
./compile: line 13: /bin/qmake: No such file or directory
make: *** No targets specified and no makefile found.  Stop.
```

So I tried running qmake from the qmake directory..
```
sudo /usr/bin/qmake ./compile
```
which responded with,
```
compile:8: Parse Error ('cd libquat/')
Error processing project file: /home/kopilo/qavimator/compile
```

*is lost*

---

### Post by kopilo on 2008-02-21
Found a .deb file within the qavimator forums, used the file to install qavimator.

---

### Post by Tsu Dho Nimh on 2008-04-11
Using 64-bit AMD and &,04 Ubuntu

I'm trying to install from the binary (.deb) and get an error about a dependency with libc6 

If I try the 32-bit package, it balks and says I have the wroing CPU ... even though I have all the 32-bit libraries I should need. 


I have installed everything that starts with libc6 that Synaptic lists ... hwat's the trick to this?

---

### Post by Replicon on 2008-04-23
Hi,

I was playing with this just now. I have Gutsy on 64-bit, and was pretty easily able to compile:

```

sudo aptitude install qt3-dev-tools libglut3-dev
export QTDIR=/usr
./compile

```

Worked like a charm. The compile script seems to assume QTDIR is set. I set it to /usr based on the location of qmake returned by "which qmake"

Finally, because those silly people have hard-coded the data path, I had to symlink /usr/share/qavimator/data to where it got installed.

Hope this helps!

---

