---
title: "[SOLVED] Make LiveUSB partition read-only when mounted by external OS"
date: 2008-05-28
forum: General Help
---

### Post by drewster1829 on 2008-05-28
I used [this tutorial]("http://www.pendrivelinux.com/2008/05/15/usb-ubuntu-804-persistent-install-from-linux/") to make a persistent Ubuntu 8.04 LiveUSB using a SanDisk 4GB Cruzer.  It results in two partitions.  The first is FAT16, 750 MB, containing the files off of the LiveCD (labeled ubuntu8 ).  The second is ext2, and is empty (labeled casper-rw).

This tutorial works fine (except for some **minor problems: see last paragraph**), except that when I plugged it into a running Windows XP machine, it must've wrote some files to the ubuntu8 partition and corrupted it, because it wouldn't boot after that.  Actually, I'm not exactly sure if that's what happened, but after I plugged it into a running XP machine, it would freeze when trying to start X, giving me a blank screen with a working mouse cursor, and nothing else (couldn't switch to the terminal, either), and I ended up having to recopy all the files onto the ubuntu8 partition (which subsequently fixed it).

What I want to know is: is there a way to make the ubuntu8 (FAT16, 750MB) partition read-only when it's mounted by an external file system, but still read-write when I boot from the USB pen drive in persistent mode?  Also handy would be an easy way to change it to read-write if I mount it with my Ubuntu machine(s), in case I want to edit something using an external OS, like if I messed up the OS on the pen drive again, and it wouldn't boot.  The latter would be a luxury, so it's totally optional. I'm more concerned about making it read-only when mounted by MS Windows. I would like the casper-rw partition to be read-write, always.

Now, for the problems I had with the above tutorial.  Following it to the 'T', when I first tried to boot it, I got "Couldn't find kernel: /casper/.vml".  For some reason, it truncates the filename length.  The solution is to copy or move vmlinuz from the /casper folder to root (and make sure initrd.gz is also in the root folder), and then go through and edit /syslinux.cfg.  It's easiest to do a find and replace, finding "/casper/vmlinuz" and replacing it with "vmlinuz" (*no slash!* it won't work otherwise).  You may also have to get rid of the slash ahead of initrd.gz wherever it appears (I had to).  That *should* fix it.  Anyway, thanks for your help in advance!

EDIT: Okay, I tried to do it with three partitions, sdb1 being an empty FAT32 partition, sdb2 is the 750 MB Live CD files (ubuntu8), and sdb3 is the casper-rw partition.  I figured since Windows only mounts the first partition, this would allow me to use it as a regular pen drive OR as a persistent Ubuntu LiveUSB pen drive.

However, I can't get it to boot.  I used "syslinux -sf /dev/sdb2", but at boot all I get is "Missing operating system".  The boot flag is set on /dev/sdb2 (I forgot that initially, then fixed it, but it didn't help).  I'm sure it's something obvious, so I'll keep messing around with it.  If anyone has any ideas in the meantime, please let me know. Thanks!

---

