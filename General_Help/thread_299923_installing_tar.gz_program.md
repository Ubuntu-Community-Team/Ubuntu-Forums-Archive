---
title: "installing tar.gz program"
date: 2006-11-14
forum: General Help
---

### Post by evilc on 2006-11-14
I have been trying to install emelfm2-0.3.tar.gz which is a file manager, have extracted to temp folder (a1) and then ran checkinstall it's output:

_____________________________________
This package will be built according to these values: 

0 -  Maintainer: [ root@clive ]
1 -  Summary: [ emelfm2-0.3 ]
2 -  Name:    [ emelfm2 ]
3 -  Version: [ 0.3 ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ i386 ]
8 -  Source location: [ emelfm2-0.3 ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]

Enter a number to change any of them or press ENTER to continue: 

Installing with make install...

========================= Installation results ===========================
creating object directories in 'objs'
generating marshals
/bin/sh: glib-genmarshal: not found

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.
_______________________________________________

I checked synaptic but that only had version .9 (very basic) and would prefer the latest version.
I have no idea what I am doing wrong can someone help.

TIA

---

### Post by pay on 2006-11-15
Try ```
sudo aptitude install build-essential
wget http://asic-linux.com.mx/~izto/checkinstall/files/source/checkinstall-1.6.1.tgz
tar zxvf checkinstall-1.6.1.tgz
cd checkinstall*
./configure
make
sudo make install
sudo checkinstall
cd a1
./configure
make
sudo checkinstall
```

---

### Post by karamba_kid on 2006-11-15
Not to insult checkinstall or anything, but I think it's a messy hack because dependencies and apt can get confused, or at least that's what I always suspected.  Instead when I need to install something from source I usually just compile and install the standard *nix way with make.  I would suggest installing it to /usr/local you'll need to specify that when you compile.  Good luck with finding a solution that works for you.

---

### Post by evilc on 2006-11-15
> **pay said:**
> Try ```
sudo aptitude install build-essential
wget http://asic-linux.com.mx/~izto/checkinstall/files/source/checkinstall-1.6.1.tgz
tar zxvf checkinstall-1.6.1.tgz
cd checkinstall*
./configure
make
sudo make install
sudo checkinstall
cd a1
./configure
make
sudo checkinstall
```

When I run the first line I get:

_____________________
Couldn't find any package whose name or description matched "built-essential"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

 I run it from both home & temp folder?
Must admit I am hopeless when it comes to tar files.

edit: Just checked checkinstall it's ver. 1.6.2

---

### Post by pay on 2006-11-15
It's not built-essential, It's build-essential.

---

### Post by evilc on 2006-11-15
> **pay said:**
> It's not built-essential, It's build-essential.

Sorry,
Got as far as clive@clive:~/checkinstall-1.6.1$ cd a1 see below then it all spat the dummy on me.](*,) 

========================================================

An existing checkinstallrc file has been found.
The one from this distribution can be found at:

-e      /usr/local/lib/checkinstall/checkinstallrc-dist


========================================================


======================== Installation successful ==========================

Copying documentation directory...
./
./FAQ
./BUGS
./TODO
./README
./installwatch-0.7.0beta5/
./installwatch-0.7.0beta5/BUGS
./installwatch-0.7.0beta5/TODO
./installwatch-0.7.0beta5/README
./installwatch-0.7.0beta5/CHANGELOG
./installwatch-0.7.0beta5/VERSION
./installwatch-0.7.0beta5/INSTALL
./installwatch-0.7.0beta5/COPYING
./NLS_SUPPORT
./RELNOTES
./INSTALL
./Changelog
./COPYING
./CREDITS

Copying files to the temporary directory...OK

Striping ELF binaries and libraries...OK

Compressing man pages...OK

Building file list...OK

Building Debian package...OK

NOTE: The package will not be installed

Erasing temporary files...OK

Writing backup package...OK

Deleting temp dir...OK


**********************************************************************

 Done. The new package has been saved to

 /home/clive/checkinstall-1.6.1/checkinstall_1.6.1-1_i386.deb
 You can install it in your system anytime using: 

      dpkg -i checkinstall_1.6.1-1_i386.deb

**********************************************************************

clive@clive:~/checkinstall-1.6.1$ cd a1
bash: cd: a1: No such file or directory
clive@clive:~/checkinstall-1.6.1$

---

### Post by pay on 2006-11-15
Sorry I didn't realise that you already had checkinstall installed already. You can continue using the old one or use the new one with```
sudo dpkg -i checkinstall_1.6.1-1_i386.deb
```and then change to the a1 directory and continue```
cd a1
./configure
make
sudo checkinstall
```

---

### Post by evilc on 2006-11-16
Still don't work here's what happened:

clive@clive:~$ cd a1
clive@clive:~/a1$ ./configure
bash: ./configure: No such file or directory
clive@clive:~/a1$ make
creating object directories in 'objs'
make: *** No rule to make target `src/build/e2_marshal.list', needed by `src/build/e2_marshal.h'.  Stop.
clive@clive:~/a1$ 

