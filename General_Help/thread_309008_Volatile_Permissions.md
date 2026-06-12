---
title: "Volatile Permissions"
date: 2006-11-29
forum: General Help
---

### Post by joegumbo on 2006-11-29
Hi,

     I'm running Ubuntu 6.10 Edgy Eft and I'm having an issue with permissions on my external HD.  I used to just be able to turn it on and I could read/write to it.  However, first several files, then eventually all the files have icons with lock symbols on them.  I've tried " chmod 666 /media/usbdisk", but I'm informed that the disk is "Read Only".  I'v tried  sudo nautilus and then browsing to the external hd, and then cahnging permissions under Properties,  only to be notified that the disk is "Read Only."  I can still read the hd, but I can no longer write to it.

Thank you,
-Joe G

---

### Post by aysiu on 2006-11-29
Can you plug the drive into your computer and post the output here of these terminal commands? ```
sudo fdisk -l
cat /etc/fstab
df -h
```

---

### Post by CatKiller on 2006-11-29
It's possible that the drive has been re-mounted as read-only because of problems with the drive.

---

### Post by joegumbo on 2006-11-29
Thanks,

joegumbo@joegumbo-desktop:~$ sudo fdisk -l
Password:

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *         524        8543    64420650    7  HPFS/NTFS
/dev/hda2               1         523     4200966    b  W95 FAT32
/dev/hda3            8544       19323    86590350   83  Linux
/dev/hda4           19324       19457     1076355    5  Extended
/dev/hda5           19324       19457     1076323+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sde: 80.0 GB, 80026361344 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1        9729    78148161    c  W95 FAT32 (LBA)
joegumbo@joegumbo-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=dd14dfbc-96cf-47e8-8f33-476ec0bfc508 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=14dbca25-fb38-4c55-b140-66422ae972de none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
joegumbo@joegumbo-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda3              82G   25G   53G  32% /
varrun                181M   80K  181M   1% /var/run
varlock               181M     0  181M   0% /var/lock
procbususb             10M  132K  9.9M   2% /proc/bus/usb
udev                   10M  132K  9.9M   2% /dev
devshm                181M     0  181M   0% /dev/shm
/dev/sde1              75G   19G   57G  25% /media/usbdisk
joegumbo@joegumbo-desktop:~$

---

### Post by joegumbo on 2006-11-29
"It's possible that the drive has been re-mounted as read-only because of problems with the drive."

Hi CatKiller,

It works fine under XP.

Thanks,
-Joe G

---

### Post by aysiu on 2006-11-29
What CatKiller says is true--it could have to do with some kind of drive corruption. Let's assume for now that's not the case, though.

I don't know why this is happening, but let's say we manually mount the drive. Maybe that'll solve it.

Let's unmount it first: ```
sudo umount /media/usbdisk
``` Create a new mount point ```
sudo mkdir /usbdisk
``` Make a backup copy of the /etc/fstab ```
sudo cp /etc/fstab /etc/fstab061128
``` Edit /etc/fstab ```
gksudo gedit /etc/fstab
``` Add this line in at the end: ```
/dev/sde1 /usbdisk vfat iocharset=utf8,umask=000 0 0
``` Save and exit and remount the drive ```
sudo mount -a
``` Then go to /usbdisk and see if everything's still locked.

If so, it may be what CatKiller suspects...

P.S. I'm mounting it outside of /media because I've seen rare cases on these forums of mounting FAT32 within /media somehow giving buggy permissions on certain folders on the drive.

---

### Post by CatKiller on 2006-11-29
> **joegumbo said:**
> It works fine under XP.

Ah, but maybe it doesn't and XP hasn't noticed ;)

I just mentioned it as a possibility, since it can happen. It's a more sensible approch than blindly carrying on with writing to the drive, I suppose. I don't really know how you'd test for it, other than with the manufacturer's boot floppy, and I don't know how you'd go about fixing it.

aysiu knows more than me though, so he may have cunning solutions to your problem :)

EDIT: > **aysiu said:**
> What CatKiller says is true--it could have to do with some kind of drive corruption. Actually, I was thinking that it might be USB, FireWire or shonky-cable-related as possibilities, too. Hopefully it isn't, though.

---

### Post by joegumbo on 2006-11-29
When I browse to Places> /usbdisk , everything is still locked.  

When I sudo nautilus to Filesystem>usbdisk, the usbdisk icon has alock on it, but when I go to Properties, now ROOT owns the files.  I think we're making progres.

Thank you,
-Joe

---

### Post by aysiu on 2006-11-29
Hm. I'm stuck. Are you able to create new folders on the drive or create new files on it?

Is it just the preexisting folders that are locked?

---

### Post by joegumbo on 2006-11-29
Hi Aysiu,

     I cannot create new folders.  Also, when I take a different path to it, Places>Computer>usbdisk, under Properties, the owner is listed as "unknown."  

If I follow the path Places>/usbdisk, the owner is ROOT.

Thanks,
-Joe

---

### Post by aysiu on 2006-11-29
I'm not sure if it makes any difference, but what if you don't go through Places?

What happens if you press Alt-F2, type ```
nautilus
``` and then in the location bar (Control-L) type ```
/usbdisk
``` ? No different?

---

### Post by joegumbo on 2006-11-29
I can browse there, but I cannot create  or delete folders.  

I also tried umountinmg,.  Now, I need to su - to root and then umount /dev/sde1 in order to umount usbdisk.  I don't seem to be able to launch nautilus as root.  I wonder if I can browse as root if I couild read / write.

-Joe

---

### Post by joegumbo on 2006-11-29
I also tried:

joegumbo@joegumbo-desktop:~$ su -
Password: 
root@joegumbo-desktop:~# cp /home/joegumbo/ACBA /usbdisk
cp: cannot create regular file `/usbdisk/ACBA': Read-only file system


