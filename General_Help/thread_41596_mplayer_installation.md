---
title: "mplayer installation"
date: 2005-06-14
forum: General Help
---

### Post by dakafal on 2005-06-14
I am having a real real problem installing mplayer. Initially I use sudo apt-get install mplayer-386 . But after reading the Ubuntu forums, I tried sudo apt-get install -t hoary mplayer-386. And I get this error: 

sudo apt-get install -t hoary mplayer-386
Password:
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  libggi2 libgii0 libgii0-target-x
Suggested packages:
  libggi-target-emu libggi-target-monotext libggimisc2 w32codecs libdvdcss mplayer-doc
Recommended packages:
  libggi-target-x libggi-target mplayer-fonts
The following NEW packages will be installed:
  libggi2 libgii0 libgii0-target-x mplayer-386
0 upgraded, 4 newly installed, 0 to remove and 2 not upgraded.
Need to get 319kB/3919kB of archives.
After unpacking 8925kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main libgii0 1:0.8.5-2 [126kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main libggi2 1:2.0.5-1ubuntu1 [193kB]
Fetched 319kB in 1s (160kB/s)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libg/libgii/libgii0_0.8.5-2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libg/libgii/libgii0_0.8.5-2_i386.deb)  MD5Sum mismatch
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libg/libggi/libggi2_2.0.5-1ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libg/libggi/libggi2_2.0.5-1ubuntu1_i386.deb)  MD5Sum mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
                                                         Thanks

---

### Post by afonic on 2005-06-14
I'd use Synaptic.

Use search, find mplayer and then install mplayer-386 as well as the fonts.

---

### Post by cutOff on 2005-06-14
I strongly advise to compile it. Take a look to this

[http://ubuntuforums.org/showthread.php?t=31061&highlight=mplayer](http://ubuntuforums.org/showthread.php?t=31061&highlight=mplayer)

---

### Post by afonic on 2005-06-14
[QUOTE=cutOff]I strongly advise to compile it. Take a look to this

[http://ubuntuforums.org/showthread.php?t=31061&highlight=mplayer](http://ubuntuforums.org/showthread.php?t=31061&highlight=mplayer)[/QUOTE]
 Why could this be? There is a pre-compiled package in Synaptic, which installs and runs just fine.

Do you get better results or something?

---

