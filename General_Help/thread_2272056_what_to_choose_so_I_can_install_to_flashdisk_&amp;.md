---
title: "what to choose so I can install to flashdisk &amp; enables it to rollback to original sta"
date: 2015-04-03
forum: General Help
---

### Post by newbie14 on 2015-04-03
At the "create partition" menu, when I want to install ubuntu 12.10; What options should I choose so I can install to flash-disk properly and enables me to uninstall / reverted / rollback my USB flash-disk to its original state? One day if the need arise? These was what I did:

step 0: I use 2 flash-disks; the 16 GB for the initial bootable ubuntu installer [**[photo]**]("http://i.imgur.com/NcKYxuF.jpg"). And the 32 GB for the installation media [**[photo]**]("http://i.imgur.com/rVewmnx.jpg").
step 1: I am using rufus at windows computer to create a 16 GB bootable usb-flash-disk. Using the ubuntu-12.10-desktop-i386.iso as boot image. This is the photo: [B][[Photo 1]("http://i.imgur.com/BxonPnl.png")],.... [[Photo 2]]("http://i.imgur.com/YSPbkhy.png").
[/B]step 2: **[[photo]]("http://i.imgur.com/gdDojCP.jpg")** I plugged in the 16 GB flash-disk first.
step 3: I switched on my computer.
step 4: I press the F12 button on my keyboard, immediately
step 5: a "select boot first device" menu appeared, and I chosen the "USB-ZIP" option.
step 6: [**[photo]**]("http://i.imgur.com/PD8Lk2M.jpg") at the welcome menu, I selected "install" option.
step 6a: [**[photo]**]("http://i.imgur.com/i5ARTnC.jpg") I plugged in the 32 GB flash-disk.
step 7: [**[photo]**]("http://i.imgur.com/4mIkhzi.jpg") I have chosen "something else".
step 8: [**[photo]**]("http://i.imgur.com/h6pi8fA.jpg") I highlighted my 32 GB flash-disk.
step 9: [**[photo]**]("http://i.imgur.com/QQ8bTfX.jpg") I clicked the plus button.
step 10: [**[photo1]**]("http://i.imgur.com/Cu5CzDw.jpg")....[**[photo2]**]("http://i.imgur.com/3FsIsFJ.jpg") I was presented with many options of creating a partition.

considering that the 32 GB usb flash-disk installation media must be able to be rolled back / reverted to its original state one day if the need arise;
My questions are:
1. what options should I choose? primary? logical? beginning of this space? end of this space?
2. what should I "use as"? Ext4? Ext3? Ext2? journaling file system? fat16? fat32?
3. what "mount point" should I choose? "/"? "/home"? "/temp"?

---

### Post by oldfred on 2015-04-03
Your 12.10 is obsolete and not supported anymore.
Use 12.04 or 14.04 which are long term support versions or 14.10.
       Please see this sticky thread in the Installation subforum.
Forums Staff recommendations on EOL Ubuntu releases, in particular 10.04 desktop.
[http://ubuntuforums.org/showthread.php?t=2229730](http://ubuntuforums.org/showthread.php?t=2229730)

Ubuntu does not have a roll back. Best just to have good backups to restore from.

      
 Lots of detail, screenshots and essential info.14.04  Something Else example
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)
[http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation)
[http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using](http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using)

   Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)

 [https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

---

### Post by Impavidus on 2015-04-04
12.10 is old and has several known bugs/security holes which are not going to be fixed. That's what we mean by no longer supported. 12.04 LTS is even older, but still gets critical bug fixes (LTS=long term support). 14.04 LTS or 14.10 are the releases I recommend. If you don't want to upgrade or reinstall every 6 months, pick 14.04. The installation process is the same on all, except that not all live disk creation tools work equally well on all releases.

Your steps 0–9 are OK. If by uninstall/revert/rollback your usb flash disk to the original state you mean removing Ubuntu and using it again as a portable data drive, you can just reformat the drive. Of course, when you have done so, the drive will be empty.

When you only use about 30GB, it's best to use a single partition for everything. The only question is whether you want a swap partition (comparable to virtual memory in Windows). Usb drives are slow and will quickly wear if you use swap on them, so if you have plenty of memory (RAM, say about 4GB) it may be better not to use any swap.

So that is one primary (doesn't really matter though) ext4 partition, mount point /, at the beginning of the drive (doesn't really matter though), taking almost the entire drive, and (if you wish) a swap area (primary or logical, doesn't really matter), about 2GB, at the end of the drive. Everybody has his own ideas on partitioning, so don't be surprised when you see some conflicting posts below.

More importantly, choose /dev/sdc as the device for boot loader installation, or your computer will be unbootable when the usb drive is not attached.

---

### Post by newbie14 on 2015-04-04
Thank you. Nice & direct technical answer, just exactly what I need. I will try choose single partition, not use any swap, ext4 file system, at the beginning of the drive, primary.

---

