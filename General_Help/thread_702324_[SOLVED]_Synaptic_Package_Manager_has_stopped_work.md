---
title: "[SOLVED] Synaptic Package Manager has stopped working."
date: 2008-02-20
forum: General Help
---

### Post by lambono on 2008-02-20
Synaptic Package Manager has stopped working.
When I try to install a new program it seems to download the files but not Install them. 
The terminal shows the following error

dpkg: syntax error in triggers Deferred file '/var/lib/dpkg/triggers/Unincopr' at character 'U' midline
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install. Trying to recover:

I tried to reinstall dpkg but got the following error:
E: Couldn't configure pre-depend dpkg for imlib-base, probably a dependency cycle.

Any ideas??

Thanks for your help!!!

---

### Post by y-lee on 2008-02-20
Try:

```
sudo dpkg-reconfigure -a
```

If that doesn't work post any errors here.

---

### Post by lambono on 2008-02-20
I tried 
sudo dpkg-reconfigure -a 
and 
sudo apt-get install aa3d...


```
conor@conor-linux:~$ sudo dpkg-reconfigure -a
dpkg-query: syntax error in triggers Deferred file `/var/lib/dpkg/triggers/Unincorp' at character `U' midline
/usr/sbin/dpkg-reconfigure: aa3d is not installed
conor@conor-linux:~$ 
conor@conor-linux:~$ 
conor@conor-linux:~$ sudo apt-get install aa3d
Reading package lists... Done
Building dependency tree       
Reading state information... Done
aa3d is already the newest version.
The following packages were automatically installed and are no longer required:
  liblzo1 libglitz-glx1 kdebase-kio-plugins python-qt3 libkonq4 python-sip4
  kdebase-bin libglitz1 kdesktop
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 23 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
dpkg: syntax error in triggers Deferred file `/var/lib/dpkg/triggers/Unincorp' at character `U' midline
E: Sub-process /usr/bin/dpkg returned an error code (2)
conor@conor-linux:~$ 

```

---

### Post by lambono on 2008-02-20
Dont know if this is of any help...

```

conor@conor-linux:/var/lib/dpkg/triggers$ pwd
/var/lib/dpkg/triggers
conor@conor-linux:/var/lib/dpkg/triggers$ cat Unincorp
Package: libc6
Status: install ok triggers-pending
Priority: required
Section: libs
Installed-Size: 10120
Maintainer: Ubuntu Core developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Source: glibc
Version: 2.6.1-1ubuntu10
Provides: glibc-2.6-1
Depends: libgcc1
Suggests: locales, glibc-doc
Conflicts: libterm-readline-gnu-perl (<< 1.15-2), tzdata (<< 2007e-2)
Conffiles:
 /etc/init.d/glibc.sh 2b765577647ae33c2fdcc7bba95e4c7f
 /etc/ld.so.conf.d/i486-linux-gnu 36f09aeeab18f6af453d0a1db0a0942c
 /etc/ld.so.conf.d/libc.conf d4d833fd095fb7b90e1bb4a547f16de6
 /etc/gai.conf 25b7f2e990aa62df7b7d233acd644813
 /etc/bindresvport.blacklist db84c47f31f8d5a334a4053d8368e902
Description: GNU C Library: Shared libraries
 Contains the standard libraries that are used by nearly all programs on
 the system. This package includes shared versions of the standard C library
 and the standard math library, as well as many others.
Triggers-Pending: ldconfig
Original-Maintainer: GNU Libc Maintainers <debian-glibc@lists.debian.org>
conor@conor-linux:/var/lib/dpkg/triggers$ 

```

---

### Post by lespaul_rentals on 2008-02-20
Try running:

```
sudo apt-get update
```

---

### Post by y-lee on 2008-02-20
Ok I thought that might happen. it seems you have the same problem as is found here, [SOLVED] Update Manager and apt-get not working]("http://ubuntuforums.org/showthread.php?t=681675").

read that post very carefully and follow the advice there. 

If you have any problems post here. Let us know how it works out.

EDIT: Read all 3 pages first before you do anything.

---

### Post by lambono on 2008-02-20
Thanks for the post
Just tried that. 
Sill getting the same errors however.

---

### Post by y-lee on 2008-02-20
Ok your situation is a bit different, I think the problem is the conflict 

```
Conflicts: libterm-readline-gnu-perl (<< 1.15-2), tzdata (<< 2007e-2)
```

but honestly this is a bit out of my league. :(  I hate to advise you to do something dangerous but I would try:

> **PmDematagoda said:**
> Ok, now this involves a bit of risk as it means editing the Unincorp file so do this only if you are willing to take a risk.

First open Nautilus in root mode using:-
```
gksudo nautilus
```

Then navigate to /var/lib/dpkg/triggers and make a backup of the Unincorp file or copy it somewhere else.

After you have made a backup of the Unincorp file open the current Unincorp file for editing using:-
```
gksudo gedit /var/lib/dpkg/triggers/Unincorp
```

Then remove everything that is there to make it blank and save the file.

Then try doing:-
```
sudo apt-get remove libterm-readline-gnu-perl   tzdata
```

Now try

```
sudo dpkg-reconfigure -a 
```

But I honestly am not sure. This is a guess flat out... You might want to wait till somebody comes along that knows more than me.

---

### Post by lambono on 2008-02-20
Hi y-lee,
I was replying to lespaul_rentals post.
I haven't worked my way through your recommended thread just yet. 
I am heading away for a long weekend so prob wont get a chance to look at this again until next week. I will let you know how I get on and thanks again for your help!

Conor

---

### Post by lambono on 2008-02-25
> Ok I thought that might happen. it seems you have the same problem as is found here, SOLVED] Update Manager and apt-get not working.

read that post very carefully and follow the advice there. That worked!! :) 

Thanks very much y-lee and for everyone else who responded!

Lambono

---

