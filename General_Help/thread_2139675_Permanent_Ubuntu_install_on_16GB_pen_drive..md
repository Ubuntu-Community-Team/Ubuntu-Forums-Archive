---
title: "Permanent Ubuntu install on 16GB pen drive."
date: 2013-04-27
forum: General Help
---

### Post by kingofcheese on 2013-04-27
Ok, first of all i want to say that my experience with Ubuntu and Linux is pretty much zero.
What i am trying to do, is a permanent install of Ubuntu on my 16GB pen drive.

I have downloaded the .iso file and installed a 'Live' version of Ubuntu using Universal USB Installer from PenDriveLinux.com, and can boot from the pen drive fine.
But every time i boot the OS, it asks me if i want to 'try' or 'install' Ubuntu, and one of the applications on the left is an 'install' button.
I tried clicking on install, but the only partition directories available to install on were the HDD or SSD.

Is there a way to do a 'permanent' install onto my pen drive?

My intention is to be able to use the pen drive to plug into any computer and boot a 'permanent' version of Ubuntu with all of my settings/programs/etc saved, rather than a 'Live' version.

Have made several Google searches and can't seem to find what i'm looking for.
Any help is greatly appreciated, keeping in mind that my experience with Ubuntu and Linux is VERY little.

---

### Post by grahammechanical on 2013-04-27
Did you create a persistence file? If you did then you have as near as you can get. Just hit Try each time. With a persistence file the settings and documents will be saved and you can install new applications. But you will not a have a lot of space. Perhaps 4 GB as the maximum.

Another thing you can try (and I have not tried this myself) is to create an Install image on a DVD and run the live session from that and direct it to install to the USB stick.

---

### Post by fantab on 2013-04-27
You can install Ubuntu on USB.

Plug in the USB you want to install to and boot with Ubuntu Live USB. (You will need two USB Pendrives for this). While installing you have to choose the "Something Else" option to manually install Grub bootloader to install on your USB. The rest of the install is normal. Creating a small SWAP partition on USB won't hurt, about 1gb or less.

You will have to format the USB with ext4 filesystem before installing Ubuntu. You can use Gparted on the LiveUSB format and partition.

Good Luck....

---

### Post by kingofcheese on 2013-04-27
Ok, I might try the dvd option first. Would I just be able to burn the live version to an iso image rather than a physical disc then load the image with daemontools? Then install to pen drive with ext4 filesystem?

---

### Post by pfeiffep on 2013-04-27
> **kingofcheese said:**
> Ok, first of all i want to say that my experience with Ubuntu and Linux is pretty much zero.
What i am trying to do, is a permanent install of Ubuntu on my 16GB pen drive.

I have downloaded the .iso file and installed a 'Live' version of Ubuntu using Universal USB Installer from PenDriveLinux.com, and can boot from the pen drive fine.
But every time i boot the OS, it asks me if i want to 'try' or 'install' Ubuntu, and one of the applications on the left is an 'install' button.
I tried clicking on install, but the only partition directories available to install on were the HDD or SSD.

Is there a way to do a 'permanent' install onto my pen drive?

My intention is to be able to use the pen drive to plug into any computer and boot a 'permanent' version of Ubuntu with all of my settings/programs/etc saved, rather than a 'Live' version.

Have made several Google searches and can't seem to find what i'm looking for.
Any help is greatly appreciated, keeping in mind that my experience with Ubuntu and Linux is VERY little.

Ubuntu can be made persistent on a USB stick, or you can install the entire OS on the stick - here's my thread about [this]("http://ubuntuforums.org/showthread.php?t=2130569")

---

### Post by C.S.Cameron on 2013-04-27
Following is step by step for installing 12.04.2 LTS on a 8GB flash drive on an Intel machine.
12.10 is similar. A Full install boots faster than a Persistent install, is more secure and can be updated or upgraded.

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

