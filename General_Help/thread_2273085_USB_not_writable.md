---
title: "USB not writable"
date: 2015-04-10
forum: General Help
---

### Post by Y^2om&amp;#7sgP on 2015-04-10
Hopefully I'm posting in the correct area 

After a recent update (just over a week ago) I can no longer write to usb sticks.

I've tried so far the following

[http://ubuntuforums.org/showthread.php?t=1704147](http://ubuntuforums.org/showthread.php?t=1704147)
[http://askubuntu.com/questions/247475/automounted-usb-devices-are-read-only](http://askubuntu.com/questions/247475/automounted-usb-devices-are-read-only)

And running sudo thunar, and reformatting the stick using gparted to FAT32

Permissions for user are set to none, and if I change them as either user or sudo to R/W they change back immediately to none.

I'm running Xubuntu 14.04 LTS, with all updates as they're made available

Can anyone suggest a way of getting write permissions back?

Thanks all

---

### Post by coffeecat on 2015-04-10
You don't need sudo thunar - you don't need root privileges - and trying to change permissions on a Microsoft filesystem will not work. FAT32 doesn't support Linux permissions. Write permission is enabled by means of mount options.

Let's see what is happening - this may give us a clue as to what the problem might be. Plug the USB drive in and then post the output of these two terminal commands:

```
sudo fdisk -lu
mount
```

---

### Post by Y^2om&amp;#7sgP on 2015-04-10
utput of 
sudo fdisk -lu
```
Disk /dev/sdd: 16.2 GB, 16231956480 bytes
255 heads, 63 sectors/track, 1973 cylinders, total 31703040 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00055279

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1            2048    31703039    15850496    b  W95 FAT32
```

and mount

```
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=phatton)
/dev/sdc1 on /media/phatton/Audio type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
gvfsd-fuse on /home/phatton/.gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev)
/dev/sdb1 on /media/phatton/My Book type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdd1 on /media/phatton/Evolution-201503-64bit type vfat (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks2)
```

---

### Post by coffeecat on 2015-04-10
Your sdd1 FAT32 partition is mounted read-write, so that excludes one problem. I should have asked earlier - exactly what happens when you try to write to sdd1 by drag and drop using thunar? That is, regular thunar - not invoked by sudo. Do you get an error message? If so, what does it say?

---

### Post by Y^2om&amp;#7sgP on 2015-04-10
Pop up message ' Error while copying to.... destination is read only'

---

### Post by Y^2om&amp;#7sgP on 2015-04-10
I should add, that if I do sudo thunar, then copying works.

---

### Post by coffeecat on 2015-04-10
> **hattpa]Pop up message ' Error while copying to.... destination is read only' [/quote]

[QUOTE=hattpa said:**
> I should add, that if I do sudo thunar, then copying works.

That is extremely odd since your partition has been mounted read-write by udisks for your UID and GID (presumably):

> ```
/dev/sdd1 on /media/phatton/Evolution-201503-64bit type vfat (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks2)
```

I'm puzzled. I've prefixed your thread Xubuntu in case this is something that other Xubuntu users have encountered.

In the meantime, please confirm your uid and gid by posting the output of:

```
id
```

---

### Post by Y^2om&amp;#7sgP on 2015-04-10
uid=1000(phatton) gid=1000(phatton) groups=1000(phatton),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),108(lpadmin),124(sambashare)

---

### Post by leunam12 on 2015-04-10
Have you tried```
sudo dosfsck -a /dev/sdx#
```Of course, x is the letter assigned to that drive and # is the partition number. Then pull the USB stick and re-insert it.

---

### Post by Y^2om&amp;#7sgP on 2015-04-10
same problem :(

---

### Post by matt_symes on 2015-04-10
Hi

Plug the USB stick in. Open a terminal and type

```
sudo hdparm -r /dev/sdd
```

Post the results back here. 

It's a long shot as you can write to the device using elevated privileges but worth checking.

Kind regards

---

### Post by Y^2om&amp;#7sgP on 2015-04-11
all it gives is

/dev/sdd:
 readonly      =  0 (off)

---

### Post by matt_symes on 2015-04-11
Hi

Plug the USB stick in.

What does this return ?

```
ls -l /media/phatton/Evolution-201503-64bit
```

Kind regards

---

### Post by Y^2om&amp;#7sgP on 2015-04-11
total 32
-rw-r--r-- 1 phatton phatton 29184 Apr 10 18:51 Mins Feb 2015.doc


the one file on the stick was copied on via a Windows PC :oops:

---

### Post by matt_symes on 2015-04-11
Hi

So far it all looks good.

Plug the device in and wait 10 seconds.

Open a terminal and type

```
dmesg | tail -n 20
```

Post that output back here.

After that type

```
touch /media/phatton/Evolution-201503-64bit/test.tmp
```

Does that last command return an error message or nothing at all ?

Kind regards

---

### Post by Y^2om&amp;#7sgP on 2015-04-11
[   45.141539] audit: type=1400 audit(1428732399.814:60): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=2235 comm="apparmor_parser"
[   45.141546] audit: type=1400 audit(1428732399.814:61): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2235 comm="apparmor_parser"
[   45.141826] audit: type=1400 audit(1428732399.814:62): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2235 comm="apparmor_parser"
[  332.021070] usb 1-1.2: new high-speed USB device number 5 using ehci-pci
[  332.248011] usb 1-1.2: New USB device found, idVendor=8564, idProduct=1000
[  332.248016] usb 1-1.2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  332.248018] usb 1-1.2: Product: Mass Storage Device
[  332.248020] usb 1-1.2: Manufacturer: JetFlash
[  332.248022] usb 1-1.2: SerialNumber: 44ZMPAHMI116HXYZ
[  332.248436] usb-storage 1-1.2:1.0: USB Mass Storage device detected
[  332.249130] scsi8 : usb-storage 1-1.2:1.0
[  333.709692] scsi 8:0:0:0: Direct-Access     JetFlash Transcend 16GB   1100 PQ: 0 ANSI: 0 CCS
[  333.710059] sd 8:0:0:0: Attached scsi generic sg4 type 0
[  333.710760] sd 8:0:0:0: [sdd] 31703040 512-byte logical blocks: (16.2 GB/15.1 GiB)
[  333.711834] sd 8:0:0:0: [sdd] Write Protect is off
[  333.711839] sd 8:0:0:0: [sdd] Mode Sense: 43 00 00 00
[  333.714532] sd 8:0:0:0: [sdd] No Caching mode page found
[  333.714537] sd 8:0:0:0: [sdd] Assuming drive cache: write through
[  333.719648]  sdd: sdd1
[  333.722847] sd 8:0:0:0: [sdd] Attached SCSI removable disk


The last command returns nothing...

---

### Post by coffeecat on 2015-04-11
Sorry to interrupt because matt_symes is doing some excellent detective work which I am following with interest! :) But I think I've found a relevant bug report:

[https://bugs.launchpad.net/ubuntu/+source/thunar/+bug/1332623](https://bugs.launchpad.net/ubuntu/+source/thunar/+bug/1332623)

@hattpa, you mention usb sticks in the plural in your OP, but you are testing with one stick only. Do you have other USB sticks to test?

---

### Post by Y^2om&amp;#7sgP on 2015-04-11
I have four sticks, but all are read only in the Xubuntu pc.  In a laptop running Arch and another windows PC, they're all fine

---

### Post by coffeecat on 2015-04-11
Going back to the touch command that matt_symes asked you to do, the fact that it returned no message suggests that it completed successfully. Have a look at the contents of the flash drive in Thunar. Is there an empty file called test.tmp? And/or re-run this command on that flash drive:

```
ls -l /media/phatton/Evolution-201503-64bit
```

---

### Post by Y^2om&amp;#7sgP on 2015-04-11
Err, not sure at what point this has happened....but

There is a file called test.tmp.  not only that but I can now copy files onto the stick, so really have no idea what’s going on???

I've also just ejected it, re-inserted and still works.  Also tried a different stick and that now works??

How??  Can anyone explain what has happened.  It hadn't worked for a couple of weeks and suddenly is??

At least it seems to be fixed.  Thanks guys for the help, although I have absolutely no idea what’s happened..:p

---

### Post by coffeecat on 2015-04-11
I'm glad it appears to be working, but I'd suggest delaying the celebrations until you can be sure that the problem doesn't recur.

Have another look at the bug I linked in an earlier post. In that bug the bug-reporter was able to write a file to a FAT32 partition from the terminal, but got the same error as you when using Thunar. The reason that the file test.tmp is now on the device is because you wrote it there with the touch command that matt-symes suggested. I'm convinced that you have experienced the same bug as the one reported on Launchpad. 

What is not explicable (just yet) is why you can now write to the USB device from Thunar. What I suggest is that you see what happens over the next hours/days. Don't mark this thread as solved, and if the problem recurs, post again with an update and we'll investigate further.

---

### Post by matt_symes on 2015-04-15
Hi

Nice catch with that bug report Coffeecat. I had not seen that one.

I would also suspect that the OP was suffering from that issue.

Kind regards

---

### Post by Y^2om&amp;#7sgP on 2015-05-16
Further to all of this.  USB sticks are still working, so that's all good.

But.... I've just inserted a sd reader with a card in, and get the message 'Mass storage device has been connected'

If I then try and access the card I get 'Failed to mount Mass Storage Device'

Anyone else with this issue?

Cheers

---

