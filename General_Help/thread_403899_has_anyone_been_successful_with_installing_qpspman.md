---
title: "has anyone been successful with installing qpspmanager-1.3.tar.gz??"
date: 2007-04-07
forum: General Help
---

### Post by Fittersman on 2007-04-07
i downloaded qpspmanager-1.3.tar.gz but i dont know what im doing to install it..

the homepage of the program is:
[http://qpspmanager.sourceforge.net/](http://qpspmanager.sourceforge.net/)

just click downloads on the side and then download it from there...


but anyway, has anyone installed it before? i cant seem to do it

here is the readme that came with it:

```

QPPSPManager
The Linux PSP File Manager
(C) 2006 Bernat Ràfales Mulet (see COPYING for license details)

Installation instructions
=========================

First, be sure you have the QT3 Development files, then just type

qmake

to build the Makefile, then

make

to build the project, and finally

make install

to install the program (you should execute make install with root permission).

Then you will have the binary "qpspmanager" for your enjoyment.

I strongly recommend changing the default "style" for QT, which is KeramiK, to
another one more better looking such as PlastiK.

```

i got past qmake but when i tried to use make, it gave me this...

```
cleippi@cleippi-desktop:~/Desktop/qpspmanager-1.3$ make
cd src && make -f Makefile
make[1]: Entering directory `/home/cleippi/Desktop/qpspmanager-1.3/src'
make[1]: *** No rule to make target `/usr/share/qt3/lib/libqt-mt.prl', needed by `Makefile'.  Stop.
make[1]: Leaving directory `/home/cleippi/Desktop/qpspmanager-1.3/src'
make: *** [sub-src] Error 2

```

and i tried sudo make also and that didnt work, gave me the same output...

---

### Post by Fittersman on 2007-04-09
sooooo, anyone got any help on this subject?

---

### Post by aysiu on 2007-04-09
Have you tried this? ```
wget -c http://superb-east.dl.sourceforge.net/sourceforge/qpspmanager/qpspmanager_1.1.2-1_i386.deb
sudo dpkg -i qpspmanager_1.1.2-1_i386.deb
```

---

### Post by Fittersman on 2007-04-09
ok, i tried that and this is what happend:

```
cleippi@cleippi-desktop:~$ wget -c http://superb-east.dl.sourceforge.net/sourceforge/qpspmanager/qpspmanager_1.1.2-1_i386.deb
--01:18:03--  http://superb-east.dl.sourceforge.net/sourceforge/qpspmanager/qpspmanager_1.1.2-1_i386.deb
           => `qpspmanager_1.1.2-1_i386.deb'
Resolving superb-east.dl.sourceforge.net... 209.160.66.130
Connecting to superb-east.dl.sourceforge.net|209.160.66.130|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 64,598 (63K) [application/octet-stream]

100%[====================================>] 64,598       109.93K/s             

01:18:04 (109.84 KB/s) - `qpspmanager_1.1.2-1_i386.deb' saved [64598/64598]

cleippi@cleippi-desktop:~$ sudo dpkg -i qpspmanager_1.1.2-1_i386.deb
Password:
Selecting previously deselected package qpspmanager.
(Reading database ... 121942 files and directories currently installed.)
Unpacking qpspmanager (from qpspmanager_1.1.2-1_i386.deb) ...
dpkg: dependency problems prevent configuration of qpspmanager:
 qpspmanager depends on libqt3c102-mt (>= 3:3.3.4); however:
  Package libqt3c102-mt is not installed.
dpkg: error processing qpspmanager (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 qpspmanager
cleippi@cleippi-desktop:~$ 

```

it says "Package libqt3c102-mt is not installed." so i went to symnatec and did a search for libqt3c102-mt but it returned no results...

---

### Post by aysiu on 2007-04-09
How about trying to install *libqt3-mt* through Synaptic and seeing if that resolves the issue?

If that doesn't work, try installing *libqt3c102-mt* from [here](http://packages.debian.org/stable/libs/libqt3c102-mt).

---

### Post by Fittersman on 2007-04-10
i got it to work, i dont like it, how do i uninstall now?

---

### Post by aysiu on 2007-04-10
> **Fittersman said:**
> i got it to work, i dont like it, how do i uninstall now?
```
sudo apt-get remove qpspmanager
``` By the way, was it *libqt3-mt* that worked, or *libqt3c102-mt*?

---

### Post by Fittersman on 2007-04-10
thanks, and it was libqt3c102-mt, but i had to uninstall all my KDE apps to install that, so thats what im doing now (reinstalling all the kde apps :()

---

### Post by HasratUSA on 2007-04-12
> **Fittersman said:**
> i got it to work, i dont like it, how do i uninstall now?

The moment I saw its website, I hated it. I don't even know why I would need it LOL. Good to know I didn't install it. Cheers and death to crapware :)

---

