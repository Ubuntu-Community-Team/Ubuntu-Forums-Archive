---
title: "Trouble with Swap Partition"
date: 2007-11-18
forum: General Help
---

### Post by benjamin222 on 2007-11-18
Hey! I just installed kubuntu a few days ago, way new to linux. Anyway when I installed it I didnt set up a swap partition. My friend said it wasnt necessary. Well I want to be able to hibernate, so now Im trying to set it up. 

So far I've restarted using the livecd and used qtparted to set up the swap partition. All went ok. Then I restarted from hard disk, went to system settings > advanced > Disk & Filesystems, and enabled the new partition I made as a swap partition. Now Kinfo shows the correct 1.5 gb I allocated for swap, but if I restart my computer it says swap unavailable and I have to go through the whole thing again. And on top of that, still can't hibernate, even when it says swap is active.

Could it have anything to do with the swap partition under options saying "noauto"? if so what should it be? 

Thanks!!!

---

### Post by PmDematagoda on 2007-11-18
Please post your fstab file using:-

```
cat /etc/fstab
```

---

### Post by benjamin222 on 2007-11-18
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
# /dev/sda3
UUID=52695ff1-48b1-40af-a900-5e28cf36ffa4 / ext3 nouser,defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1
# /dev/sda1
UUID=33B627632DC41DE7 /media/sda1 ntfs defaults,umask=007,uid=0,gid=46,auto,rw,nouser 0 1
# /dev/sda2
UUID=4B6E-6BC0 /media/sda2 vfat defaults,utf8,umask=007,uid=0,gid=46,auto,rw,nouser 0 1
/dev/hdc /media/cdrom0 udf,iso9660 user,atime,noauto,rw,dev,exec,suid 0 0
/dev/hdd /media/cdrom1 udf,iso9660 user,atime,noauto,rw,dev,exec,suid 0 0
/dev/sda4 <mount\040point> swap noauto 0 0

---

### Post by PmDematagoda on 2007-11-18
> **benjamin222 said:**
> 
/dev/sda4 <mount\040point> swap noauto 0 0

That line doesn't look right, open up the fstab file for editing using:-

```
sudo gedit /etc/fstab
```

and change the line to this:-

```
/dev/sda4 none swap sw 0 0
```
Then see if the Swap partition is mounted at start-up.

---

### Post by benjamin222 on 2007-11-18
Sweet thanks a lot for helping out. Just making sure I got this right...

so I'm just changing the last line on the fstab file so now my fstab file should look like this?...


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
# /dev/sda3
UUID=52695ff1-48b1-40af-a900-5e28cf36ffa4 / ext3 nouser,defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1
# /dev/sda1
UUID=33B627632DC41DE7 /media/sda1 ntfs defaults,umask=007,uid=0,gid=46,auto,rw,nouser 0 1
# /dev/sda2
UUID=4B6E-6BC0 /media/sda2 vfat defaults,utf8,umask=007,uid=0,gid=46,auto,rw,nouser 0 1
/dev/hdc /media/cdrom0 udf,iso9660 user,atime,noauto,rw,dev,exec,suid 0 0
/dev/hdd /media/cdrom1 udf,iso9660 user,atime,noauto,rw,dev,exec,suid 0 0
/dev/sda4 none swap sw 0 0



yeah again sorry im way noobish

---

### Post by PmDematagoda on 2007-11-18
Yes, now reboot the system and see if that solves your problem.

---

### Post by benjamin222 on 2007-11-18
hey,,, so it kinda worked, Upon reboot it correctly showed 1.5 gigs of available swap.

But then I tried to hibernate, and the computer just showed a whole bunch of error messages and turned off completely

After turning it back on... no swap available.. and I'll probably have to reformat the partition back as a swap partition.. same thing I did before..

Maybe this is just a complicated hibernation problem where hibernating isnt working and just destroying my swap partition... hmm

---

### Post by PmDematagoda on 2007-11-18
It could be that Hibernate is corrupting the fstab file, could you please repost the fstab file?

---

### Post by benjamin222 on 2007-11-18
yeah checked it.. pretty sure its all the same...

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
# /dev/sda3
UUID=52695ff1-48b1-40af-a900-5e28cf36ffa4 / ext3 nouser,defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1
# /dev/sda1
UUID=33B627632DC41DE7 /media/sda1 ntfs defaults,umask=007,uid=0,gid=46,auto,rw,nouser 0 1
# /dev/sda2
UUID=4B6E-6BC0 /media/sda2 vfat defaults,utf8,umask=007,uid=0,gid=46,auto,rw,nouser 0 1
/dev/hdc /media/cdrom0 udf,iso9660 user,atime,noauto,rw,dev,exec,suid 0 0
/dev/hdd /media/cdrom1 udf,iso9660 user,atime,noauto,rw,dev,exec,suid 0 0
/dev/sda4 none swap sw 0 0

---

### Post by benjamin222 on 2007-11-18
ok and now i just checked qtparted, what i found was the 1.5 gig partition i made is now showing up "unknown"

---

