---
title: "Flash drive mounting read only"
date: 2020-11-26
forum: General Help
---

### Post by Softa on 2020-11-26
I have a brand new flash drive that I need to copy some files to.  However, it always mounts as owned by root and read only for everybody else.  My brother has mounted the drive on a computer running Fedora, and it mounts correctly, so I know the drive's OK.  What can I do to get the drive to work properly on my computer?

---

### Post by ajgreeny on 2020-11-26
For a start, with the flash drive attached, let's see the output of terminal command ***sudo fdisk -l*** which will tell us more about the flash drive and its filesystem, etc, etc.

---

### Post by ActionParsnip on 2020-11-26
Before you physically unplug the device do you use the safe remove feature in the OS?
What file system are you using on the USB storage?

---

### Post by Softa on 2020-11-27
Here's the relevant part of the response to fdisk -l:

/dev/sdf1          32 31260671 31260640 14.9G  c W95 FAT32 (LBA)

---

### Post by Softa on 2020-11-27
Of course I use the safe removal, but what does that matter, as the issue cropped up the first time I inserted it.  When I first tried to use the drive, it had the filesystem on it that it was formatted with at the factory, probably FAT32, and when I reformatted it, that's what I gave it.

---

### Post by ajgreeny on 2020-11-27
Let's  see what the permissions are for the flash disk with command ***ls -ls /media/username/diskident*** 

Change the username and diskident to your own system, of course, and note that this is assuming the flash drive is automounted when you insert it.

---

### Post by TheFu on 2020-11-27
> **Softa said:**
> Of course I use the safe removal, but what does that matter, as the issue cropped up the first time I inserted it.  When I first tried to use the drive, it had the filesystem on it that it was formatted with at the factory, probably FAT32, and when I reformatted it, that's what I gave it.

It matters for a number of reasons.

FAT32 permissions are controlled through mount options.  It is possible that whoever first connected the flash drive setup the mount options to work for just their userid.  NTFS, exFAT, and other non-Linux file systems have this problem.

The mount options are what matter.  Let me try to find a FAT32 flash device.

Ok - found one:
```
$ lsblk -e 7 -o name,size,type,fstype,mountpoint
NAME                                SIZE TYPE FSTYPE      MOUNTPOINT
sdb                                 962M disk             
&#9492;&#9472;sdb1                              961M part vfat        
```
Let's mount with default options:
```
$ sudo mount /dev/sdb1 2/
$ mount |egrep 'sdb1|Avail'
/dev/sdb1 on /mnt/2 type vfat (rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/mnt/2$ ll
total 8
drwxr-xr-x 2 root root 4096 Dec 31  1969 ./
drwxr-xr-x 7 root root 4096 Sep  4 07:57 ../
```
So root:root are the owner and group. That isn't very useful.  To mount with useful options ... hummmm. First I need to umount it. Done. Let's try that mount again, but gather the uid and gid first:
```
$ id
**uid=1000**(tf) **gid=1000**(tf) groups=1000(tf),4(adm),24(cdrom),27(sudo),29(audio),30(dip),46(plugdev),110(lxd),116(libvirtd),117(lpadmin),118(sambashare)

/mnt$ sudo mount **-o uid=1000,gid=1000** /dev/sdb1 2/
/mnt$ touch 2/my-new-file
/mnt$ ls -la 2/
total 8
drwxr-xr-x 2 tf   tf   4096 Dec 31  1969 ./
drwxr-xr-x 7 root root 4096 Sep  4 07:57 ../
-rwxr-xr-x 1 tf tf        0 Nov 27 08:59 my-new-file*
```

Perfect.
The uid needed was found using the 'id' command, as shown above. Same for the gid. The owner and group for the mount matter.  There are other options.

If 'id' said your uid or gid were 1009 and 1010, then use those numbers, respectively.  System accounts have uids less than 1000.  The first account on any Ubuntu system, created at install time will begin from 1000 and increment by 1 for each new userid created.  Whatever the highest number is plus 1 more, will get selected when a new userid is created.  The method doesn't reuse old, deleted, accounts.  I think it is a 32-bit number, so 64K accounts (64535?) are allowed. The most I've ever seen used on a network was around 8,000 userids.

I'm almost positive there is an easier way to accomplish this. I don't mount storage in this way, but the method I use has some setup using a tool called **autofs** tied to the LABEL for mount locations. I'm betting that others here know an easier, GUI, way?

Or just use **f2fs** which honors all Unix ownership, groups, permissions, ACLs, and xattrs. Then we can just use normal Unix permission management tools - chown, chmod, chgrp and don't need to worry about mount options.  f2fs is supported on Android now and it is faster than ext4 while being kind to flash storage with fewer writes.

---

### Post by Frogs Hair on 2020-11-27
There is an old open bug on this issue. I remember being briefly affected.

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1021375](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1021375)

---

### Post by Softa on 2020-11-30
It's mounted as /media/usb:

lrwxrwxrwx 1 root root 4 Dec 21  2016 usb -> usb0

---

### Post by Softa on 2020-11-30
> **TheFu said:**
> It matters for a number of reasons.

FAT32 permissions are controlled through mount options.  It is possible that whoever first connected the flash drive setup the mount options to work for just their userid.  NTFS, exFAT, and other non-Linux file systems have this problem.

I was the first consumer to mount the drive, and it was already like that on Ubuntu, but it worked OK on my brother's computer with Fedora.  He's reformatted it, and it still doesn't work on my computer.

---

### Post by Softa on 2020-11-30
> **Frogs Hair said:**
> There is an old open bug on this issue. I remember being briefly affected.

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1021375](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1021375)

So it's an old, known bug with no workaround, right?  I'd have to change the ownership and/or permissions every time I use it, right?

---

### Post by TheFu on 2020-11-30
> **Softa said:**
> It's mounted as /media/usb:

lrwxrwxrwx 1 root root 4 Dec 21  2016 usb -> usb0

Sorry, I don't know what you are trying to show above.  A symbolic link as usb --> usb0  in the same location from 2016 doesn't really seem relevant.  I must be missing something.

The commands and sample output that I've posted were trying to get you do perform the same commands, but post YOUR different output, so we can see some details.  Sorry, if that wasn't clear.

---

