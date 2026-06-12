---
title: "Unable to boot ubuntu 10.04, no init found."
date: 2014-08-30
forum: General Help
---

### Post by adayoegi on 2014-08-30
Hello guys,

I installed my ubuntu 10.04 on VMWARE in my win7-64bit laptop.

4 hours ago I slept my ubuntu and win7, taking my laptop to school. However, when they are turned on again, the ubuntu failed to boot up and shows the following message:

====
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init.
No init found. Try passing init= bootarg.


BusyBox v1.13.3 (Ubuntu 1:1.13.31ubuntu11) built-in shell (ash)
Enter 'help for a list of built-in commans.

(initramfs)
====

I have searched for some topics this morning but their solutions do not work in my case. 
For example, in [http://ubuntuforums.org/showthread.php?t=1561735](http://ubuntuforums.org/showthread.php?t=1561735)
It says entering "ls" will get [COLOR=#000000] something like "vmlinuz" and "initrd", however, the only thing [/COLOR] I have is 
====
grub> ls
(hd0) (hd0,6) (hd0,5) (hd0,1) (fd0)
grub> ls (hd0)
Device hd0: Partition table
grub> ls (hd0,6)
          Partition hd0,6: Unknown filesystem
grub> ls (hd0,5)
          Partition hd0,5: Filesystem type ext2 - Last modification time 2014-08-28 13:43:03 Thursday, UUID 206680fe-8241-........4c
grub> ls (hd0,1)
          Partition hd0,1: Filesystem type ntfs, UUID 14E....0E
grub> ls (fd0)
Device fd0: Filesystem cannot be accessed
error: mo such disk
====
There is nothing [COLOR=#000000]like "vmlinuz" and "initrd".
In other topics, they usually need to know the main drive, but I do not know where to get the information.

In the end, if anyone could help me with this problem and get my ubuntu works, it would be really appreciative.[/COLOR]

---

### Post by yancek on 2014-08-30
The kernel (vmlinuz) and initrd should be in the boot directory so:  ls /boot should show it.

If you are actually using 10.04, it is an unsupported version.  If you hibernate and not do a full shutdown, this might be the problem also.  I'm basing that on what I've read in other posts as I don't use hibernation.  Simple enough to shut down windows totally and reboot to try.

---

### Post by adayoegi on 2014-08-30
Hi, thanks for your reply.
As I used ls /boot, it shows:
====
(initramfs) ls
dev sbin conf lib etc proc var
root scripts init bin sys tmp
(initramfs) ls /boot
ls: /boot: No such file or directory
(initramfs) ls/boot
/bin/sh: ls/boot: not found
(initramfs) ls/root
/bin/sh: ls/root: not found
(initramfs) ls /root
(initramfs) ls 
dev sbin conf lib etc proc var
root scripts init bin sys tmp
====
It seems nothing happening.
I used to hibernate my windows very often, but I now know it is not wise to do so on ubuntu.
Rebooting my windows does not work for this.

---

### Post by dragonfly41 on 2014-08-30
I had this same error when trying to bootup an old USB drive containing Ubuntu 10.10 with the intention of installing fresh Ubuntu 14.04.   

The external USB drive was /dev/sdb1.

I had to apply these commands 

sudo fdisk -l
sudo fsck.ext4 -f /dev/sdb1

clicking through all fsck errors with "yes".

then I rebooted external USB and all was well.

...

[p.s.] I see that your file format is ext2 so you will have to amend the above which works on ext4.

---

### Post by yancek on 2014-08-30
Just to clarify, your Ubuntu install is in virtual software (VMWARE) in your windows 7 partition not on a partition of its own?
Is there any particular reason why you are using 10.04 as it hasn't been supported for over a year or is that a typo?

---

