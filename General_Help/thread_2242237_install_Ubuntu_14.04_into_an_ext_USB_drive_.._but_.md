---
title: "install Ubuntu 14.04 into an ext USB drive .. but retaining partition structure."
date: 2014-08-31
forum: General Help
---

### Post by dragonfly41 on 2014-08-31
It seems that I need a refresher course on installing Ubuntu 14.04 from USB flash. 
It may be that in previous installations I was installing into a blank external USB drive.  
But in this current situation I want to preserve a partition in the USB drive containing data.

I have Ubuntu 12.04 and Windows dual boot setup.

I'm now preparing to install Ubuntu 14.04 on an external USB drive which had an old Ubuntu 10.10 installed.
I purged three partitions in this USB drive ready for installation of Ubuntu 14.04 root, home and swap partitions (effectively replacing the purged old Ubuntu partitions).

I've prepared a Ubuntu 14.04 installer on a USB flash .. [http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-ubuntu](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-ubuntu) .. 
and booted into the installer (selecting USB in F12 BIOS at options reboot).

Following this workflow .. [http://www.linuxbsdos.com/2013/10/23/how-to-install-ubuntu-13-10-on-an-external-hard-drive/](http://www.linuxbsdos.com/2013/10/23/how-to-install-ubuntu-13-10-on-an-external-hard-drive/)
Ubuntu 14.04 prepared to install and progressed through the first few windows ..  


[LIST]
[*]First window .. Preparing to install Ubuntu
[*]Second window .. Installation type .. selected "something else" for manual installation
[*]Third window .. Advanced Partitioning Tool .. selected /dev/sdb device
[/LIST]

However this is where I hit a problem since I want to retain the existing partition structure in /dev/sdb which has data archived in /dev/sdb6 whilst other partitions I've purged out.

It seems that the Advanced Partitioning Tool in the USB installer expects to delete *all* the partitions in /dev/sdb and then create them again for a fresh installation of Ubuntu.   But I want to install in my external USB drive where one partition is still occupied with data.

/dev/sdb
    /dev/sdb1       ext4            target "/" partition
    /dev/sdb2       ext4            target "/home" partition
    /dev/sdb3       extended
        /dev/sdb5   linux-swap   target "swap" partition
        /dev/sdb6   ntfs            occupied with archived data


So my question is how do I force the installer to map "/", "/home" and "/swap" directly to these ready partitions: /dev/sdb1, /dev/sdb2, /dev/sdb5 ?

---

### Post by yancek on 2014-08-31
In the Installation type window, click in the main window to highlight sdb1 on which to install / then click the change tab below the window.  Select to format and select the filesystem type and select / as the mount point.  Repeat for home and swap.

---

### Post by dragonfly41 on 2014-08-31
Thanks. That got me through the partition installation to install Ubuntu 14.04.
I used the existing partition structure.
But when I rebooted I got this message:

error: file not found
grub rescue>

I don't know where I missed installing grub.
I'm sure that I selected /dev/sdb (not /dev/sdb1) for "device for bootloader installer".

I'm back in my usual PC with Ubuntu 12.04.
Inspecting /dev/sdb1 it has boot flag set.

I ran boot repair.  Output ..

[http://paste.ubuntu.com/8200384/](http://paste.ubuntu.com/8200384/)

So the dual boot grub still works .. but I need to add a grub menu for the external drive containing Ubuntu 14.04.

---

### Post by yancek on 2014-08-31
Your boot repair file shows Ubuntu 14.04 is installed on sdb1.  It shows syslinux bootloader installed to the mbr of /dev/sdb.
How do you get the error 'file not found' from grub, selecting which option?
Am I correct that you are able to boot Ubuntu 12.04 on sda6?  If that is the case, just run:  sudo update-grub  which should detect the new 14.04 install and put an entry in the menu.  If you can then boot to 14.04 you can install grub to the mbr of sdb with:  sudo grub-install /dev/sdb
You don't need to set a boot flag for sdb1 as that is only necessary with a windows system.  Since it is already set, no reason to change it as it does no harm.

---

### Post by dragonfly41 on 2014-09-01
I dug myself out of the hole I was in by reinstalling afresh and this time targeting /dev/sda (not /dev/sdb) for the installation of boot loader.

The three installations (Vista, Ubuntu 12.04 and Ubuntu 14.04 (ext)) now appear on the grub menu and I've booted into all three to check that they launch.

However the external USB Ubuntu 14.04 still has some problems in first running but I guess I should start new thread(s) for this stage. 
e.g. I can't install gnome-session-flashback.

I'll mark this thread as solved.  Thanks.

---

### Post by yancek on 2014-09-01
> However the external USB Ubuntu 14.04 still has some problems 

Welcome to the club.  I still have problems with the nvidia drivers and sometimes get a garbled screen on boot which doesn't happen on 12.04.  A new post for your problem is a good idea.  Good luck with it.

---

### Post by dragonfly41 on 2014-09-01
I added [SOLVED] too soon to this thread .. although I did succeed in installing Ubuntu 14.04 in two partitions in an external USB drive I later hit various problems and ended with Ubuntu 14.04 not booting after various restarts.

I saw message at booting USB in BIOS ...

error: no such device
a7d38dd2-c93-4d54-a605-e26492683c89
error: file not found
error: you need to load the kernel first

Back in my normal Ubuntu 12.04 (in my laptop) I checked the UUID of all partitions both internal and external and oddly none matched the device UUID above.

I then decided to install Ubuntu 14.04 into one of the empty partitions in my laptop and that installation has gone smoothly.   I was able to launch programs such as gnome-session-flashback which I could not do in the USB installation.

I don't know why I hit these problems with my external USB drive which has been used by older versions of Ubuntu.

I'm now focussing on tweaking Ubuntu 14.04 in the triple boot setup I have in my internal drive.

Vista
Ubuntu 12.04
Ubuntu 14.04

Unmarked thread as SOLVED since I have yet to solve the problem of the "error: no such device".   But that can wait for later.

I have to cleanup Grub to get rid of the unused Ubuntu 14.04 entry for the USB drive.

---

### Post by yancek on 2014-09-01
Boot into 12.04 on the internal drive with the external drive attached (the one with 14.04 on it) and open a terminal and run:  sudo update-grub
Watch the output.  It should detect 14.04 and create an entry for it.  When you installed 14.04, did you select to install grub to /dev/sdb (external drive mbr) or to its partition.  If you install it to /dev/sdb you will be able to select that drive in the BIOS and boot.  If you boot 14.04 on the external and run:  sudo update-grub, it should create a boot entry for 12.04 on the internal also.  There isn't any real need for this if the internal is booting both, just a safety precaution in case your internal fails.

---

### Post by dragonfly41 on 2014-09-02
Inspecting the grub menu when I boot up (internal HDD and USB modes via F12) I've spotted the problem with my external USB drive installation.

I installed the Ubuntu loader into a USB flash drive (using Startup Disk Creator) and then used that to install Ubuntu 14.04 onto the second plugged in USB drive (the target).   I noticed that during installation the target for installation was labelled /dev/sdc (not /dev/sdb) .. but when the USB flash drive was removed the USB drive containing Ubuntu 14.04 changed to be /dev/sdb.

So this must be why the external USB drive installation of Ubuntu 14.04 is not working and I'm getting the message "gave up waiting for root device".   I left the USB flash drive (installer) plugged in when I first tested the newly installed Ubuntu 14.04 and I then marked this thread as "Solved".

Then of course with the USB flash drive (installer) removed the grub menu device mapping is incorrect.

/dev/sdc becomes /dev/sdb

I now see from the link below that UUIDs are used to reference partitions. 
[http://ubuntuforums.org/showthread.php?t=1789603](http://ubuntuforums.org/showthread.php?t=1789603)

> 
You can just copy the relevant 'UUID="<number>" part from the terminal, and paste it over the device name in your /etc/fstab file.

For example, an output such as
Code:

$ sudo blkid
[sudo] password for vanadium: 
/dev/sda1: UUID="521cd407-2a4d-4ea8-a8e6-703d2370f2d0" TYPE="ext4"



From Ubuntu 12.04 I inspected /etc/fstab in the ext Ubuntu 14.04 file system which does not boot.  This shows the (now) incorrect mapping to /dev/sdc1 and /dev/sdc2 and /dev/sdc5:-

```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdc1 during installation
UUID=808e875e-d22d-4297-b0d5-6313237e5130 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdc2 during installation
UUID=3cab1cf8-f198-43a1-85fc-dfb081e6474c /home           ext4    defaults        0       2
# swap was on /dev/sdc5 during installation
UUID=3a7170bf-25dd-4934-b9cb-2eb3c94a5181 none            swap    sw              0       0


```

It might be helpful for the Ubuntu installer to be able to choose between device names and device UUID's.

Alternatively at install time how can I ensure that the USB flash device (installer) is named _after or below_ the target USB device name? i.e. the installer is /dev/sdc.   This might be a simple matter of USB port selection .. I don't know yet.

---

