---
title: "Gusty update problem"
date: 2007-12-07
forum: General Help
---

### Post by miteshanand1729 on 2007-12-07
I have problem in update.Whenever i launch synaptic or try to update gusty it start and then closed automatically.Also when i want to update from terminal it gives following error...

Reading package lists... Done
mitesh@Mitesh-Desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Segmentation fault (core dumped)
mitesh@Mitesh-Desktop:~$

---

### Post by banewman on 2007-12-07
Try running memtest to see if the memory is ok. :)

---

### Post by taurus on 2007-12-07
Post your /etc/apt/sources.list.

```
cat /etc/apt/sources.list
```

---

### Post by miteshanand1729 on 2007-12-07
> **taurus said:**
> Post your /etc/apt/sources.list.

```
cat /etc/apt/sources.list
```
My sources list is

mitesh@Mitesh-Desktop:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071017)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
deb [ftp://ftp.free.fr/mirrors/ftp.ubuntu.com/ubuntu/](ftp://ftp.free.fr/mirrors/ftp.ubuntu.com/ubuntu/) gutsy main universe restricted multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security universe main restricted multiverse
deb [ftp://ftp.free.fr/mirrors/ftp.ubuntu.com/ubuntu/](ftp://ftp.free.fr/mirrors/ftp.ubuntu.com/ubuntu/) gutsy-updates universe main restricted multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
mitesh@Mitesh-Desktop:~$

---

### Post by miteshanand1729 on 2007-12-07
> **banewman said:**
> Try running memtest to see if the memory is ok. :)
how i test memory...???

I have 1gb RAM and 1gb swap...

---

### Post by taurus on 2007-12-07
Edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and place a # in front of the first line to comment out the cdrom so it won't ask you to insert it.  Then, remove the # in front of all the lines that start with **deb** & **deb-src**.  Save it and run

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by miteshanand1729 on 2007-12-07
My fstab is
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda8 :
UUID=aa99fd68-d93f-4aa6-8a1c-622d4994ff93 / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/sda1 :
UUID=D490E35290E33A1E /media/sda1 ntfs-3g defaults,locale=en_IN 0 1
# Entry for /dev/sda5 :
UUID=40784B26784B1A54 /media/sda5 ntfs-3g defaults,locale=en_IN 0 1
# Entry for /dev/sda6 :
UUID=22C893AEC8937F2B /media/sda6 ntfs-3g defaults,locale=en_IN 0 1
# Entry for /dev/sda7 :
UUID=cfcc37ac-d9a5-49a7-a569-c460cca30430 none swap sw 0 0
/dev/hda /media/cdrom0 udf,iso9660 user,noauto,exec 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec 0 0


this. Now where is deb & deb-src...???
i don't get u?????

---

### Post by taurus on 2007-12-07
> **miteshanand1729 said:**
> My fstab is
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda8 :
UUID=aa99fd68-d93f-4aa6-8a1c-622d4994ff93 / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/sda1 :
UUID=D490E35290E33A1E /media/sda1 ntfs-3g defaults,locale=en_IN 0 1
# Entry for /dev/sda5 :
UUID=40784B26784B1A54 /media/sda5 ntfs-3g defaults,locale=en_IN 0 1
# Entry for /dev/sda6 :
UUID=22C893AEC8937F2B /media/sda6 ntfs-3g defaults,locale=en_IN 0 1
# Entry for /dev/sda7 :
UUID=cfcc37ac-d9a5-49a7-a569-c460cca30430 none swap sw 0 0
/dev/hda /media/cdrom0 udf,iso9660 user,noauto,exec 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec 0 0


this. Now where is deb & deb-src...???
i don't get u?????

I gave you the wrong file to edit.  It should be /etc/apt/sources.list.

---

### Post by miteshanand1729 on 2007-12-07
i got it... i uncheck CDROM from update sources list... now its working... thanx for help...

---

