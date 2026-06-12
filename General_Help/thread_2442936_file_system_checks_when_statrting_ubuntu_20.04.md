---
title: "file system checks when statrting ubuntu 20.04"
date: 2020-05-09
forum: General Help
---

### Post by glenno02 on 2020-05-09
I recent installed a clean copy of ubuntu 20.04 from a created usb drive on my laptop. I t worked fine for sevral days  however, upon booting up the last few times I am noticing some different some writing " press ctrl + c  to cancel file system check" and  other menus asking to run advanced test etc and it slowed down the boot process considerably. What ar these, what do they mean and how to fix.

---

### Post by CelticWarrior on 2020-05-09
Welcome.

File systems checks are done periodically, that's normal.
If you let it finish, do your things in the OS as usual and then shutdown properly, does it happen again in the next boot? If so it suggests something is wrong with the partition/drive.

---

### Post by TheFu on 2020-05-09
If you allow the OS to shutdown completely, then file system checks should only happen at most every 7-90 reboots unless someone went out of their way to specifically ask for that to happen more often.  It is a file system tuning parameter on normal file systems.

Have you rebooted 7 times in a day?

If you are using either ZFS or BTRFS, I cannot help. They work differently.

But if the file systems are not properly closed as part of shutdown/reboot, then that will force the fsck process.

---

### Post by kneutron on 2020-06-06
--If you are using a "cheap" USB thumbdrive, it may be going bad.  Make sure you set 'noatime' on all filesystems in /etc/fstab and copy your data off to another drive.

--For better reliability, I recommend getting a USB3 external SSD.  I boot my Ubuntu 20.04 ZFS boot/root laptop off a Samsung T5 500GB and they're below $90 now on Amzn.  There are other external SSDs out there that are smaller-size and less expensive, but I can say the T5 is very reliable so far, I have several.  And beware - some of the odd-named brands tend to disappear so you can't buy more.  Do some research and look for reliable brand-name manufacturers, and read the reviews.

---

