---
title: "Getting 13.04 to run on a USB stick."
date: 2013-06-10
forum: General Help
---

### Post by at2smithjason on 2013-06-10
I am trying to get 13.04 to run from a virtual box off of my 16 GB kingston USB stick.  I was trying to do a full install on it so that I could use virtual box (I used the LiLi live USB tool to create the live usb).  Every time I tried to do a full install, it didnt recognize my usb.  I was using the presistance file on it, and I read that it wouldnt work for a full install.  So I reformatted in the FAT32 and tried again without the persistance.  Still no luck.  Is there something that I am doing wrong?  I dont want to have to keep using the live function.  I would liek to be able to just plug in and go when ever I want to from anywhere I want to.  I did a little google searching and searched around on previous posts seemed to be people just asking how to do it.  Nothing with an issue like mine.  Do I need to go down to the last version?

---

### Post by jim_deadlock on 2013-06-10
You have to install uck and then you can do a proper full installation onto a USB stick. You need at least a 8Gb stick, preferably 16Gb. Mine is a tight squeeze on 8Gb with a few games installed.

---

### Post by C.S.Cameron on 2013-06-10
Following is step by step for installing 12.04 on a 8GB flash drive on an Intel machine.
13.04 is similar except "add" = "+"

Turn off and unplug the computer. (See note at bottom)
Remove the side from the case.
Unplug the power cable from the hard drive.
Plug the computer back in.
Insert the flash drive.
Insert the Live CD or Live USB.
Start the computer, the CD/USB should boot.
Select language
Select install Ubuntu.
Select Download updates while installing and Select Install this third-party software.
Continue
At "Installation type" select "Something else".
Continue
Confirm Device is correct.
Select "New Partition Table" 
Click Continue on the drop down.

(Optional partition for use on Windows machine)
Click "Free space" and "Add".
Select "Primary".
Make "New partition size..." about 1000 megabytes.
Location = Beginning.
"Use as:" = "FAT32 file system".
And "Mount point" = /windows.
Select "OK"

Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 4000 to 6000 megabytes, Beginning, Ext4, and Mount point = "/" then OK.

(Optional home partition)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 1000 to 4000 megabytes, Beginning, Ext2, and Mount point = "/home" then OK.

(Optional swap space, allows hibernation)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = remaining space, (1000 to 2000 megabytes, or same size as RAM), Beginning and "Use as" = "swap area" then OK.

(Important)
Confirm "Device for boot loader installation" points to the USB drive. Default should be ok if HDD was unplugged.

Click "Install Now".
Select your location.
Continue.
Select Keyboard layout.
Continue.
Insert your name, username, password, computer name and select if you want to log in automatically or require a password.
Selecting "Encrypt my home folder" is a good option if you are worried about loosing your USB drive.
Select Continue.

Wait until install is complete.
Turn off computer and plug in the HDD.
Stick the side panel back on.

Note:
You may omit disabling the hard drive if, when partitioning you choose to install grub to the root of the usb drive you are installing Ubuntu to, (ie sdb not sdb1). Be cautious, many people have overwritten the HDD MBR.
You can revise grub later, if you wish.

---

### Post by C.S.Cameron on 2013-06-10
Following is step by step for installing 12.04 on a 8GB flash drive on an Intel machine.
13.04 is similar except "add" = "+"

Turn off and unplug the computer. (See note at bottom)
Remove the side from the case.
Unplug the power cable from the hard drive.
Plug the computer back in.
Insert the flash drive.
Insert the Live CD or Live USB.
Start the computer, the CD/USB should boot.
Select language
Select install Ubuntu.
Select Download updates while installing and Select Install this third-party software.
Continue
At "Installation type" select "Something else".
Continue
Confirm Device is correct.
Select "New Partition Table" 
Click Continue on the drop down.

(Optional partition for use on Windows machine)
Click "Free space" and "Add".
Select "Primary".
Make "New partition size..." about 1000 megabytes.
Location = Beginning.
"Use as:" = "FAT32 file system".
And "Mount point" = /windows.
Select "OK"

Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 4000 to 6000 megabytes, Beginning, Ext4, and Mount point = "/" then OK.

(Optional home partition)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 1000 to 4000 megabytes, Beginning, Ext2, and Mount point = "/home" then OK.

