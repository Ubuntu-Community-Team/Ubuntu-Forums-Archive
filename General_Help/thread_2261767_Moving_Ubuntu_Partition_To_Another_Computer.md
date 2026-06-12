---
title: "Moving Ubuntu Partition To Another Computer"
date: 2015-01-20
forum: General Help
---

### Post by byrondallas on 2015-01-20
I'm dual booting Ubuntu 14.04 32bit with Windows XP on an old laptop and really like the way I have Ubuntu setup and would hate to have to start all over with a new install. What I would like to do is move the Ubuntu partition to my Windows 7 64bit machine which is ONLY running Windows 7 at this time. Is it possible to make an image of the Ubuntu partition only, using Clonezilla, and then make a partition on my Windows 7 laptop with the exact same amount of space and install the image there, again using Clonezilla? Or would I have to start all over again since the Windows 7 is 64bit. And if starting over with a Ubuntu 14.04 64bit is my only choice, is there a way to move my programs and settings from the XP machine?

---

### Post by yancek on 2015-01-20
You can clone your Ubuntu partition and move it to another drive.  Some possible problems would be that you would need to install the Ubuntu Grub2 bootloader as it is very difficult to get windows to boot any Linux, particularly without third party software.  If you have proprietary drivers a different hardware for things like the graphics card, you would need to configure that.  The UUIDs would be different on the new machine so you would probably need to modify the /etc/fstab file.

---

### Post by kevdog on 2015-01-21
It's totally possible to do this.  In fact creating the partitions on the winxp side and moving the data over is very easy. You could go Clonezilla, but it would be easier if you could like plug in your hard drive to lets say the USB port on the machine and directly move data over using a dd command or something.

The bootloader is definitely the tricky part, meaning your going to have to use grub to boot and chainloader within grub unless windows is your first command.  The real difficult part however if dealing with UEFI if your system has that.  I've never worked with that before although the process has been well described by many, but its often a cause of concern and problems for many.

---

### Post by Mark Phelps on 2015-01-21
> and install the image there, again using Clonezilla? 

I'd be very careful with doing this -- for several reasons:

First, be sure to use ONLY the Win7 Disk Management utility to shrink the Win7 OS partition to make room for Ubuntu.  Do NOT use the Installer with the slider to do the shrinkage as this risks corrupting the Win7 filesystem, rendering it unbootable, and making it really hard to fix.

Second, BEFORE you do this, use the Backup feature in Win7 to create and burn a Win7 Repair CD.  You might need this later to repair the Win7 boot loader if the dual-boot setup goes badly.

Third, using the Win7 Disk Management utility, count the number of partitions already on the drive.  IF you have four, that is the maximum allowed and you can't simply create another for Ubuntu. If you do this using the Disk Management utility, it will automatically convert ALL your partitions to Dynamic Disks -- something you do NOT want.

Fourth, when you back up a partition using Clonezilla, it restores it to the same location on a drive; meaning, if it's partition #1 on your source volume, when you restore it to the Win7 drive, it will overwrite partition #1 on that drive.  What I would look into is RedoBackup.  It has a GUI interface and it might allow you to "drag and drop" the backup to an open location on the Win7 drive.

---

### Post by C.S.Cameron on 2015-01-21
I understand that Ubuntu 32 bit does not work in a UEFI system, 64 bit is required.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

But I think you are ok if the machine came with Windows 7 and not 8.

---

### Post by byrondallas on 2015-01-21
Thanks guys. Yeah I forgot about the boot loader. Sounds like I could run into some difficulties. Let's say I go ahead and just burn a new copy of the 14.04 64 bit and install it that way. Is there an easy way to move my settings and programs from the Windows XP machine?

---

### Post by oldfred on 2015-01-21
My backup is just to be able to reinstall. All your user settings are in /home, so copy that. And if you made some system wide settings like grub, Network, or other they are in /etc, so back that up, but you may not want to just restore that if a newer version. Settings may be slightly different.

If you have separate /home you can copy that to a new partition, if not copy it back into your new install.

       Oldfred's list of stuff to backup May 2011 (still mostly current, see added links):
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)
Some files(temp, cache etc) to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)

My backup includes this also. The dpkg list is a very long text list of all applications and the dependencies. You may want to edit it to remove obsolete, old kernels or others. It will not re-install anything already installed.

 from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
From old install
dpkg --get-selections > ~/my-packages
From New install
sudo dpkg --set-selections < my-packages
sudo apt-get -y update
sudo apt-get dselect-upgrade

And I do not fully backup /etc, but anytime I manually edit a file like grub or 40_custom, I copy it into a folder in /home, so my normal backup of /home includes it.

---

### Post by byrondallas on 2015-01-21
Thanks oldfred!

---

