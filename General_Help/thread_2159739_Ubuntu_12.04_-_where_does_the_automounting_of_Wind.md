---
title: "Ubuntu 12.04 - where does the automounting of Windows partitions happen?"
date: 2013-07-04
forum: General Help
---

### Post by mailforbiz on 2013-07-04
Hi

I was trying to do some adjustment to the way my Windows partitions are automounted and realized that my /etc/fstab doesn't have entries for automounting but still the Windows partitions ARE getting automounted in nautilus as I can see them there , albeit they are mounted in RO mode. I am scratching my head now - I always thought this was due to me having added them to the fstab before but looks like I was wrong.

Does this automounting take place somewhere else now , like grub? Would appreciate if anyone can solve this mystery. My purpose is to load one of the partitions in RW mode.

HT

---

### Post by Morbius1 on 2013-07-04
This is now the 4th post that I know of that has suggested that Ubuntu has become sentient and is mounting these partitions by itself - just because it can. In those other posts the OP was politely told to stop using drugs and stay in school since this was simply not possible. Four posts makes a trend though so .....

Let's get rid of the usual suspects:

[1] Is this a true dual boot or is this a Wubi ( install within Windows ) install?

[2] Back in the olden tymes when one clicked on the partition label on the left side of Nautilus he was asked to provide the sudo password to actually mount it but that doesn't happen anymore. Clicking on it as a non-root user now automatically mounts it and the user doesn't even realize that this is actually mounting the partition. Could this be the case or do you know for a fact that it is truly mounting by itself. One way to find out is not use Nautilus but simply run the following command at the next reboot to see if it's really mounting by itself:
```
mount
```

[3] I don't use KDE but there seems to be some option somewhere where one can tell it to mount these partitions automatically but there is no such option in Gnome so which Desktop Environment are you using?

[4] These are all internal partitions right? Not USB?

---

### Post by efflandt on 2013-07-04
Running the typical default 12.04 (Unity) from it own partition(s) does not automount Windows partitions unless you click on one in the file manager, and then fuse automounts it in /media, without anything in fstab.

Example before clicking on my Win7 partition (MEMORY 8000 is automounted USB mass-storage in a mouse receiver):```
ls -l /media
total 20
drwxr-xr-x 2 root     root      4096 May  9 09:29 cdrom
drwx------ 2 efflandt efflandt 16384 Dec 31  1969 MEMORY 8000
```After clicking on my Win7 partition in file manager (nautilus):```
ls -l /media
total 28
drwxr-xr-x 2 root     root      4096 May  9 09:29 cdrom
drwx------ 2 efflandt efflandt 16384 Dec 31  1969 MEMORY 8000
drwx------ 1 efflandt efflandt  8192 Jun 19 22:12 OS
```What it is called depends whether it has a partition label (if no label may be mounted by its UUID). And note that permissions and "mount" (or /etc/mtab) show it as rw:
/dev/sda3 on /media/OS type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)

And if you click the little up arrow thing next to it in the left panel of the file manager it umounts.

I have never used wubi, so not sure how that would mount it (or other desktops). Or mounting ro may mean the Linux thinks there may be a problem that it does not want to tamper with. My main Linux system would spontaneously remount ro when my hard drive was failing (everything is now on a new drive).

---

### Post by Mark Phelps on 2013-07-04
Do NOT automount any Windows OS partition read/write -- doing so is asking for filesystem corruption.  If you must access a Windows OS partition from inside Ubuntu, then be sure to mount it only Read-only.  

You CAN mount Windows Data partitions r/w -- but if you hibernate Windows while in Ubuntu, that can cause serious filesystem corruption.

---

### Post by mailforbiz on 2013-07-04
Thanks everyone  for your replies ... and sorry for the false alarm, it is only mounting on the click. 

 efflandt and morbius1 -
I think you're right, they mount when I click on the drive letter in Nautilus. It SEEMED like they were already mounted but apparently not.

morbius1 -
Its not WUBI - its a dual boot with Windows 7 which is on primary partition. I am using Gnome 3 (or Unity or whatever its called now, sorry I don't keep up with the DEs anymore). And yes, these were internal partitions.


Mark -
thanks for the advice, yes, I understand the precariousness of loading the Win partition in RW mode. This is just a one time thing but your warning is heeded :-)


HT
[who btw is too old for drugs, college and by the look of it, fancy new Desktop Environments]

---

