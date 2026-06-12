---
title: "How to add a new drive as dual boot"
date: 2021-08-31
forum: General Help
---

### Post by satimis on 2021-08-31
Hi all,

SilverFast SE (Plus) or SilverFast 8 coming with Epson V850 Pro flatbed scanner only work on Windows.  Therefore I need to run Windows on bare metal for using the Epson scanner.  On my PC, all windows are running as VMs.

PC config.
Host - Ubuntu 20.04
Virtualization software - Oracle VirtualBox
VMs - Ubuntu 20.04, Win10 Pro, Win10 Home etc.

I have Windows ISO.  Would it be possible adding a 500G SSD to my PC, as dual boot, to install Windows direct on their ISO without creating a Windows boot-USB.

If Yes, please advise where can I find relevant documents?  Thanks in advance

Regards

---

### Post by yancek on 2021-08-31
>  I have Windows ISO.  Would it be possible adding a 500G SSD to my PC, as  dual boot, to install Windows direct on their ISO without creating a  Windows boot-USB.
 

Yes.  See my explanation in the link below, post  5 at that site.  It's definitely not a 1 step process.  Some things you need to remember are to use ntfs rather than vfat filesystem from which to boot the extracted iso file as some files are over 4GB and vfat can't handle them.  Also, make sure you get the correct UUID as explained at the end of the explanation.  I got this method from a site which had images attached to make it simpler but can't seem to find. 

  [https://ubuntuforums.org/archive/index.php/t-2263582.html](https://ubuntuforums.org/archive/index.php/t-2263582.html)

---

### Post by Autodave on 2021-08-31
On my machine, I disconnected the internal HD and installed a second one on a different MB port.  After installation of Linux, I plugged the Windows drive back in and then went to the BIOS and made sure that Linux was the first bootable.  Then, made Windows the secong bootable.  When I need Windows, I just enter the boot order and choose Windows.

---

### Post by oldfred on 2021-08-31
Windows has been known to install a boot partition, old boot with BIOS or ESP with UEFI to default boot drive based on UEFI/BIOS settings.
It does not see Linux partitions and just overwrites whatever was in the default drive.
So either make sure drive you are installing Windows into is seen as default drive (not sure how to do that, have not installed Windows) or disconnect other drives.

And have good backups, just in case.

---

### Post by satimis on 2021-08-31
Hi all,

Thanks for your advice.

What I did in the past;
1. Disconnect all hard discs on the PC.
2. Connect a new hard disc for installing Windows
3. Boot the PC with Windows boot USB
4. Install Windows on the new hard disc
5. Reconnect all hard discs to the PC
6. Boot the PC and select the booting disc on BIOS

It worked for me in the past without problem but I need to burn a boot Windows USB.

This time I'm prepared to try a new adventure, installing Widows direct on its ISO.  I'm searching for a working document guiding me.  But if disconnecting all running hard discs on the PC I can't boot the PC.

Regards

---

### Post by dragonfly41 on 2021-08-31
I do have Windows 10 in my internal drive and Ubuntu on two external SSD's in USB 3.0 dual docking bay.

If you are starting a new adventure then you might look at Windows 11 which comes with a full version of Ubuntu. I have not yet made this leap but here is the documentation.

[https://docs.microsoft.com/en-us/windows-insider/isos](https://docs.microsoft.com/en-us/windows-insider/isos)

Returning to your status quo I have read about inline power switches which can toggle power to various drives.

My compromise solution is using a StarTech dual docking bay (USB 3.0) which allows me to unplug external SSD's (Ubuntu installed), but not going as far as switching off the power to the internal drive containing Windows 10.

I have read about the option of temporarily switching off the boot flags in Windows internal drive but I have not tried that (using LiveUSB / Gparted / bootflags).

Final idea, I would try ReFIND as an overlay to Grub in multi OS setups.  I use it to switch between Windows and other Ubuntu installations. It can be installed in external SSD to separate from the internal drive.

---

### Post by yancek on 2021-08-31
>  
This time I'm prepared to try a new adventure, installing Widows direct on its ISO.   

If I understand your question, you want to boot the windows installer directly from a partition on your hard drive so you don't have to use a usb.  If that's the case, it is explained in the link in my previous post.  Obviously, you will not have to disconnect any disks.

---

### Post by satimis on 2021-09-01
> **yancek said:**
> If I understand your question, you want to boot the windows installer directly from a partition on your hard drive so you don't have to use a usb.  If that's the case, it is explained in the link in my previous post.  Obviously, you will not have to disconnect any disks.
Hi yancek,

Thanks for your advice.

I went through your posting;
February 2nd, 2015, 05:26 PM
of your link.
[https://ubuntuforums.org/archive/index.php/t-2263582.html](https://ubuntuforums.org/archive/index.php/t-2263582.html)

For safety reason I'm prepared to disconnect the other 2 hard discs on my PC
Hard disc 1 - 2TB SSD for running Ubuntu 20.04 as OS and VirtualBox
Hard disc 2 - 2TB WD for data storage.

The Windows 10 Home ISO and Windows 10 Pro ISO are 100% working.  All Windows VMs were installed on them previously.

**I wonder whether following steps will help me :-**
1. Connect the 500G SSD to PC for installing Windows 10 Pro
2. Copy Windows 10 Pro ISO on 500G SSD
**[COLOR="#FF0000"]Question;[/COLOR]**
Do I need to format 500G SSD which is an old disc having non-useful old data on it?  OR during installing Windows 10 Pro the old data will be erased automatically ?

3. Disconnect Hard disc 1 and Hard disc 2
4. Boot up the PC with an Ubuntu 20.04 boot USB
5. Cd 500G SSD and start installation

Please advise.  Thanks in advance

Regards

---

### Post by yancek on 2021-09-01
>  Boot up the PC with an Ubuntu 20.04 boot USB 

No, that won't work. You will need to boot the windows installer from Grub as explained in the link I provided.  You can boot the Ubuntu USB and put a boot entry for the windows installer but when you reboot, it will not be there as the 'live' USB is read only and all data/changes are lost on reboot.  You need to put the windows installer boot entry in the grub.cfg file on your installed Ubuntu which means that drive will need to be attached when you boot the windows installer  

There are 2 major steps involved, one is creating the partition for the windows installer and copying all the folders/files from the extracted iso to the ntfs partition so that you can boot it.
The second step is the actual installation.

If your Ubuntu install is UEFI, you need to install windows UEFI or it won't boot from Grub.  This means your drive, the one you want to install to (500GB drive) should be a GPT drive.  You can do this with Gparted if you have it installed on Ubuntu.  Otherwise you can use the Ubuntu install USB which does have GParted.  You should have an EFI partiton on this drive.  I don't know if you need to create this in advance or if the windows installer will do it for you. When I did this 6 years ago, it was on a Legacy/msdos drive. 

If you have free space on your Ubuntu drive, I would create an ntfs partition on that drive for the windows installer.  If you don't have free space, you will need to shrink the Ubuntu partition and you will need to use GParted on the 'live' Ubuntu USB as partitions cannot be modified from a running Linux OS.  Extract the iso and copy the extracted files to this partition and put the windows boot entry in the grub.cfg file so you can boot the windows installer partition. Reboot the machine and select the windows installer entry to begin the installation.  I expect the installer will create the necessary partition but am not sure.  If you get an error/errors, you may need to create and EFI and ntfs partition from GParted.  Once you have finished the installation and successfully booted windows, you can delete or format this partition to use again.
It should not be difficult to get the correct device to install to as your Ubuntu drive is 1TB and the drive you want to install to is 500GB.  Use sudo fdisk -l or sudo parted -l to get the naming for each drive (sda, sdb,sdc, etc).   

If you successfully boot the windows installer, one of the steps gives you install options.  If I remember correctly, this is immediately after the window where you see the windows licensing agreement and here you should select the Custom option if you see it.

I found the link to the site I used to do this.  The site explains how to create a bootable windows USB without using any specific software for this purpose and booting it from Grub.  THe link is below and remember that it is explaining how to boot from a USB so wherever it makes such a reference, change it to the installer partition on your drive.  Also, obviously skip the part at the link below to install Grub as that is not necessary, you already have Grub on the 1TB drive and are not using a USB.  Another thin, I would use the UUID method rather than the drive label.  This is explained about half way down the page.  

 [https://www.onetransistor.eu/2014/09/make-bootable-windows-usb-from-ubuntu.html](https://www.onetransistor.eu/2014/09/make-bootable-windows-usb-from-ubuntu.html)

If something is not clear to you, don't proceed but post back before continuing.  Good luck.

---

### Post by satimis on 2021-09-02
> **yancek said:**
> No, that won't work. You will need to boot the windows installer from Grub as explained in the link I provided.  You can boot the Ubuntu USB and put a boot entry for the windows installer but when you reboot, it will not be there as the 'live' USB is read only and all data/changes are lost on reboot.  You need to put the windows installer boot entry in the grub.cfg file on your installed Ubuntu which means that drive will need to be attached when you boot the windows installer  

There are 2 major steps involved, one is creating the partition for the windows installer and copying all the folders/files from the extracted iso to the ntfs partition so that you can boot it.
The second step is the actual installation.

If your Ubuntu install is UEFI, you need to install windows UEFI or it won't boot from Grub.  This means your drive, the one you want to install to (500GB drive) should be a GPT drive.  You can do this with Gparted if you have it installed on Ubuntu.  Otherwise you can use the Ubuntu install USB which does have GParted.  You should have an EFI partiton on this drive.  I don't know if you need to create this in advance or if the windows installer will do it for you. When I did this 6 years ago, it was on a Legacy/msdos drive. 

If you have free space on your Ubuntu drive, I would create an ntfs partition on that drive for the windows installer.  If you don't have free space, you will need to shrink the Ubuntu partition and you will need to use GParted on the 'live' Ubuntu USB as partitions cannot be modified from a running Linux OS.  Extract the iso and copy the extracted files to this partition and put the windows boot entry in the grub.cfg file so you can boot the windows installer partition. Reboot the machine and select the windows installer entry to begin the installation.  I expect the installer will create the necessary partition but am not sure.  If you get an error/errors, you may need to create and EFI and ntfs partition from GParted.  Once you have finished the installation and successfully booted windows, you can delete or format this partition to use again.
It should not be difficult to get the correct device to install to as your Ubuntu drive is 1TB and the drive you want to install to is 500GB.  Use sudo fdisk -l or sudo parted -l to get the naming for each drive (sda, sdb,sdc, etc).   

If you successfully boot the windows installer, one of the steps gives you install options.  If I remember correctly, this is immediately after the window where you see the windows licensing agreement and here you should select the Custom option if you see it.

I found the link to the site I used to do this.  The site explains how to create a bootable windows USB without using any specific software for this purpose and booting it from Grub.  THe link is below and remember that it is explaining how to boot from a USB so wherever it makes such a reference, change it to the installer partition on your drive.  Also, obviously skip the part at the link below to install Grub as that is not necessary, you already have Grub on the 1TB drive and are not using a USB.  Another thin, I would use the UUID method rather than the drive label.  This is explained about half way down the page.  

 [https://www.onetransistor.eu/2014/09/make-bootable-windows-usb-from-ubuntu.html](https://www.onetransistor.eu/2014/09/make-bootable-windows-usb-from-ubuntu.html)

If something is not clear to you, don't proceed but post back before continuing.  Good luck.
Hi yancek,

Thanks for your detail advice and your time spent to help me.

My reason not to touch the SSD running Ubuntu 20.04 is having 36 websites running on VMs of VirtualBox.  Those 36 websites are the cloned live websites running on Internet.  In case of problem on the live websites I just clone the local website on the problematic live website.  I have done this step in multiple occasions in the past

I'm now considering following 2 solutions:-

1)
How to Easily Create Windows 10 Bootable USB on Ubuntu or Any Linux Distro
[https://www.linuxbabe.com/ubuntu/easily-create-windows-10-bootable-usb-ubuntu](https://www.linuxbabe.com/ubuntu/easily-create-windows-10-bootable-usb-ubuntu)

or

Make A Bootable Windows 10 USB Install Stick On Linux With WinUSB Fork (WoeUSB)
[http://www.webupd8.org/2016/06/make-bootable-windows-10-usb-install.html](http://www.webupd8.org/2016/06/make-bootable-windows-10-usb-install.html)

Install woeusb.  I have spare USB stick.

2)
How to Burn ISO to DVD on Ubuntu 20.04 Desktop
[https://linuxconfig.org/ubuntu-20-04-burn-iso-to-dvd](https://linuxconfig.org/ubuntu-20-04-burn-iso-to-dvd)

Install Brasero.  I have DVD writer on the PC

Which route shall I select, booting USB or booting DVD?

Comment would be appreciated.

Regards

---

### Post by yancek on 2021-09-02
The link in my post above (post 9) is basically the same as the first link in your last  post so I would suggest that.  In your link, use the first option to install EFI to a USB .  It might be simpler to write the widows iso to a DVD.  I haven't used DVD's in years.  Make sure the windows iso file is smaller than the capability of the DVD.  The original standard size for data is/was 4.7GB and the windows iso is likely larger than that.  Some newer DVD's should be able to hold more, I don't know as I don't use them.  I have never used WoeUSB so don't have any opinion on it.

Try either of these methods if the DVD doesn't work.

 [https://www.linuxbabe.com/ubuntu/easily-create-windows-10-bootable-usb-ubuntu](https://www.linuxbabe.com/ubuntu/easily-create-windows-10-bootable-usb-ubuntu)

[https://www.onetransistor.eu/2014/09/make-bootable-windows-usb-from-ubuntu.html](https://www.onetransistor.eu/2014/09/make-bootable-windows-usb-from-ubuntu.html)

---

### Post by oldfred on 2021-09-02
Not sure if very newest Windows changed to just have ISO work in FAT32 with split .wim file.

Older Windows that fit into 4GB limit of FAT32 could just be extracted & booted in UEFI boot mode.
But then they changed the .wim file and made it larger than 4GB. The Windows installer tool to create flash drive splits the .wim file into 2 parts to work for FAT32 & UEFI boot. Older instructions on Internet often do not cover the size of the .wim newer versions of Windows.

Split .wim with Linux tools.
[https://www.dedoimedo.com/computers/windows-10-usb-media-linux.html](https://www.dedoimedo.com/computers/windows-10-usb-media-linux.html)
The .wim too large, Windows commands to split
[https://www.dell.com/support/article/en-us/sln313422/windows-10-iso-contains-wim-file-that-is-big-for-fat32-file-system?lang=en](https://www.dell.com/support/article/en-us/sln313422/windows-10-iso-contains-wim-file-that-is-big-for-fat32-file-system?lang=en)

---

### Post by satimis on 2021-09-03
Hi yancek and oldfred,

I haven't burned CD/DVD for prolonged time.  Fortunately I found a blank-new TDK DVD-RW disc of 4.7G 4x on shelves. On inserting the TDK DVD-RW disc in the DVD Writer, it popup "bland-new DVD".

Start Brasero and select Win10 Pro ISO and then the DVD RW disc -> Burn

It went through without complaint until finish.

Now how can I check the Win10 Pro installer disc working before I disconnect the Ubuntu 20.04 SSD and the storage WD HD in my PC?  

On inserting Win10 Pro installer disc on the DVD Writer, nothing popup.

Regards

Edit
Screenshot of DVD writer spec

---

### Post by yancek on 2021-09-03
>   On inserting Win10 Pro installer disc on the DVD Writer, nothing popup.

Do you not see an icon for the DVD in the left panel on Ubuntu?  I don't know what all the info on the DVD means.  I would suggest that you reboot and go into the BIOS firmware boot options and select the option for the DVD with windows installer on it to test if it boots.  If it does boot, reboot and disconnect the drives and have only the drive you want to install windows to attached.  THis 500GB drive on which you wish to install windows isn't a USB drive is it?  If so, I would not expect it to work.

---

### Post by satimis on 2021-09-03
> **yancek said:**
> Do you not see an icon for the DVD in the left panel on Ubuntu?  I don't know what all the info on the DVD means.  I would suggest that you reboot and go into the BIOS firmware boot options and select the option for the DVD with windows installer on it to test if it boots.  If it does boot, reboot and disconnect the drives and have only the drive you want to install windows to attached.  THis 500GB drive on which you wish to install windows isn't a USB drive is it?  If so, I would not expect it to work.
The icon is a clip added by Ubuntu forum, nothing relevant to the content in the screenshot.  When I check the DVD disc it seems to me not burned compared to other discs.  I wonder whether I need to blank the DVD first before burning.  The DVD is RW disc.  I can burn it again.

I have another blank-new TDK DVD-RAM disc, still sealed in plastic film.  The said disc is made in Japan with all instruction in Japanese.  The only instruction I can understand is "the disc is for recording video - 120 min".

The 500GB SSD is an internal drive with SATA connection

Edit-1
The information on the screenshot showing that the cdrom is a DVD RAM Writer

Edit-2
Tried booting the newly burnt Win10 Pro disc and failed, continue asking to insert the booting media

---

### Post by oldfred on 2021-09-03
Have not used DVD for installing for years.
But remember (I think), that the rewriteable DVDs did not work reliably for creating an bootable drive for installing.
Part of reason I converted to flash drives, was that I often had bad burns & created another coaster. I only have one coffee cup (at a time) so did not need all the coasters.
Another thing was to use slowest speed possible as that supposed improved quality.

---

### Post by satimis on 2021-09-03
> **oldfred said:**
> Have not used DVD for installing for years.
But remember (I think), that the rewriteable DVDs did not work reliably for creating an bootable drive for installing.
Part of reason I converted to flash drives, was that I often had bad burns & created another coaster. I only have one coffee cup (at a time) so did not need all the coasters.
Another thing was to use slowest speed possible as that supposed improved quality.
Hi oldfred,

Burned Win10 Pro ISO on DVD-RW disc the second time.  It went through without complaint and finally eject the disc at finish.

Inserted the disc in the DVD Writer and Ubuntu detected it this time showing all files.  Booted Win10 Pro.  This time it worked asking where to install Win10 Pro.

I'll connect the 500G SSD in the PC and disconnect other hard drives later.  I'll come back after having installed Win10 Pro,

Regards

---

### Post by oldfred on 2021-09-03
You should get two boot modes in UEFI.
One clearly UEFI:xxx and other just xxx which is then BIOS.
Be sure to boot in correct mode.

Windows requires gpt partitioning for UEFI and requires MBR(msdos) for MBR. It will erase drive, if not in correct partitioning or may give error that it cannot install. With UEFI, it wants multiple partitions, so best to just let it create whatever it wants.

---

### Post by satimis on 2021-09-04
Hi all,

I have tried more than an hour and couldn't get Window10 Pro installed.  I could start Window10 Pro boot DVD and copy files but always failed on "Updating Windows".  Warning;```

Windows cannot copy files from E:\Sources to D:\$Windows~LS\Source.  Network problem may be preventing Windows from accessing the files.  Make sure the computer is connected to the network and restart the installation .  Error code:0x8007000s
```

The computer is connected to 500MB Fibre Network.  I don't know how to proceed further.

---

### Post by satimis on 2021-09-04
Hi all,

Now I have finished installing Win10 Pro.  The solution is very simple and funny, just change the connection of the 500G SSD to another port.  Now Win10 Pro is running on this PC and I have tested rebooting it.

I'll start another adventure soon reinstalling Ubuntu 20.04 because of the problem mentioned on another posting:
How to disable Alert Sound 
[https://ubuntuforums.org/showthread.php?t=2466616&page=2&p=14057119#post14057119](https://ubuntuforums.org/showthread.php?t=2466616&page=2&p=14057119#post14057119)

I have no solution.  It'll take me several hours to finish because I have to install Oracle VirtualBox and to clone all live websites on it.  I have already copied all valuable data to the Data storage WD hard drive.

I'm now posting this reply on Win10 Pro

Edit
===
Dual boot works;_
1) Switch on PC.  It boots straight to Ubuntu 20.04
2) To boot Win 10 Pro, select from BIOS

Regards

---

