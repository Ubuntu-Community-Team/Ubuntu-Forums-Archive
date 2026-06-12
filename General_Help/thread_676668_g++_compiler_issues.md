---
title: "g++ compiler issues"
date: 2008-01-24
forum: General Help
---

### Post by zlittlefield on 2008-01-24
When i try to install the g++ compiler, i get this message:


zlittlefield@Zak-Laptop:~$ sudo apt-get install g++
[sudo] password for zlittlefield:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  g++-4.1 libc6-dev libstdc++6-4.1-dev linux-libc-dev
Suggested packages:
  g++-multilib g++-4.1-multilib gcc-4.1-doc glibc-doc manpages-dev
  libstdc++6-4.1-doc
The following NEW packages will be installed:
  g++ g++-4.1 libc6-dev libstdc++6-4.1-dev linux-libc-dev
0 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/7670kB of archives.
After unpacking 31.0MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Media change: please insert the disc labeled
 'Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)'
in the drive '/cdrom/' and press enter


after that, i can't do anything because i used a live disc to install ubuntu.  What can i do about this?

---

### Post by Tenken on 2008-01-24
You can still use the live cd, or remove the CD from you sources list go to System->Administration->Software Sources and under the Ubuntu Software tab uncheck the Installable from CD ROM/DVD box.

---

### Post by LaRoza on 2008-01-24
Use the command:

```

sudo aptitude install build-essential

```

It will get everything else you need to use it.

---

