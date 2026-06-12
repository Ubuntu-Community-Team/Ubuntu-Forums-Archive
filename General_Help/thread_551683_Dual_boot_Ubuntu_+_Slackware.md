---
title: "Dual boot Ubuntu + Slackware"
date: 2007-09-15
forum: General Help
---

### Post by EYEdROP on 2007-09-15
I want to dual boot slaackware 12.0 with ubuntu on my system. I currently have ubuntu installed on my primary HD. It looks like the whole disk is in use by Ubuntu: 
 
ian@PR0BATR0N:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hda1             73939452  38290040  31893420  55% /
varrun                  517884       144    517740   1% /var/run
varlock                 517884         0    517884   0% /var/lock
procbususb              517884       120    517764   1% /proc/bus/usb
udev                    517884       120    517764   1% /dev
devshm                  517884         0    517884   0% /dev/shm
lrm                     517884     15092    502792   3% /lib/modules/2.6.20-16-generic/volatile
/dev/hdc               3803258   3803258         0 100% /media/cdrom0
/dev/disk/by-label/SAVE
                     245111704 142568364 102543340  59% /mnt
ian@PR0BATR0N:~$ 
 
I want to install Slackware on hda1, but I think Ill have to make some free space first. How do I do this? I cant seem to do it in cfdisk, fdisk, or Gparted. Any help?

---

### Post by The_PhAnT0m on 2007-09-15
I'm not totally sure what you are trying to do. Are you trying to free space with Gparted?

---

### Post by dpar on 2007-09-15
If you are trying to free space with gparted, you will have to use the livecd. You can't mess with the partition when it is mounted by ubuntu.

---

### Post by EYEdROP on 2007-09-15
> **dpar said:**
> If you are trying to free space with gparted, you will have to use the livecd. You can't mess with the partition when it is mounted by ubuntu.

I tried to use fdisk and cfdisk when istalling slackware, but it didnt look like it had the option to resize. Are there any ways I can do this through the shell in the slackware installation?

---

### Post by dpar on 2007-09-15
I've never installed Slackware, but usually ther is an option to resize the partition during the install.

---