### Post by pfeiffep on 2013-04-27
> **C.S.Cameron said:**
> Following is step by step for installing 12.04.2 LTS on a 8GB flash drive on an Intel machine.
12.10 is similar. A Full install boots faster than a Persistent install, is more secure and can be updated or upgraded.

Turn off and unplug the computer. (See note at bottom)
[COLOR=#808080][I]Remove the side from the case.
Unplug the power cable from the hard drive.[/I][/COLOR]
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

If on the other hand you're dealing with a laptop
power off 
look for the screws on the bottom that secure the hard drive, remove, and slide the hard drive out.

---

### Post by Gizfreak on 2013-04-27
I succeeded with [the USB Installer from pendrivelinux.com]("http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/"). It supports Ubuntu 13.04 as you can see.

---

### Post by zemega on 2013-04-27
You dont really need to remove the harddrive. Go to BIOS and disable your harddrive (You only need to do this if you're using old computer that doesnt support USB booting well). Set primary boot to USB. Boot your computer/laptop with the USB that has the Ubuntu installer (I used Unetbootin to create one). Enter Ubuntu, plug in the big USB you want to install to. Then just install on that USB.

Edit, the typer of USB drive you are using and the USB port you are using does matters. USB 1.0 is slow, normal HDD will be way faster. USB 2.0 is pretty okay, If you can get yourself a USB with read/write speed more than 7MB/s its comparable to a 7200 rpm HDD. If you're using USB 3.0 you can get really fast, way faster than spinning HDD, but still slower compared to SSD, not that you will notice the difference unless you really do a lot of read/write. Note that, on packages, they will usually said up to 10 MB/s for USB 2.0, but you need to test it yourself to be sure, I'm not sure if there is a website that does the tests and keep tracks of it.

I install 13.04 onto one, and it sure was fast and stable on an Acer ZG5, it was a USB with 6.0MB/s +- write speed.

Do remember that if you accidentally disturb your USB, i.e. budging it and the connection is lost, you need to restart. Try getting some like this [http://www.sandisk.com/products/usb/drives/cruzer-fit/](http://www.sandisk.com/products/usb/drives/cruzer-fit/) .

---

### Post by C.S.Cameron on 2013-04-27
> **zemega said:**
> Try getting some like this [http://www.sandisk.com/products/usb/drives/cruzer-fit/](http://www.sandisk.com/products/usb/drives/cruzer-fit/) .

I picked up a few 16GB Sandisk Fits.
They run Ubuntu really well, I am impressed with the speed considering the price.
Only problem is I keep misplacing them.
Probably a good option to encrypt home when installing to one of these.

---

### Post by kingofcheese on 2013-04-28
Cheers everyone. Ill get myself another usb to put the live version on then install to the 16GB one.

---

### Post by r.stiltskin on 2013-04-28
A couple of things to keep in mind.

The beauty of a LiveUSB is that you can plug it into "any" computer (within certain limits, e.g., 32-bit vs. 64-bit, bios vs uefi) and it will work, so if you opt for a LiveUSB with persistence you can use that USB stick on many different computers, but the persistence file gets used up.  Add a file, it gets written to the persistence file.  Delete that file and not only do you not reclaim the space, but the deletion actually consumes some more space.  The persistence file is a sort of log of all the changes you make, so every change that you make to the files in the .iso consumes space in the persistence file.  I read somewhere that if you run out of space in the persistence file the stick will no longer boot.

On the other hand, if you partition and format the stick like a small hard disk and do a normal full (non-live) installation to it, it will act just like an installation to an ordinary hard disk.  You can add files and delete files as usual so you're much less likely to run out of space.  But, it will be set up with only the drivers and configurations needed to run on the computer on which you installed it, and won't work on other computers unless they're substantially identical (or at least "close enough") to the original machine in terms of CPU model, motherboard chipset, video card, etc.

---

### Post by rrich1974 on 2013-04-28
pretty good topic! 
so, you make a bootable dvd/usb, run the live ubuntu and plug the other usb.
then, install-choose sonething else- choose the other usb as installing drive. and also install the grub on the same usb. 
finally, boot the usb where you have installed. 
anyone of you have tried this?

---

### Post by fantab on 2013-04-28
As pointed out earlier in this thread, we CANNOT use full ubuntu/linx install on USB to run on any computer as we can with LiveUSB. The reason being during install Ubuntu will detect the hardware on your machine and install itself accordingly. As long as we are using this USB-Ubuntu on the same computer we are alright. But when we plug the same USB-Ubuntu on another computer it either won't boot at all or will run with many problems.

LiveUSB-Ubuntu (with or without persistence), on the other hand can boot and run on any computer because it is designed to run on number of Hardware varieties.

---

### Post by rrich1974 on 2013-04-28
i have got it right.  i will use it on the same computer. (signature) 
how is the speed? is it almost the same as a HDD instalation? i have usb 2.0.....i want to try later this day.
and what about swap? the system will use the swap from the hdd or i must create a swap in the usb? 
thanx a lot! 
i want to do that because my hdd is pretty old (1.8 years of working)  and an installation put a heavy load on it i i have only 160 GB.

---

### Post by fantab on 2013-04-28
> **rrich1974 said:**
> i have got it right.  i will use it on the same computer. (signature) 
how is the speed? is it almost the same as a HDD instalation? i have usb 2.0.....i want to try later this day.
and what about swap? the system will use the swap from the hdd or i must create a swap in the usb? 
thanx a lot! 
i want to do that because my hdd is pretty old (1.8 years of working)  and an installation put a heavy load on it i i have only 160 GB.

If you have SWAP on HDD then USB-Ubuntu will use that and you don't need to create one on USB. However, personally, I would create a small SWAP of 1GB or less (512MB), just for 'in case' senario. 

Another thing: If you enter your BIOS set up you may have an option to "Boot USB Devices First" or something like that. Enable it. When USB-ubuntu is plugged in it will boot first, if not then your HDD will boot. If you don't enable this feature then you will have to manually intervene to Boot your USB-Ubuntu.

Compared to your HDD, USB 2.0 will be slower. However USB 3.0 will be faster than USB 2.0. If you have a USB 3.0 port then you can consider buying a USB 3.0 PenDrive. 

HDD's are relatively cheap now. Consider getting yourself a New HDD with more storage capacity.

Good Luck...

---

### Post by rrich1974 on 2013-04-28
okay, i will try right now. i have an 8 GB pendrive and i will try. 
i will post the result.

later edit:
i have just installed 13.04 on a 8 GB usb, 2.0 and i can tell you guys that is not worth it. it is slow. maybe if i would have a 3.0 usb.....
the procedure is simple. format the usb as ext4 and add a small partition for swap. you must install the grub on that same USB. 
finally, boot from that usb. but i tell you, if you have 2.0 it is slow, especially when you install something or run multiple apps. the shutdown os also very slow. last time i have to force shutdown.

---

### Post by CaptainMark on 2013-04-28
I am quite surprised that no one has mentioned the main downside to doing a full install onto a usb.  When running a fully installed system there are a huge number of hard drive writes going on in the background, usb storage is just not designed to handle this huge number of writes and re-writes and can quickly corrupt, I'm speaking through experience and it will burn out your usb stick rendering it useless, how fast it happens depends on how much you use it.  A live usb does not write log files or modify databases so is not prone to this problem

---

### Post by ibjsb4 on 2013-04-28
I believe CaptianMark is talking about Journaling, it can be turned off in ext4 and ext2 doesn't have it.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=journaling&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=journaling&sa=Search&cof=FORID:9)

---

### Post by fantab on 2013-04-28
> **rrich1974 said:**
> okay, i will try right now. i have an 8 GB pendrive and i will try. 
i will post the result.

later edit:
i have just installed 13.04 on a 8 GB usb, 2.0 and i can tell you guys that is not worth it. it is slow. maybe if i would have a 3.0 usb.....
the procedure is simple. format the usb as ext4 and add a small partition for swap. you must install the grub on that same USB. 
finally, boot from that usb. but i tell you, if you have 2.0 it is slow, especially when you install something or run multiple apps. the shutdown os also very slow. last time i have to force shutdown.

Creating SWAP on USB is not a MUST if you have SWAP on HDD. With only 8gb Ubuntu WILL be slow. 16GB Pendrive will be a better option and relatively fast. On 8gb OS will be hard pressed for space. 

CaptainMark makes a valid point.

---

### Post by pfeiffep on 2013-04-28
> **fantab said:**
> If you have SWAP on HDD then USB-Ubuntu will use that and you don't need to create one on USB. However, personally, I would create a small SWAP of 1GB or less (512MB), just for 'in case' senario. 

Another thing: If you enter your BIOS set up you may have an option to "Boot USB Devices First" or something like that. Enable it. When USB-ubuntu is plugged in it will boot first, if not then your HDD will boot. If you don't enable this feature then you will have to manually intervene to Boot your USB-Ubuntu.

Compared to your HDD, USB 2.0 will be slower. However USB 3.0 will be faster than USB 2.0. If you have a USB 3.0 port then you can consider buying a USB 3.0 PenDrive. 

HDD's are relatively cheap now. Consider getting yourself a New HDD with more storage capacity.

Good Luck...

USB hard drives are also an option to consider - I use a USB 2 hard drive to fully install and test OSes on my laptop. More expensive than a USB flash drive but 320 Gb for ~$50 won't break the bank.

---

### Post by zemega on 2013-04-28
If you're saying running from your USB is slow, can you post the read/write speed as well? Since not all USB are fast. I used one with  ++6MB/s, 12.04 hangs sometimes in it, 13.04 no freeze at all, that is its a bit faster than 5400 rpm HDD. I remember before there were USB 2.0 with speed of barely 3.0MB/s, now thats way slower than 5400 rpm HDD.

As for the drivers, I did not have any problem running it at several different computer/laptop. The only trouble I have is when that computer has old Nvidea graphic cards (Nvidea is always a problem for Linux), and old motherboards. Its most likely it was not automatically supported in the current Ubuntu.

---

### Post by rrich1974 on 2013-04-28
i just have performed a benchmark with disk utility, a read-only (read/write does not work)
it seems to be good.

---

### Post by zemega on 2013-04-28
Well, its okay, not the fastest USB drive around, but its definitely better than old HDD, they need to let go of the HDD design, even Seagate has stated that it will stop developing 7200 rpm HDD. Write speed is also important. With HDD, you can only choose write or read at one time, that is not the case with SSD, but on USB, it differs between the actual technology for each. And most importantly, nothing physically moves inside a Flash drive, so you throw your USB and SSD into the freezer for a week and use it right away, yes someone did this crazy stunt and publish it.

---

### Post by oldfred on 2013-04-28
My install to a USB2 flash drive is not speedy, but seems very functional. And once apps are loaded they run just as fast as the kernel caches recent activity in RAM, so there is little activity to flash drive.

But I did change ext4 to turn journal off and other settings to reduce writes.

       With SSD or Flash (trim do not work on flash) drives, Use ext4 without journal:
sudo tune2fs -O ^has_journal /dev/sda1
sudo tune2fs -o discard /dev/sda1
No swap or set swapiness or install 'Dynamic Swap Space Manager' from the Ubuntu Software Center
After installing, change the fstab so that everything gets mounted with noatime.
Make sure BIOS is in AHCI mode for trim to work.
change to noop i/o scheduler
But per this noop may not now be best.
[URL="http://www.phoronix.com/scan.php?page=article&item=linux_iosched_2012&num=1"]http://www.phoronix.com/scan.php?page=article&item=linux_iosched_2012&num=1

[/URL] Post #14 some flash drives that did not work
[http://ubuntuforums.org/showthread.php?t=2120196](http://ubuntuforums.org/showthread.php?t=2120196)
More tests Flash drives post #5 -  C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=2130234](http://ubuntuforums.org/showthread.php?t=2130234)

[URL="http://www.phoronix.com/scan.php?page=article&item=linux_iosched_2012&num=1"]
[/URL]

---

### Post by C.S.Cameron on 2013-04-28
> **CaptainMark said:**
> I am quite surprised that no one has mentioned the main downside to doing a full install onto a usb.  When running a fully installed system there are a huge number of hard drive writes going on in the background, usb storage is just not designed to handle this huge number of writes and re-writes and can quickly corrupt, I'm speaking through experience and it will burn out your usb stick rendering it useless, how fast it happens depends on how much you use it.  A live usb does not write log files or modify databases so is not prone to this problem

I have never heard of anyone bricking a (quality) flash drive running Ubuntu from it.
Most flash drives are good for at least 10000 writes and have wear leveling.

Now take an empty flash drive and time how long it takes to fill up by copying files to it.

16 000 MB @ 10 MB/s = 1600 seconds = 27 minutes.

Multiplying that by 10000 = 111 forty hour work weeks.

And nobody writes to a flash drive full time so figure about ten years of actual use.

[http://www.bress.net/blog/archives/114-How-Long-Does-a-Flash-Drive-Last.html](http://www.bress.net/blog/archives/114-How-Long-Does-a-Flash-Drive-Last.html)

I am using 10GB swap on the flash drive that powers my home entertainment center because I want to ensure that the computer hibernates when not in use.

I do not install swap on general purpose flash drive installs.

Full install flash drive should work on any (non UEFI) computer as long as proprietary drivers are not installed.

---

### Post by zemega on 2013-04-28
After looking at other threads, I have to admit, I am using SanDisk drives line, Cruzer Pop, Cruzer Fit and Ultra. You know, we should create a subforum just for running Ubuntu off USB thumdrive, or externals.

---

### Post by C.S.Cameron on 2013-04-28
> **zemega said:**
> After looking at other threads, I have to admit, I am using SanDisk drives line, Cruzer Pop, Cruzer Fit and Ultra. You know, we should create a subforum just for running Ubuntu off USB thumdrive, or externals.

+1

---

### Post by CaptainMark on 2013-04-29
> **ibjsb4 said:**
> I believe CaptianMark is talking about Journaling, it can be turned off in ext4 and ext2 doesn't have it.
Journalling is only a small part of it, 

@c.s.cameron its not that simple, all it takes is one corrupt sector to make a filesystem go haywire, and you have heard of someone bricking a flash drive from this, as I said, I'm talking from experience,
i'm not saying its a huge show stopper problem, but its something that should be considered, no one minds about bricking a freebie 2gb usb drive you got from some promotional thing, but 32/64gb one that you paid for is a different story

---

### Post by C.S.Cameron on 2013-04-29
16GB drives are under $10 and have 2-5 year warranties, I agree it is not a show stopper.
As I understand, a flash drive that fails from too many writes is still readable.
Many people seem afraid that if they run Ubuntu from a flash drive it will burn out in a few days.
I have a flash drive still working after six years of running Linux.

You are the first person I have actually heard of bricking a flash drive running Ubuntu.
Was it a name brand drive with wear leveling?
Are you sure it failed solely from running Ununtu?

---

### Post by CaptainMark on 2013-04-30
No it was only a freebie no-name one and I can't be sure it was that. Given the pros and cons I feel a Live USB is a better method than a full USB install, but to each his own.

---

### Post by C.S.Cameron on 2013-04-30
Each has it's advantages, I guess it depends what you need it for.
Full installs boot faster and are more secure but can't be used to install Ubuntu or fit on a drive under 5GB.
All my removable devices, including my MP3 player, have either Full or Persistent installs on them.

---

### Post by oldfred on 2013-04-30
On my larger flash drives with a full install, I put ISOs directly into the data partition and use grub2 to loopmount them. So my full install can be an installer also, but is more for the repair ISO as a super repair flash drive with a variety of repair ISO.

---

