---
title: "Bootable &amp; usable usb stick"
date: 2013-02-26
forum: General Help
---

### Post by ksaul on 2013-02-26
I picked up a couple 64gb USB thumb drive/stick today at BestBuy and was wondering if it is possible to reformat, and partition the USB stick to become a bootable, and usable (Read & Writable) Ubuntu environment?

Example: Laptop has Windows 7 installed, I insert the USB stick (before booting), boot off the USB stick and instead of using Windows 7, Ubuntu is booted instead, and any work done in that Ubuntu session is then saved on the thumb drive.

This would be awesome if it can work

---

### Post by oldfred on 2013-02-26
I have a 16GB flash drive with a full install of Ubuntu in 8GB and 8GB for data. It is not real speedy as writes are slow and USB ports are slower than hard drive. I just got a new USB3 flash drive that is supposed to be a bit faster even with my USB2 ports. You do want to make some settings to reduce writes to help performance. If you have a fair amount of RAM once data is loaded it is just as fast as data is in RAM.

       Pros & cons of persistent install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

       Full install - C.S.Cameron post #2
[http://ubuntuforums.org/showthread.php?t=2116798](http://ubuntuforums.org/showthread.php?t=2116798)
Full install of 12.04 to 64GB USB device C.S.Cameron post #3
[http://ubuntuforums.org/showthread.php?t=2092077](http://ubuntuforums.org/showthread.php?t=2092077)

If you want to be able to read or write some data from Windows you have to make first partition NTFS as Windows only sees first partition.

It really is just like any install to another drive. You do want to use manual install or Something Else so you get the option (during partition stage) to choose where to install the grub2 boot loader. You want grub in the MBR of the flash drive, otherwise it defaults to sda which usually is your hard drive.

       Install to external drive. Also any second drive.
Installer version has not changed much so still a good guide except I do not recommend the separate /boot for most systems. Older systems may need it. And some with very large / (root) partitions. BIOS/MBR not for UEFI
[http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/](http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail - now alternative (text based) installer
Different versions have slight difference in install screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)

       With SSD or Flash drives, Use ext4 without journal:
sudo tune2fs -O ^has_journal /dev/sda1
sudo tune2fs -o discard /dev/sda1
No swap or set swapiness or install 'Dynamic Swap Space Manager' from the Ubuntu Software Center
After installing, change the fstab so that everything gets mounted with noatime.
Make sure BIOS is in AHCI mode for trim to work. (Trim not for flash drives)
change to noop i/o scheduler

---

### Post by ksaul on 2013-02-26
awesome information.. THANK YOU! Very exciting to take Ubuntu everywhere with me :)

I will only be using basic things (firefox, emacs, terminal) so not worried about speed to much.

---

### Post by ksaul on 2013-02-26
> **oldfred said:**
> 

It really is just like any install to another drive. You do want to use manual install or Something Else so you get the option (during partition stage) to choose where to install the grub2 boot loader. You want grub in the MBR of the flash drive, otherwise it defaults to sda which usually is your hard drive.

I am about to delete the partition table pre-installed on the 64bit stick now, should I wait to format/partition it up again til I am ready to install ubuntu?

Also, I should probably install a 32bit version, not 64bit for compatibility - right?

---

### Post by ksaul on 2013-02-26
How should I setup my USB stick to be ready for Ubuntu 12.10 32bit? 

Whats the best partition setup? (I do not need read/write access between NTFS and Ubuntu)

---

### Post by oldfred on 2013-02-26
Even on my hard drives I do not like more than 25GB for / (root) and then I store data in other partitions. You only need 10 to 20GB for / if you set it up to mount the data partition and store data there.

Unless you have old computers, the 64 bit still works. My laptop is 6 years old with 1.5GB of RAM and I boot it with flash drive and currently 12.04.2 64 bit. More just for test installs as it does not have a lot of room on hard drive.

I usually partition in advance, but the current install version when using manual install lets you do just about everything you would want.

I also wanted to learn about gpt partitioning so I used gpt for my flash drive. Once installed I do not even see any difference.

---

