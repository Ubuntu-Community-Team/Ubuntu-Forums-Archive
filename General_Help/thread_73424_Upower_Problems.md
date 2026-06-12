---
title: "Upower Problems"
date: 2005-10-09
forum: General Help
---

### Post by nihilism on 2005-10-09
Hey, I'm trying to install upower, and I'm getting alot of annoying problems:
```
zax@ubuntu:~/upow$ sudo dpkg -i *.deb
(Reading database ... 81152 files and directories currently installed.)
Preparing to replace lib++dfb-0.9-22 0.9.22-1 (using lib++dfb-0.9-22_0.9.22-1_i386.deb) ...
Unpacking replacement lib++dfb-0.9-22 ...
Preparing to replace libdirectfb-0.9-22 0.9.22-1 (using libdirectfb-0.9-22_0.9.22-1_i386.deb) ...
Unpacking replacement libdirectfb-0.9-22 ...
Selecting previously deselected package upower.
Unpacking upower (from upower_0.1-1_i386.deb) ...
Setting up libdirectfb-0.9-22 (0.9.22-1) ...

dpkg: dependency problems prevent configuration of upower:
 upower depends on libgcc1 (>= 1:4.0.0-7); however:
  Version of libgcc1 on system is 1:4.0-0pre6ubuntu7.
dpkg: error processing upower (--install):
 dependency problems - leaving unconfigured
Setting up lib++dfb-0.9-22 (0.9.22-1) ...

Errors were encountered while processing:
 upower

```
And then when I apt-get libgcc1 i get:
```
zax@ubuntu:~/upow$ sudo apt-get install libgcc1
Reading package lists... Done
Building dependency tree... Done
libgcc1 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```
Please, all help would be appreciated, I'm using this [guide]("https://wiki.ubuntu.com/UPower") but no dice, any help?

---

### Post by Syphin on 2005-10-09
I'm having the exact problem trying to install this also.
Would love for some info on how to get it working, too. I've tried everything i could think of, nothin worked. :(

---

### Post by Goshawk on 2005-10-16
upower needs to be recompiled to work on breezy (the 0.1 version) while the 0.2 will suppot breezy natively (so no problems with usplash).
You must wait, since i'm not able to compile it (my pc is broken), when it will be fixed upower 0.2 for breezy + theme package will be available.

---

### Post by limit223 on 2005-12-27
Could anyone managed to install upower in breezy, now?
 I did everything from here: [http://nanofreesoft.org/index.php?module=subjects&func=viewpage&pageid=1](http://nanofreesoft.org/index.php?module=subjects&func=viewpage&pageid=1)

and I can't install it because of 
upower:
Depends: libppdfb-0.9-22  but it is not installable

There is anywhere else I can find this package?

---

