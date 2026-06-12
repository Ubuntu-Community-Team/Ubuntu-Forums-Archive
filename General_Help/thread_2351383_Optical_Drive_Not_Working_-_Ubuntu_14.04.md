---
title: "Optical Drive Not Working - Ubuntu 14.04"
date: 2017-02-02
forum: General Help
---

### Post by akaPrilly on 2017-02-02
Hello, folks.  I have decided to try to embark on fixing an several issues I have been dealing with for a number of months now.  The first of which is being that my optical drive fails to show up in the system dock when I insert media into it.  It is also notable that I am also having the same issue when connecting two different USB hard drives. Interestingly enough, a thumb drive inserted into the same USB port(s) loads right up.  The problem seems to have manifested itself after I changed the location of my Home folder to a different hard drive.  Perhaps the problem is with the modified Fstab?  Here is my current Fstab which was modified based on instruction I gathered from various sources online:

[TABLE="width: 500"]
[TR]
[TD]# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during installation
UUID=2b38f170-386f-4ec4-9ab4-9d522b516607 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda3 during installation
#UUID=2367e913-b02e-4ddc-8a59-3bd78c6a729f none            swap    sw              0       0


/dev/mapper/cryptswap1 none swap sw 0 0


# (identifier)  (location, eg sda5)   (format, eg ext3 or ext4)      (some settings) 
UUID=206d72f4-1723-4c5e-9b31-cf8a0826078d	/home	ext4	defaults	0	2
[/TD]
[/TR]
[/TABLE]

UUID=206...078d is the drive where my home folder is
UUID=2b38...607 is the drive where my OS is installed

These are presently the only two devices shown after running this command in Terminal:
[TABLE="width: 500"]
[TR]
[TD]ls /dev/disk/by-uuid -lt [/TD]
[/TR]
[/TABLE]

I am not sure what the UUID is for my optical drive.   For now, I have to presume it is the other UUID listed in Fstab.  

Any suggestions of what to try would be greatly appreciated.

---

### Post by Keith_Helms on 2017-02-03
Fstab is used for drives that are automatically mounted at boot time.  Look under your settings for something like removable drives and media.  That will contain the options for what to do when a disc or USB drive is inserted.

---

### Post by akaPrilly on 2017-02-03
Up to now, I have thought that a permanent piece of hardware such as a CDROM drive was mounted at the time the OS was loaded.  I am now beginning to understand that a device connected or seen by the OS does not necessarily mean the device is mounted.  My new understanding is that something like an optical drive would only mount to the system when media is present (e.g a disk is inserted).   I feel that I have made some progress with solving this issue on my own.  I have been able to "see" my optical drive under Disks utility but it says "no media" even when there is a disk inserted.  This includes and audio CD and a Data DVD.  Disks utility also seemed to recognize one of my external USB drives also; the other one I have doesn't get recognized at all. After messing with my system and countless searches online,  I soon came to the realization that my USB hard drive wasn't being mounted because the partition was formatted as a master boot record.  I ran Gparted application and changed it to EXT 4 and it voila! It mounted!  I do not think this is the same problem with my other drive because it connects just fine to my laptop running 16.04.  Still no luck with the optical drive.  I am starting to wonder if perhaps my problem here might be what I really didn't consider at all.   -That maybe my drive has stopped reading disks.  

Optical drive is showing to be at location /dev/sr0  

I have tried to manually mount it and terminal response is:

mount: no medium found on /dev/sr0

Finally, I attempted to boot to DVD using an Ubuntu 16.04 DVD I burned (on my laptop).  That didn't work either.  

Thoughts????

---

### Post by akaPrilly on 2017-02-05
Issue resolved.  The problem was a bad DVD drive.  Just replaced drive with a brand new one and I am presently burning a test DVD with it.

---

