---
title: "LVM - pvcreate missing?"
date: 2006-12-02
forum: General Help
---

### Post by navilon on 2006-12-02
I just installed Ubuntu 6.10 Server on an extra machine
I needed LVM on that computer so I installed it with the following command..
```
sudo apt-get install lvm2
```
which resulted in this..
```
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  lvm-common mdadm
Suggested packages:
  dmsetup
Recommended packages:
  mail-transport-agent
The following NEW packages will be installed:
  lvm-common lvm2 mdadm
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 469kB of archives.
After unpacking 1479kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com edgy/main mdadm 2.4.1-6ubuntu5 [152kB]
Get:2 http://us.archive.ubuntu.com edgy/main lvm-common 1.5.20ubuntu7 [16.9kB]
Get:3 http://us.archive.ubuntu.com edgy-updates/main lvm2 2.02.06-2ubuntu3.2 [300kB]
Fetched 469kB in 2s (227kB/s)
Preconfiguring packages ...
Selecting previously deselected package mdadm.
(Reading database ... 16034 files and directories currently installed.)
Unpacking mdadm (from .../mdadm_2.4.1-6ubuntu5_i386.deb) ...
Selecting previously deselected package lvm-common.
Unpacking lvm-common (from .../lvm-common_1.5.20ubuntu7_i386.deb) ...
Selecting previously deselected package lvm2.
Unpacking lvm2 (from .../lvm2_2.02.06-2ubuntu3.2_i386.deb) ...
Setting up mdadm (2.4.1-6ubuntu5) ...
Generating mdadm.conf... done.
update-initramfs: Generating /boot/initrd.img-2.6.17-10-server
 * Starting RAID monitoring service mdadm --monitor                      [ ok ]

Setting up lvm-common (1.5.20ubuntu7) ...

Setting up lvm2 (2.02.06-2ubuntu3.2) ...
Backing up any LVM2 metadata that may exist...done.
```

Looking pretty good from here, but when i try to run the first command..
```
sudo pvcreate /dev/hdb
```
i get this..
```
 No program "pvcreate" found for your current version of LVM
```

why didn't **pvcreate** get installed?

---

### Post by geppy on 2006-12-05
I'm experiencing the same problem with all of the pv* tools (pvchange, pvdisplay, pvmove, pvremove, pvresize, pvs, pvscan and pvcreate).

I'm using Ubuntu 6.10 and package 2.02.06-2ubuntu3.2 of 'lvm2'.

---

### Post by AusIV4 on 2006-12-05
I had similar problems getting LVM and RAID to work on Edgy. After several hours of hassle, I switched back to Dapper, which installs both from the LiveCD.

I know that's not what you want to hear, and some people may have found a solution, but I do think it's the best solution. I wish the website would make it clear that Dapper is the more stable and reliable version, so people would find out before they come to the forum with their problems.

---

### Post by geppy on 2006-12-05
Try the lv* tools instead: e.g. lvcreate.

---

### Post by hellsing on 2006-12-14
this worked for me:
apt-get remove --purge lvm10 lvm-common
apt-get install lvm2

---

### Post by Panhead Bill on 2006-12-19
hellsing;  Any other suggestions?

I tried your remove/install commands, but still got the "not in my version" message.  I also tried at level 1 (which dapper seemed to require).

---

### Post by Panhead Bill on 2006-12-19
hI filed a bug report on malone  Bug #76534

---

### Post by joebwan on 2006-12-20
This may be a dumb suggestion, but I had the same problem and I issued

/etc/init.d/lvm start

and then I no longer received errors about pvcreate version not matching.

---

### Post by Panhead Bill on 2006-12-21
Joebwan;  
That worked for me.  Thanks.

---

### Post by davemc on 2006-12-29
I've experienced the same error with a different scenario.

Boot Dapper from a live CD

Mount a another partition also already installed with Dapper, and using LVM, then 

chroot to the mounted partition.

Any LVM command gives this error.  Version on live CD and installed is 2.02.02-1ubuntu1

---

### Post by changlinn on 2007-01-04
that fixed it for me hellsing, thanx, that and joebwan

---

### Post by grimdestripador on 2007-03-17
> **joebwan said:**
> This may be a dumb suggestion, but I had the same problem and I issued

/etc/init.d/lvm start

and then I no longer received errors about pvcreate version not matching.

Heh, that did it for me.

---