Also I ran sudo dpkg -i checkinstall_1.6.1-1_i386.deb would that overwrite the other checkinstall that was there?

---

### Post by pay on 2006-11-16
Yes that would overright the old installation of checkinstall. cd into the right directory where the source is and try ./configure. If that doesn't work try autoconf and then ./configure. Also read the readme to see if it has any tips for compilling from source. the general steps though are to 
```
tar zxvf file.tar.gz # or tar jxvf file.tar.bz2
cd file
./configure
make
make install
```

---

### Post by towsonu2003 on 2006-11-16
```
sudo apt-get install emelfm
``` unless you need the newer version for a reason -I didn't see any message specifying that-

it seems to be in the universe repository, so you'll need to enable it. [https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/extra-repositories.html](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/extra-repositories.html)

---

### Post by evilc on 2006-11-16
pay,
 I thought there may have been an error in download so I re-downloaded it again this time to the desktop. Did what you have said, the first part made a folder on desktop. I then change to that folder and run *make* this  totally failed all errors?
I am starting to dislike tar files more and more :) there don't seem to be any standards with them.

towsonu2003,
I wanted this (latest) version as it has much better design and layout  than  the one in synaptic.

---

### Post by pay on 2006-11-16
Did you run ./configure before make?

---

### Post by evilc on 2006-11-16
Yup here's what I got.
clive@clive:~/Desktop/emelfm2-0.3$ ./configure
bash: ./configure: No such file or directory
clive@clive:~/Desktop/emelfm2-0.3$ 

Just a query why have'nt synaptic updated this file there have been about 6 or so updates. ( might make another threed regarding this).

---

### Post by Jongi on 2006-11-16
put sudo in front of each command eg **sudo ./configure**

---

### Post by evilc on 2006-11-16
Jongi,
Tried that no luck.

Pay,

Thanks for all your help I have been searching around about emelfm2 to see if there was any problems with it and low & behold I found ver.2-0.1 in deb format d/l and it dropped in no problems.:D

Have noticed around the forums there seems to be a lot of problem with tar files and installing, I would have thought some genius would make an easy installing prog for it. Anyway thanks again.

---

### Post by pay on 2006-11-16
Well tar.gz files nromally contain source code so they will never be easy to manually install. A genius did make a file system called portage though that is used in Gentoo that automatically downloads source code (and occasioanlly binaries) and compiles it for you, but I wouldn't recommend that distro for someone that is new to Linux.

---

### Post by pay on 2006-11-16
I decided to download it myself and compille it and it worked for me (I'm on Gentoo), with ```
tar zxvf emelfm2-0.3.tar.gz
make
su
make install #su won't work on Ubuntu so use sudo make install
```and then to make it run I had to run ```
emelfm2 --ignore-problems
```Abit nasty but it worked. Maybe someone will shed some light on why it won't compile in Ubuntu (Assumming you have GCC installed with sudo aptitude install build-essential)

---

### Post by adamkane on 2006-11-16
You checked synaptic, but you didn't check the emelfm2 website for a recent ubuntu deb file:
[http://emelfm2.net/DownLoads](http://emelfm2.net/DownLoads)
[http://lottalinuxlinks.com/files/emelfm2_0.2.0-1_i386.deb](http://lottalinuxlinks.com/files/emelfm2_0.2.0-1_i386.deb)

Always check the website and then google for an ubuntu deb.

---

### Post by qpieus on 2006-11-16
You beat me to it adamkane, I was just about to post the lottalinuxlinks link. I just started listening to the lottalinuxlinks podcast and he had a show on this file manager.

---

### Post by pay on 2006-11-16
He didn't want version 0.2, He wanted version 0.3.

---

### Post by evilc on 2006-11-16
Thanks *pay so it's not *yours & mine attempt to install it just a compiling problem. Glad to hear I'm not going around the twist.:D

Adamkane,

Thanks that the one I ended up with.

---

### Post by gribelu on 2006-12-20
fought it for a while and it finaly installed

first download the latest emelfm2 tar.gz .. i used emelfm2-0.3.1.tar.gz

```

apt-get install build-essential libgtk2.0-dev libglib2.0-dev
tar xvfz emelfm2-0.3.1.tar.gz
cd emelfm2-0.3.1
make
make install

```

then just run it by typing emelfm2 .. or create shortcuts

now, i have a problem... weird one... whenever i get a confirmation dialog (copy delete whatever) emelfm2 freezes under gnome (ubuntu 6.10) ... but under kde, where my gtk apps use no theme (ugly :) ) it works fine. Weird hm?
I tried changing the desktop theme but no luck. Any ideas?

Edit: seems to work fine under kde with the gtk-qt theme... so it's no longer ugly... but i still don't get why it won't work on Gnome. Please try this too thanks

---