(Optional swap space, allows hibernation)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = remaining space, (1000 to 2000 megabytes, or same size as RAM), Beginning and "Use as" = "swap area" then OK.

(Important)
Confirm "Device for boot loader installation" points to the USB drive. Default should be ok if HDD was unplugged.

Click "Install Now".
Select your location.
Continue.
Select Keyboard layout.
Continue.
Insert your name, username, password, computer name and select if you want to log in automatically or require a password.
Selecting "Encrypt my home folder" is a good option if you are worried about loosing your USB drive.
Select Continue.

Wait until install is complete.
Turn off computer and plug in the HDD.
Stick the side panel back on.

Note:
You may omit disabling the hard drive if, when partitioning you choose to install grub to the root of the usb drive you are installing Ubuntu to, (ie sdb not sdb1). Be cautious, many people have overwritten the HDD MBR.
You can revise grub later, if you wish.

Edit:
My experience is that Vbox runs very slowly when installed on Ubuntu on a USB2 flash drive.
But it is the only way I know to run AutoCAD from a portable flash drive.
Should not be too bad on a good USB3 flash drive.

---

### Post by at2smithjason on 2013-06-10
Cameron, This is on my laptop, I dont want to go and spelunking around the inside of my laptop.  It just sounds easier to use the live function whenever I want to use it.  Thanks for the help though.

---

### Post by C.S.Cameron on 2013-06-11
You may omit disabling the hard drive if, when partitioning you choose to install grub to the root of the usb drive you are installing Ubuntu to, (ie sdb not sdb1). Be cautious, many people have overwritten the HDD MBR.

---

### Post by zemega on 2013-06-11
You can disable the harddrive inside the BIOS. You can disable some other things as well.

---

