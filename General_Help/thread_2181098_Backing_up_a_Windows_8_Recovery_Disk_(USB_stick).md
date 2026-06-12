---
title: "Backing up a Windows 8 Recovery Disk (USB stick)"
date: 2013-10-16
forum: General Help
---

### Post by brendonwp on 2013-10-16
Hi all

I am trying to do something that should be relatively simple. I've found instructions on how to use dd to create an image file from a memory stick (see at bottom).

For some reason the USB with the Windows 8 recovery information is not seen under Ubuntu 12.04 at all.  Any hints on where I should go from here?

Thanks
Brendon


Problem summary: 

o My wife has a new Windows 8 desktop at home.
o I've run the Lenovo control centre's function to copy the restore partition to a USB memory stick.
o The restore partition was deleted off the hard drive in the process.
o I want to duplicate the memory stick but Ubuntu 12.04 does not see it at all.


Procedure to go from USB stick to ISO:

from tomshardware forum:

chamaecyparis September 6, 2011 2:05:23 PM
Use the dd command as root after unmounting the USB drive.

Should you not know how, first learn how your USB stick is recognized by the system 

ls -l /dev/disk/by-id/*usb*

Unmount it

umount /dev/sdX

Make the ISO

dd if=/dev/sdX of=/path/to/your.iso

---

### Post by fantab on 2013-10-16
... but is the back up you made to USB an .iso? 
Why can't you use any Windows partition recovery tool to restore the lost/deleted partition?
Can you plug in the USB with backup and from ubuntu terminal post the output of:
```
sudo fdisk -l
sudo parted -l
```?

---

### Post by brendonwp on 2013-10-16
Thanks fantab.  Done it, and seems to be FAT32.  No idea why it won't appear in nautilus..

sudo fdisk -l:

```
$ sudo fdisk -l

...<hdd info removed>


Disk /dev/sdd: 8027 MB, 8027897856 bytes
255 heads, 63 sectors/track, 976 cylinders, total 15679488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *        2048    15679487     7838720    b  W95 FAT32

```


sudo parted -l:

```
sudo parted -l

...<hdd info removed>


Model: JetFlash Transcend 8GB (scsi)
Disk /dev/sdd: 8028MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start   End     Size    Type     File system  Flags
 1      1049kB  8028MB  8027MB  primary  fat32        boot

```

---

### Post by fantab on 2013-10-16
So Ubuntu 12.04 sees it.
Only .iso file can be *burned* to usb device with dd command (dd if=/dev/sdX of=/path/to/your.iso). You cannot make an .iso with it.
This is why I asked, "is the back up you made to USB an .iso?"

---

### Post by brendonwp on 2013-10-16
OK, so I can probably use something like Brasero then if dd will not do it.  Have tested Brasero with CDs.

Any idea why the memory stick is not auto-mounted like other USBs?  I suppose I need to explicitly run a mount command to look at it..

Thanks
B

---

### Post by sudodus on 2013-10-16
No, don't use Brasero!

You can make a compressed image file of your pendrive and save it on some media. I would recommend that you keep your backup on an external HDD, backup of 'everything' valuable enough to backup. So one of those things should be a backup of your Windows 8 recovery disk (USB stick).

You can use dd for it. But ***beware***, it is nicknamed 'disk destroyer' because it does what you tell it to do, and if it is different from what you intend to do, you might wipe some device that is not yet backed up. So double-check and triple-check.

Making the image file is less dangerous, restoring is more dangerous, but both operations are risky. You can [use this shell-script method to make restoring from the image safer]("http://ubuntuforums.org/showthread.php?t=1958073"). So use ***mkusb*** to restore it.

Check that the pendrive is not mounted. Unmount if necessary.

Identify the pendrive (the device letter in /dev/sda, /dev/sdb, /dev/sdc ...) with the commands

```
sudo fdisk -lu
sudo parted -l
```
and umount it with
```
sudo umount /dev/sd[COLOR=#ff0000]x[/COLOR]*
```

Change directory to the drive and directory, where you want to write the image file. Use ***dd*** to clone and ***gzip*** to compress like this

```
cd 'path-to-where-to-keep-the-backup'
sudo -s     # run as superuser 
dd if=/dev/sd[COLOR=#ff0000]x[/COLOR] bs=4096 | gzip > win8recovery.img.gz
sync        # make sure all read/write operations have finished, wait for the prompt
exit        # exit from superuser prompt
```

where [COLOR=#ff0000]x[/COLOR] is the device letter for the pendrive (only a letter, no digit).

It is a good idea to test that it really works (install to another pendrive and test it).

---

### Post by brendonwp on 2013-10-16
Thanks sudodus, will follow your advice!

---

### Post by sudodus on 2013-10-17
Good luck :-)

---

