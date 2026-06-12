---
title: "mdadm help plz!"
date: 2008-04-26
forum: General Help
---

### Post by Sp0tteh on 2008-04-26
Hey all,

After putting together my new server and successfully installing ubuntu 8.04 all was fine.

I then went onto setting up mdadm creating a raid5 array with 3 hdd&#8217;s. This all completed successfully and was working fine.

Went to re-boot the system for the first time since installing mdadm and I&#8217;m confronted with the following:, then it enters a busybox shell


&#8220;Begin: Waiting for File System... ...
Done
Check root= bootarg cat /proc/cmdline
Or missing modules, devices: cat /proc/modules ls /dev
ARRAY /dev/md0 level=raid5 num-devices=3 UUID=d3caf6ce-046e-413e-3d48-292e4d2714f1
ALERT! /dev/disk/by-uuid/18f3b757-35ec-483c-a4af-5e61749e237b does not exist. Dropping to a shell

(initramfs):
"
Now from what I can tell its finding the array fine but having an issue finding my boot drive?

The boot drive is /dev/sda1, it&#8217;s an IDE drive and is NOT part of the array or any raid setup.

I have done the installation and setup of ubuntu and mdadm around 10 times last night but just can&#8217;t get anywhere with it. Even without setting up any arrays with mdadm, after you install it and then reboot the system it dies giving the same shell as above complaining about the missing uuid.

Hoping someone on here can assist in sorting this issue out. Thx!

I have attached a couple of files bellow: fstab, mdadm.conf, menu.lst

**Output of fstab**

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=18f3b757-35ec-483c-a4af-5e61749e237b /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda2
UUID=10a5b9a0-7f34-4b59-b8e4-9ebac76ac30f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

**Output of mdadm.conf**

# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
ARRAY /dev/md0 level=raid5 num-devices=3 UUID=d3caf6ce-046e-413e-3d48-292e4d2714f1

# This file was auto-generated on Sun, 27 Apr 2008 10:37:50 +0930
# by mkconf $Id$

**Output of menu.lst**

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=18f3b757-35ec-483c-a4af-5e61749e237b ro
initrd		/boot/initrd.img-2.6.24-16-generic

---

### Post by Sp0tteh on 2008-04-27
Just tried setting it up on ubuntu 7.10 and got the same issue. yet i had tested this a week ago with 3 x 40g drives and it worked fine, im using the same commands as before. The only diference is i was using IDE drives before and not SATA.

anyone got any ideas???? as im stuck :(

---

### Post by Sp0tteh on 2008-04-27
Well, i have finally got it going.

Yet i have no idea why, here is what i done over the last 2 days.

I was using a WD 40G IDE drive as the boot and root drive, this worked fine untill i restarted after installed mdadm and setup the raid5 array.

After hours of trying to work out what was going on i decided to just start from scratch, so i grabbed another 40GB drive and once again install ubuntu and mdadm. But for some reason even with the raided drives unplugged the mdadm.conf file was generated and had 2 UUID's for /dev/md0. I have no idea what happened there.

So i grabbed another machine and installed ubuntu and mdadm and on this other machine it all worked fine, so thought it must be the hdd's.

Finally i grabbed another different drive for the boot and install ,ubuntu and mdadm, assembled the previously created array and mounted. Edited the mdadm.conf file with the new correct UUID and added mounting info to fstab. Restarted and this time it didn't drop to a shell, booted fine into ubuntu.

So there it is, and yet i still don&#8217;t really have any real clue as to what caused the issue.

---