### Post by Alan.Brown on 2013-06-11
I have installed Ubuntu 13.04 onto a USB drive several times.  Boot from the live DVD and plug in the USB drive - preferably 16GB as advised by [**[COLOR=#000000]jim_deadlock[/COLOR]**]("http://ubuntuforums.org/member.php?u=1108068").   Select Install from the main menu when the DVD has loaded.  When you get to the installation to drive part make sure you select the USB drive (which maybe **sdb  **or **hdb** - make sure it is not your hard drive which is usually **sda** or **hda**!) to use as the installation drive.   I have used USB drives formatted to **ext4** and **ntfs** without any trouble.  I have acheived this with just the live DVD without any other installation software such as unetbootin or uck.
**Make sure you select the correct drive for the boot MBR (sdb or hdb) otherwise you will overwrite the MBR on the Hard Drive.**    See the post by [**[COLOR=#000000]C.S.Cameron[/COLOR]**]("http://ubuntuforums.org/member.php?u=317145")
When the installation is complete, remove the live DVD and reboot.
As the computer starts to reboot select the **BIOS setup** procedure (on my Desktop I have to use **F10** and on the laptop **F2**).  In the BIOS settings go to the setting that allows you to select the USB drive instead of the Hard Drive to boot from then save the setting and exit to reboot.   You will have to do this on any computer on which you want use the USB to boot from.
You do not need to disable the hard drive nor do you need to get into the box itself - just to boot from the USB port.  I have used this procedure to boot from a USB drive in computers that are up to 10 years old - so it should be feasible on any modern computer.
HTH
Alan

---

### Post by sudodus on 2013-06-11
> **at2smithjason said:**
> I am trying to get 13.04 to run from a virtual box off of my 16 GB kingston USB stick.  I was trying to do a full install on it so that I could use virtual box (I used the LiLi live USB tool to create the live usb).  Every time I tried to do a full install, it didnt recognize my usb.  I was using the presistance file on it, and I read that it wouldnt work for a full install.  So I reformatted in the FAT32 and tried again without the persistance.  Still no luck.  Is there something that I am doing wrong?  I dont want to have to keep using the live function.  I would liek to be able to just plug in and go when ever I want to from anywhere I want to.  I did a little google searching and searched around on previous posts seemed to be people just asking how to do it.  Nothing with an issue like mine.  Do I need to go down to the last version?

Going back to your opening post:

- Why do you want to run VirtualBox off of a USB stick? I don't think you can boot VirtualBox from USB.

- Do you really want persistence? That is possible with the workaround, that you use a virtual disk instead of a USB device. But it is much easier to install directly from the iso file.

Keep the iso file in the host operating system. Make a virtual optical drive (CD/DVD), and connect it to the iso file. Then when you start the virtual machine, it will boot from it, as if it was a real boot CD or DVD. And you can make a normal installed system, which is better than a persistent live system.

*Edit*: Or maybe I misunderstood what you want to do. Do you want the VirtualBox virtual machine files on a USB drive?

---

### Post by C.S.Cameron on 2013-06-13
> **sudodus said:**
> Going back to your opening post:

- Why do you want to run VirtualBox off of a USB stick? I don't think you can boot VirtualBox from USB.


I  have run AutoCAD on Windows 7 on Vbox on Ubuntu on USB2 flash drive.
Verrrrrry Slooooooooow.
Might work ok on a good USB3 drive.

Edit:
Part of my problem was that I had Vbox installed in Ubuntu on one 8GB drive and the Windows virtual disk with ACAD on another 8GB drive.

---

### Post by at2smithjason on 2013-07-01
So I have some good news, I figured out how to boot from my USB stick.  Now I want to do a full install of ubuntu on my stick.  Its a 16GB Kingston Traveler and I have gathered by some of the looking and the comments that are made on here that I need to have at least a 8GB stick.   When I tried to install, I had 3 choices that all said dev/sda and they all have different sizes with them.  I know that I had about 15GB's left on my drive so I'm assuming that would've been the right one to use, but at the bottom of the dialog box there was something else that had my HDD in it.  If you need more info, tomorrow when I get a chance to I can take a picture with my phone and repost with all of the info.

---

### Post by oldfred on 2013-07-02
Full install to flash drive is just like any install to a second drive with a few extra settings to reduce writes as writes are slow. You do need to use Something Else or manual install, so at partitioning screen near bottom is the combo box on where to install the grub2 boot loader. You want it in the flash drive, not the usual default of sda or first drive.

I have a full install in 8GB with 8GB for data on my 16GB flash drive. A little slow loading but once in RAM works just like any system. Those are the only two partitions. I elected not to even have swap as I have 4GB of RAM and would not use a lot of apps at once.

 Full install - C.S.Cameron post #2
[http://ubuntuforums.org/showthread.php?t=2116798](http://ubuntuforums.org/showthread.php?t=2116798)


 Install to external drive. Also any second drive.
Installer version has not changed much so still a good guide except I do not recommend the separate /boot for most systems. Older systems may need it. And some with very large / (root) partitions. BIOS/MBR not for UEFI
[http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/](http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail - now alternative (text based) installer which is not available on newest versions. 
Different versions have slight difference in install screens but process is the same. And gui versions are not really a lot different.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)


 With SSD or Flash (trim do not work on flash) drives, Use ext4 without journal:
sudo tune2fs -O ^has_journal /dev/sda1
sudo tune2fs -o discard /dev/sda1
No swap or set swapiness or install 'Dynamic Swap Space Manager' from the Ubuntu Software Center
After installing, change the fstab so that everything gets mounted with noatime.

---

### Post by sudodus on 2013-07-02
The instructions by *oldfred* and *C.S.Cameron* are excellent, and give you an opportunity to create exactly the system you want.

But if you want a quick method to get 13.04 onto a 16 GB USB pendrive, the following method is also available.

[https://help.ubuntu.com/community/InstalledSystemFakePAE](https://help.ubuntu.com/community/InstalledSystemFakePAE)

Expand a compressed image file with Lubuntu 13.04 onto the drive. A pendrive prepared like this will run in most Intel and AMD based computers with 32-bit and 64-bit architecture including Pentium M. (The exception is UEFI, which must be switched off.)

---

### Post by C.S.Cameron on 2013-07-02
> **sudodus said:**
> The instructions by *oldfred* and *C.S.Cameron* are excellent, and give you an opportunity to create exactly the system you want.

But if you want a quick method to get 13.04 onto a 16 GB USB pendrive, the following method is also available.

[https://help.ubuntu.com/community/InstalledSystemFakePAE](https://help.ubuntu.com/community/InstalledSystemFakePAE)

Expand a compressed image file with Lubuntu 13.04 onto the drive. A pendrive prepared like this will run in most Intel and AMD based computers with 32-bit and 64-bit architecture including Pentium M. (The exception is UEFI, which must be switched off.)

This is a pretty slick method of installing to USB devices even on computers with PAE.

---

