---
title: "Missing Sata Drive"
date: 2008-02-26
forum: General Help
---

### Post by Robbyx on 2008-02-26
I notice a similar query elsewhere  but I am not sure if my problem is exactly  the same, in any case has anyone a solution to my problem where the folder loses its folder quality and becomes a file of unknown type.

[http://ubuntuforums.org/showthread.php?t=591288](http://ubuntuforums.org/showthread.php?t=591288)


Approx a week ago my 3Ware (8006-2) rade mirrored  drive lost its contents and could not be read. It had an unknown format.

I reformatted it and have been using it since the weekend. It is mounted into media/sda1 and was working last night. 

This morning I find that the sata1 is not present. Sda1 has disappeared from the media folder. It has ceased to be a folder and has become a file of unknown type. sda1 no longer appears in the list.

 I have not been able to delete it even under sudo.

I created a new folder called docs. Changed the fstab and did a sudo mount -a. Immediately I checked the media folder. Docs had disappeared as a folder. It has become a file of unknown type.

I just run AVG anti virus and it found nothing.

I am using gutsy.

I would appreciate some help in sorting this out. It is serious because all my data is on the sata drive.


Robin

---

### Post by astrotech226 on 2008-02-26
If the sata drive is /dev/sda, what's the result of:

```
sudo fdisk -l /dev/sda
```

Instead of using fstab, what happens is you do a real generic mount from the command line?  Make a new directory and what does this do?

```
sudo mkdir /mnt/sda1
sudo mount /dev/sda1 /mnt/sda1
```

This may not work if the drive is already mounted somewhere else even though you are showing some kind of corruption.  Does sda1 show up running just the mount command?

---

### Post by Robbyx on 2008-02-26
> **astrotech226 said:**
> If the sata drive is /dev/sda, what's the result of:

```
sudo fdisk -l /dev/sda
```

Instead of using fstab, what happens is you do a real generic mount from the command line?  Make a new directory and what does this do?

```
sudo mkdir /mnt/sda1
sudo mount /dev/sda1 /mnt/sda1
```

This may not work if the drive is already mounted somewhere else even though you are showing some kind of corruption.  Does sda1 show up running just the mount command?

```
robin@robin-desktop:~$ sudo fdisk -l /dev/sda
[sudo] password for robin:

Disk /dev/sda: 250.0 GB, 250058301440 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00075fd0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30401   244196001    7  HPFS/NTFS
robin@robin-desktop:~$ 

```

> robin@robin-desktop:~$ sudo mkdir /mnt/sda1
robin@robin-desktop:~$ sudo mount /dev/sda1 /mnt/sda1
robin@robin-desktop:~$ 


I have just done this and looked  in mmt. Using my usual file manager nothing appears there. When I looked under nautilus it showed sda1 as unknown type.

I think you are also advising I try mounting sda but not into a directory. What is the command line? This quess didn't work:
> robin@robin-desktop:~$ sudo mount sda
mount: can't find sda in /etc/fstab or /etc/mtab
robin@robin-desktop:~$ sudo mount /dev/sda
mount: can't find /dev/sda in /etc/fstab or /etc/mtab



Robin

---

### Post by Robbyx on 2008-02-26
I have been looking through the bug reports referred to in the url that I mentioned above. I do not know if I should try and follow the advice in the one I now quote below, because I have had the sata drive up and running. Those people could not load it at all, which is my current position but not yesterday's:

[https://bugs.launchpad.net/ubuntu/gutsy/+source/evms/+bug/109320](https://bugs.launchpad.net/ubuntu/gutsy/+source/evms/+bug/109320)

It also do not want to break by system with the wrong correction. Are there any ideas as to what to do?

Robin

---

### Post by Robbyx on 2008-02-26
I have it working but I still would like some help as will be obvious:

I have just restarted the machine. 

I looked in /media/ and found that doc was no longer there but /sda1 had returned as a directory.  I edited fstab and changed the sda command line from the uuid to /dev/sda1 and the load folder to sda1. Mounted the drive and it was ok and all was visible. 

I am concerned as to  why this happened. What can I  do to stop it repeating. Should I try purging all evms packages.  I do not have a lvm folder either in home or in boot.

Robin

---