So, even though ROOT owns /usbdisk, I cannot write to it.

---

### Post by joegumbo on 2006-11-29
Also, something esle is weird...

When I browse  Places>Computer?usbdisk and the try opening as Administrator,  nautilus crashese and an error report is sent about CD/DVd creator.  I think Ubuntu now thinks that  my usbdisk is a CD-Rom or DVD-rom.

-Joe

---

### Post by aysiu on 2006-11-29
I'm afraid this is out of my league, but [this thread](http://ubuntuforums.org/showthread.php?p=1706204) may help you.

---

### Post by joegumbo on 2006-11-29
Thank you fro trying, Aysiu,

I did try following the instructions in the thread you suggested. Unfortuneately, I can lo longer even mount to read the usbdisk.  

joegumbo@joegumbo-desktop:~$ su
Password: 
root@joegumbo-desktop:/home/joegumbo# mount /dev/sde1
mount: wrong fs type, bad option, bad superblock on /dev/sde1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

root@joegumbo-desktop:/home/joegumbo# dmesg | tail
[17237009.868000] SCSI device sde: 156301487 512-byte hdwr sectors (80026 MB)
[17237009.872000] sde: Write Protect is off
[17237009.872000] sde: Mode Sense: 03 00 00 00
[17237009.872000] sde: assuming drive cache: write through
[17237009.872000]  sde: sde1
[17237009.876000] sd 8:0:0:0: Attached scsi disk sde
[17237009.876000] sd 8:0:0:0: Attached scsi generic sg4 type 0
[17237027.164000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[17237027.164000] FAT: invalid media value (0x64)
[17237027.164000] VFS: Can't find a valid FAT filesystem on dev sde1.
root@joegumbo-desktop:/home/joegumbo# fsck -a /dev/sde1
fsck 1.39 (29-May-2006)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
Currently, only 1 or 2 FATs are supported, not 37.

root@joegumbo-desktop:/home/joegumbo# 

From what I read on this thread, it appears that Ubuntu might have a bug in this regard.

Thank you,
-Joe

---

### Post by joegumbo on 2006-11-29
> **CatKiller said:**
> Ah, but maybe it doesn't and XP hasn't noticed ;)

I just mentioned it as a possibility, since it can happen. It's a more sensible approch than blindly carrying on with writing to the drive, I suppose. I don't really know how you'd test for it, other than with the manufacturer's boot floppy, and I don't know how you'd go about fixing it.

aysiu knows more than me though, so he may have cunning solutions to your problem :)

EDIT:  Actually, I was thinking that it might be USB, FireWire or shonky-cable-related as possibilities, too. Hopefully it isn't, though.

Hi CatKiller,

     Maybe you're right.  I'll try booting into windoze and seeing if I have any utilities that can check for thr integrity of this drive.

Thank you,
-Joe

---

