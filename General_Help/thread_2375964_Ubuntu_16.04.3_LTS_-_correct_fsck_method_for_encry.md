---
title: "Ubuntu 16.04.3 LTS - correct fsck method for encrypted LVM?"
date: 2017-10-29
forum: General Help
---

### Post by matthorton2 on 2017-10-29
hi

i'm not experiencing any errors but, out of curiosity, i want to run fsck on my encrypted LVM instillation of 16.04.3.

firstly, is this a stupid thing to want to do?

secondly, which of these methods below is correct for 16.04.3? if neither, what do i need to do differently?[URL="http://ubuntuforums.org/showpost.php?p=4524774&postcount=9"]
[/URL][URL="https://ubuntuforums.org/showthread.php?t=1697268&p=10549458#post10549458"]
[/URL][https://ubuntuforums.org/showthread.php?t=1697268&p=10549458#post10549458](https://ubuntuforums.org/showthread.php?t=1697268&p=10549458#post10549458)[URL="https://ubuntuforums.org/showthread.php?t=1697268&p=10549458#post10549458"]
[/URL]
[https://ubuntuforums.org/showthread.php?t=708291&p=4524774#post4524774](https://ubuntuforums.org/showthread.php?t=708291&p=4524774#post4524774)

thanks,
matt

---

### Post by TheFu on 2017-10-29
fsck is run on the file system, not the partition.  The file system is on the LV, so just use the canonical name for the LV. **lvdisplay** will show it.  llsblk is pretty and once you learn the path, easier.  As usual, fsck cannot be run on an already mounted partition/LV, so you'll need to umount it. There is also the /forcefsck method to get it at boot and under systemd, there is a method (you'll need to look that up).

fsck can also be performed from a live-CD/flash drive, you'll just need to manually unlock the encrypted partition, access the PVs, VGs, and LVs, then run fsck.  This is an extremely useful skill, BTW.  

Lastly, whenever encryption is used, having 100% know-you-can-restore backups is mandatory.  Any sort of disk failure, either hardware or logical will need that backup to be restored. There isn't any data recovery methods that work with encrypted volumes.  If you can't handle the backup and restore requirements, best not to use encryption at all, IMHO.

---

### Post by matthorton2 on 2017-10-29
this is my output from "lvdisplay":

```

  --- Logical volume ---
  LV Path                /dev/ubuntu-vg/root
  LV Name                root
  VG Name                ubuntu-vg
  LV UUID                O8Ecx5-MiQN-ipS9-JukY-jXlq-4Xli-siQp0d
  LV Write Access        read/write
  LV Creation host, time ubuntu, 2017-10-27 02:45:34 +0100
  LV Status              available
  # open                 1
  LV Size                289.61 GiB
  Current LE             74140
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           253:1
   
  --- Logical volume ---
  LV Path                /dev/ubuntu-vg/swap_1
  LV Name                swap_1
  VG Name                ubuntu-vg
  LV UUID                7hmeXr-yXiK-htrL-uuaJ-EYyW-O83b-SA1RLt
  LV Write Access        read/write
  LV Creation host, time ubuntu, 2017-10-27 02:45:35 +0100
  LV Status              available
  # open                 1
  LV Size                8.00 GiB
  Current LE             2048
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           253:2

```

so if i boot from live cd, manually decrypt the partition and activate the LVM... do i then run "fsck  /dev/ubuntu-vg/root"?

---

### Post by matthorton2 on 2017-10-31
Hi,

I'm currently booted from Ubuntu live CD. When I run:

```
sudo cryptsetup luksOpen /dev/hda5 crypt1
```

I get the error:
```
Device /dev/hda5 doesn't exist or access denied.
```

(It does exist...) Does anyone have any idea what I'm doing wrong?

Thanks,
Matt

---

### Post by matthorton2 on 2017-10-31
Ok, I think I've worked it out. It was a typo - "hda" should have been "sda"

Could someone please tell me if I have successfully ran fsck on my encrypted instillation?

```
ubuntu@ubuntu:~$ sudo fsck -r /dev/ubuntu-vg/root
fsck from util-linux 2.27.1
e2fsck 1.42.13 (17-May-2015)
/dev/mapper/ubuntu--vg-root: clean, 387559/18980864 files, 16037316/75919360 blocks
/dev/mapper/ubuntu--vg-root: status 0, rss 3160, real 0.206552, user 0.072000, sys 0.004000

```

---

### Post by matthorton2 on 2017-11-01
somehow this managed to mess up my user password. it would log me in but wouldn't work for sudo or authenticating in the gui. it also wouldnt unlock the screen after locking it but if i clicked on 'switch user' to take me back to the login page, it would work again

---

