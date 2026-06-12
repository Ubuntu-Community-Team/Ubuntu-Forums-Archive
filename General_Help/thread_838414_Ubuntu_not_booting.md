---
title: "Ubuntu not booting"
date: 2008-06-23
forum: General Help
---

### Post by techdude300 on 2008-06-23
In order to fix this problem, I am including as much detail as possible. Thanks in advance for helping!

I am dual booting vista and ubuntu with these instructions:
[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm]("http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm")
usind EasyBCD

I recently worked on my hard drive partitions because I ran out of space on my Ubuntu partition. I have a Dell Inspiron 1501, which comes with the drive in two partitions. The first is the main Vista partition, and the secend is 10 GB for a recovery drive. I partitioned the second partition (I think that means i created an "extended" partition") that was about 5 GB for Ubuntu. I recently found, however, that this was not enough space as I would have liked.

Following the intructions at this site:
[http://ubuntuforums.org/showthread.php?t=35087]("http://ubuntuforums.org/showthread.php?t=35087")

I backed up my files to a .tgz file, and saved it to my hard drive (with vista on it). Everything went fine there. So my next task was to delete the backup and Ubuntu partitions and somehow merge them back together.

I booted into Vista to do this with disk management. I was able to make the recovey partition into unallocated space or whatever, and turned the Ubuntu partition into free space, but when I tried to delete the extended partition (now free space), it gave me an error saying that there wasn't enough space on the disk to do this. I had no idea how limited disk space could be related to deleting a partition, since y disk had plenty of space. I gave up and ended up restarting. After I booted into Vista, I found that I was able to delete the extended partition and had 10 GB of space to work with. I also noticed that I had a 87 MB partition that I couldn't delete.

I downloaded the latest .iso (alternate version - text installer) and I installed Ubuntu to the 10 GB space and created I think a "Logical drive?" (whichever didn't give me an error when I chose to make it bootable.) and used the 87 MB space as swap. So after the install Ubuntu works great, so I use the guide entioned above about backing up Ubuntu to restore all my files. The process is sucessful, and I tweak my toolbar to make it feel a bit more like vista.

After this I reboot, and attempt to boot into Vista, using the Grub bootloader. It tells me that the partition doesn't exist! Next I tried to boot into Ubuntu, and got the same error. I later found that the swap space was (hd0,0) which means the first Hard Drive, first partition. Vista was in (hd0,1) (first drive, second partition), and Ubuntu was in (hd0,2). So I pressed "e" to edit my setting so that vista booted (hd0,1). Then I went back and sucessfully booted into Vista. I then used EasyBCD to change my settings. When I rebooted, everything looked right. I had an entry for Vista and an entry for Ubuntu. But when I tried to boot into Ubuntu, the loading screen displayed, but it didn't load into Ubuntu. It displayed the little orange bar bouncing back and fourth. I waited and noting happened. I tried again, with the same result. The third time I used Ctrl+Alt+F1 to see what was going on. Here was about what I saw (There may be some typing errors):


  Booting command-list

root  (hd0,2)
 Filesystem type is ext2fs, partition type 0x83
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=bad383a0-5f0c-4b06-9680-0e4ee
56f5b1b ro quiet splash
    [Linux-bzImage, setup=0x2a00, size=0x1ce278]
intrid  /boot/intrid.img-2.6.24-16-generic
    [Linux-intrid @ 0x1f68d000, 0x78239f bytes]

[   43.288249] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[   43.344626] PCI: BIOS BUG #81{49435000] found
Loading, please wait...

	Check root= bootarg cat /proc/cmdline
	or missing modules, devices: cat /proc/modules ls /dev
ALERT! /dev/disk/by-uuid/bad383a0-5f0c-4b06-9680-0e4ee56f5b1b does not exist. Dr
opping to a shell!

BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)
(initramfs) _


If you have any questions, just ask. Thanks for reading!

---

### Post by Halfling Rogue on 2008-06-23
Man, I'm not sure. I've seen the hd(0,0) problem before, but not that particular booting problem. (Then again, I've heard plenty of horror stories about dual-booting Ubuntu and Vista, so I've made a point of never trying it.) Good luck! :(

---

### Post by rogier.de.groot on 2008-06-23
Looks like the kernel can't find a partition with the right UUID. Maybe the UUID in your GRUB config is wrong (this may have happened while restoring your backup, if you overwrote the whole filesystem?). During start-up, in the GRUB menu, you can choose to edit your settings; try removing the "root=UUID=xxxxx" part of the kernel line with "root=/dev/sdaX", where X is the number of your partition (I'd guess sda2 from your description, but you might need to try several variations).
Good luck!

---

### Post by techdude300 on 2008-06-23
I tried what you suggested, but unfortunately it didn't work. Though I did manage to get this:

 Booting command-list

root  (hd0,2)
 Filesystem type is ext2fs, partition type 0x83
kernel /boot/vmlinuz-2.6.24-18-generic root=/dev/sda2 ro quiet splash
	[Linux-bzImage, setup=0x2a00, size =0x1d25f8]
intrid  /boot/intrid.img-2.6.24-18-generic
	[Linux-intrid @ 0x1f8cd000, 0x722c4c bytes]

[   53.111496] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[   53.167633] PCI: BIOS BUG #81[49435000] found
Loading, please wait...
mount: Mounting /root/dev on /dev/.static/dev failed: No such file or directory
mount: Mounting /sys on /root/proc failed: No such file or directory
mount: Mounting /proc on /root/proc failed: No such file or durectory
Target filesystem doesn't have /sbin/init


BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) _

---

### Post by techdude300 on 2008-06-24
bump

---

### Post by rubicon on 2008-06-24
If I were you, I would consider reinstalling Ubuntu. AND - 87 mb for swap is absolutely not enough.

Let me just tell you how **I** would get out of this unpleasant situation, just to give you some directions. It's up to you to follow my guide or simply disregard it.

1. Boot up a LiveCD, backup my /home/user folder and anything else I'd want (like /usr/share/icons/ or /usr/src/, maybe even /etc/), but apparently not /boot/, /bin/, /initrd/, /sys/ and so on. Only data. Maybe using usb-drive or spare hdd.
2. Use some recovery CD with Partition Magic (name says it all), wipe Vista^W^W (whoops, can't help it :P ), edit partitions, merge that 87mb one with some other if possible. Let's assume recovery partition is somewhat of 10GB, so I just divide it to 9GB «/» and at least 1GB «swap» (though there is no need to do it now because ubuntu installer is capable of doing this kind of work, but if we started working with PartMagic, let's continue). So, I would have (/, 9GB) (swap, 1GB) (Vista, SomeGB) (Ubuntu home, SomeGB). Note that I would have separate partition for my home and data. If I'd ever need to reinstall Ubuntu, I would just format the first partition and all my settings and data on fourth partition wouldn't be touched in the process.
3. Boot up Ubuntu LiveCD, «Install», then at appropriate screen select partitioning scheme «Manual», pick FS type of ReiserFS or Ext2/3 and mount point of «/» for first partition, pick mount point of «swap» for second, leave third as it is (yuck), select Ext3 and «/home/» for fourth partition. GRUB should be installed on this drive, it will replace Vista's bootloader. We just should make sure it will hook all partitions and OSes right and fix it (possibly at a later time).
4. Wait until Ubuntu installed, boot into it, overwrite default settings and data with backed-up archive and get some coffee/beer to relax at last.

---

### Post by rogier.de.groot on 2008-06-24
Did you try any other variations for sdaX ? (e.g. sda1, sda3, etc)
Rubicon is right about the swap space being a little tight too; I run both Vista and Ubuntu on my laptop, the Ubuntu partition is quite small, I store all data files on the Vista partition anyway.
Reinstalling might be the best option.

---

