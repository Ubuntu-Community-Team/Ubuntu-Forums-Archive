---
title: "Ubuntu 15.10 won't boot unless external USB drive is connected"
date: 2015-10-28
forum: General Help
---

### Post by FelixO on 2015-10-28
Hi,

I have a working installation of Ubuntu Gnome 15.10 x64.

I have an external USB drive (MyBook) that is connected all the time.
The system has been working correctly for a week, and *probably* booting correctly even when the external drive was turned off. (I can't say 100% whether I have booted it with the drive off before today).

In order to allow this drive to be accessed and mounted/unmounted by all users of the system I have added it to /etc/fstab.

/dev/sdc1 /media/MyBook ext4 rw,user,nosuid,nodev,relatime,data=ordered,uhelper=udisks2

molly@molly:~$ ls -l /media
total 12
drwxr-x---+ 2 root root 4096 Oct 18 11:30 charlotte
drwxr-x---+ 2 root root 4096 Oct 25 18:26 molly
drwx------ 8 molly molly 4096 Oct 25 18:44 MyBook

However, now if I turn the drive off and reboot the system Ubuntu doesn't start correctly.
I get the Ubuntu logo with the 'spinner' and then after a couple of minutes the emergency mode screen.
I have an external USB drive (MyBook) that is connected all the time.
The system has been working correctly for a week, and *probably* booting correctly even when the external drive was turned off. (I can't say 100% whether I have booted it with the drive off before today).

In order to allow this drive to be accessed and mounted/unmounted by all users of the system I have added it to /etc/fstab.

/dev/sdc1 /media/MyBook ext4 rw,user,nosuid,nodev,relatime,data=ordered,uhelper=udisks2

molly@molly:~$ ls -l /media
total 12
drwxr-x---+ 2 root root 4096 Oct 18 11:30 charlotte
drwxr-x---+ 2 root root 4096 Oct 25 18:26 molly
drwx------ 8 molly molly 4096 Oct 25 18:44 MyBook

However, now if I turn the drive off and reboot the system Ubuntu doesn't start correctly.
I get the Ubuntu logo with the 'spinner' and then after a couple of minutes the emergency mode screen.

I have the following sata devices:

/dev/sr0 DVD
/dev/sda Old250
/dev/sdb OS install disk with EFI,Boot,root,Home
/dev/sdc1 MyBook external USB hard disk

If /dev/sda is unplugged Ubuntu does not boot to UI - OS disk is mounted as /dev/sda instead
If /dev/sda is switched to a different (empty) hard disk Ubuntu boots properly.
If /dev/sdc is unplugged Ubuntu does not boot to UI - OS disk is at /dev/sdb as it should be, partitions are mounted, however X does not start.

---

### Post by FelixO on 2015-10-29
Thanks to Martin Pitt who responded to my bug report.

I need to use the option   noauto  in fstab otherwise the OS requires the disk be present in order to boot correctly.

---

