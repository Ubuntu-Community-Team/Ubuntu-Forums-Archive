---
title: "Grub2 installed to main HDD"
date: 2020-03-20
forum: General Help
---

### Post by larryb1607 on 2020-03-20
I use a USB HDD to boot into an installed Linux distro.  My distro is based on Ubuntu 18.04.  When I do  not want to use Win 7, I shutdown and plug in the USB HDD.  No problems  until yesterday when I was logged in and checked for updates.  Some of  the updates had the word Grub in them which I know is the boot loader.


 If I did not have the USB HDD plugged in my PC would boot into Win  7.  Ever since this update, I now have to have the USB HDD plugged in  and select the partition that has Win 7 on it in order to get to  Windows.  If I do not have the USB HDD plugged, I get a blank screen  with a cursor in the upper left and have to shut down and insert the USB  HDD.
 This update also hosed my Linux install, but I can get into it by  booting into advanced options and choosing a different version to boot  into.

I would like to get this back to where my PC would boot into Windows and only boot into Linux if I have the External USB HDD plugged in.  I do not want the Grub interface when I boot up. 

I am a total noob when it comes to understanding what the terminal commands mean, so please keep it simple.

thanks

---

### Post by oldfred on 2020-03-20
If you have BIOS install and grub did a major update, it reinstalled grub.
And that could have been to internal drive, not external drive.
You can reinstall Windows boot loader to MBR of internal drive and reinstall (so grub update is correct) to external drive. Without reinstall grub may work or may give issue as something changed. You can try booting from external drive to test.

Often easier to use Boot-Repair and its advanced mode. That allows selection of system & drive to install boot loader. It normally is for Linux, but can install a Windows type BIOS boot loader to MBR. 
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

To avoid issue in future, you can change the default drive grub installs into with BIOS (does not work with UEFI).

#To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc # for BIOS with grub-pc 
It will show drive model & serial number
to see similar drive info
sudo lshw -C Disk -short 

sudo dpkg-reconfigure grub-pc 
#Enter thru first pages,tab to ok, spacebar to choose/unchoose drive, enter to accept, do not choose partitions
[http://ubuntuforums.org/showthread.php?t=2189643](http://ubuntuforums.org/showthread.php?t=2189643)

---

### Post by larryb1607 on 2020-03-20
Thought I posted a reply here, but does not seem to show up.  Anyway, thanks for the reply, it was a little too techy for me.  I was going to do a repair with a Windows CD, but found elsewhere where I could repair the MBR for Windows with Macrium Reflect and that worked.

---

