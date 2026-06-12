---
title: "Use All 32GB On USB For Persistence File"
date: 2014-04-11
forum: General Help
---

### Post by zane99 on 2014-04-11
Is there any way to get my USB to use all the memory instead of the ~4000mb that Universal USB Installer uses?
I'm running low on memory even though I've only used 4GB.

---

### Post by oldfred on 2014-04-11
If you want that much space, probably better to do a full install.
I have full install on my 16GB flash using 8GB for / and 8 GB for data, but that is more as an emergency boot not daily use. Only 8GB for / is a little small but workable as long as I houseclean regularly.

       Pros & cons of persistence install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=2133067](http://ubuntuforums.org/showthread.php?t=2133067)
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

    
 Large persistent - C.S.Cameron post 6 & 7
[http://ubuntuforums.org/showthread.php?t=2041679](http://ubuntuforums.org/showthread.php?t=2041679)

---

### Post by zane99 on 2014-04-11
If I do a full install on my 32GB USB will I be able to boot from any computer without overwriting the OS on the HDD.
Last time I chose "Install Ubuntu" from the boot menu I overwrote Windows 8.1

---

### Post by XBNCPRk on 2014-04-11
LinuxLive creator will allow you to set the size of the USB used for persistence, from 0 all the way up to the entirety of the drive. 

Alternatively, Id think you should be able to use gparted or windows disk manager to change the size of the partition on the usb drive to expand it from 4gb to 32.

Also, the size of the partition on the persistent live usb has nothing to do with the size of the install on a hard drive. The persistence just means that there will be the standard user folders and settings included on the usb. Otherwise it functions basically the same as an install cd/dvd, where you can boot and run, but none of your settings or files last from boot to boot. 

If you want to be able to boot from the persistent usb drive, and not overwrite whatever is on the computer already, do NOT click install ubuntu. It overwrote it because thats what you told it to do. Click try ubuntu and it will run from the usb.

---

### Post by oldfred on 2014-04-11
If you install to anything that is not the single internal drive, it is best to use Something Else or manual install.
You do have to choose partitions, mount points like / or /home, formats like ext4, but it is the only choice that lets you choose to install the grub2 boot loader to another drive than the normal default of sda.

 Install to external drive. Also any second drive.
And you want this screen to choose where to install the grub2 boot loader which is only available with Something Else or manual install
[https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29](https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29):
Installer version has not changed much so still a good guide except I do not recommend the separate /boot for most systems. Older systems may need it. And some with very large / (root) partitions. BIOS/MBR not for UEFI
[http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/](http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/)



This still shows default of drive that is sda, but as a combo box lets me choose if I want anther drive. I am installing to an existing partition on sdc that had an old test install.

---

