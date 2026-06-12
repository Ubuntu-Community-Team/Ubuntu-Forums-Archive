---
title: "How to mount drive to user (using fstab)"
date: 2013-06-06
forum: General Help
---

### Post by cincinnatus13 on 2013-06-06
Alright, so trying to work around my Plex issue..I just want to mount my external to my user each time so Plex can just run fine. I tried permissions and all that but it is in exfat which creates a whole other set of problems.

Anyway, looking over the fstab function would the code to enter be

uuid="whatfstabspitoutinthelist" /media/myuser/usbdirectory exfat user 0 0

?

Also, if I leave out "noauto", does that mean it will auto mount under root (per SOP) or under my user since I'm the one that logged on?

Thanks for the help. Always nice to be learning something new on Linux in any case.

---

### Post by papibe on 2013-06-06
Hi cincinnatus13.

You would have to use either fat or vfat as a mount type. You can specify who will own the files using the uid, and gid options

Is this an external USB drive?

Could you post the result of these commands?
```
lsusb

sudo blkid 

sudo fdisk -l
```
Regards.

---

### Post by cincinnatus13 on 2013-06-06
```
Bus 002 Device 004: ID 1058:0748 Western Digital Technologies, Inc. 

```

```
/dev/sdd1: LABEL="***" UUID="50D9-BDC1" TYPE="exfat" 
```

```
Disk /dev/sdd: 2000.4 GB, 2000365289472 bytes
255 heads, 63 sectors/track, 243197 cylinders, total 3906963456 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc9475f7d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               2  3906963455  1953481727    7  HPFS/NTFS/exFAT

```

Blocked my hard drive name but you get the gist. I figured throw the UUID in where I stated.
So I take it exfat is not an appropriate filesystem for this? What is the difference then in using fat or vfat?

---

### Post by papibe on 2013-06-06
Oh, I see. It is actually exfat. 

You will need to install an extra package to mount it. Take a look at [this]("http://askubuntu.com/questions/100278/how-do-i-install-and-mount-an-exfat-partition").

Let us know how it goes.
Regards.

---

### Post by cincinnatus13 on 2013-06-06
No, I already have fuse and mounted it just fine. It's just that I want to mount it under my user as opposed to root for the sake of plex.

I thought Plex would be fine but it can't access it. I then was just gonna chown all the stuff on the drive from root but ran into problems because it is an Exfat FS.
Therefore I'm ready to just mount it automatically under user and I should have no problems from there on out.

---

### Post by papibe on 2013-06-06
Try this:
```

uuid="whatfstabspitoutinthelist"  /media/myuser/usbdirectory  exfat  defaults,uid=1000,gid=1000  0  0
```
where 1000 is the user's uid and guid respectively (change it if necessary).

Regards.

---

### Post by cincinnatus13 on 2013-06-06
Thank you. I believe that is exactly what I've been looking for.

Cheers.

---

