---
title: "17:10: NTFS partition auto-mounts as read-only"
date: 2017-11-10
forum: General Help
---

### Post by The Bright Side on 2017-11-10
Hey guys! Since my switch from 17.04 to 17.10, I can no longer write stuff to my Windows partition from Ubuntu. It auto-mounts during startup at /media/thebrightside/ (my user name), which I think is the same location as the last 8 years I've used Ubuntu.

Mind you, I reinstalled my entire system - Windows 10 and Ubuntu 17.10 - from scratch when 17.10 came out, since I had just gotten my PC repaired. I looked the problem up online and ruled out the following possible reasons for my issue:

[LIST]
[*]Fast Boot - it's disabled in my BIOS
[*]ntfs-3g - it's already installed
[/LIST]

*ls -l /media* tells me:

> total 8
drwx------  6 thebrightside thebrightside 4096 Sep 15  2016 2NDHDD
drwxr-x---+ 3 root          root          4096 Nov 10 08:53 thebrightside

I'm suspecting it has something to do with my "thebrightside" folder being owned by root, not me. When I try *chown -R*, I get a long string of variations of this:

> chown: changing ownership of '/media/thebrightside/WINDOWS': Read-only file system

Looking at my fstab, I see that the WINDOWS partition does not appear in it:

> # /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda5 during installation
UUID=5cac86ef-9735-4522-a2d9-50e4be3b0844 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda2 during installation
UUID=44CE-D40B  /boot/efi       vfat    umask=0077      0       1
# /home was on /dev/sdc1 during installation
UUID=c7f5d936-04d9-4224-98dd-e611cd370f63 /home           ext4    defaults        0       2
# /media/2NDHDD was on /dev/sdb1 during installation
UUID=67a4faa3-4245-469a-a602-965588121ebc /media/2NDHDD ext4    defaults        0       2
/swapfile                                 none            swap    sw              0       0

This is where I'm stuck. Where would I go from here to make my WINDOWS partition writeable?

Thanks!

---

### Post by oldfred on 2017-11-10
With Windows 10 did you turn off its fast start up which is always on hibernation. All NTFS partitions are then hibernated & the Linux NTFS driver will not mount read/write. It used to not mount at all and give error message.

 Fast Start up off (always on hibernation), different than UEFI fast boot
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

---

### Post by The Bright Side on 2017-11-10
Ahhhh, that did it! Also got an extra 13 GB from disabling hibernate altogether. Can't believe I overlooked this when I installed Windows. *powercfg /hibernate off* is usually one of the first things I do. o.O

Thanks for helping!

---

