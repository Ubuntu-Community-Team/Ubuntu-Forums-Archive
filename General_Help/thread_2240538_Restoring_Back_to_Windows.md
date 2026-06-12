---
title: "Restoring Back to Windows"
date: 2014-08-20
forum: General Help
---

### Post by George_Lawrence on 2014-08-20
Hi,

I installed Ubuntu on my Toshiba laptop running Windows 8.1. When I installed Ubunutu, I erased Windows completely and installed Ubuntu on the entire hard drive. I would like to get Windows 8 back on the hard drive because I need a school software that is only supported on Windows. Is there anyway I can get Windows back on my computer? I would like to get Ubuntu back on my laptop along with Windows. But for now I am mainly focusing on getting Windows 8.1 back on my computer? Once again, I erased Windows completely. 

Any Help is greatly appreciated.

Thanks

---

### Post by overdrank on 2014-08-20
Hi and welcome :) , maybe this can help _[WindowsDualBoot]("https://help.ubuntu.com/community/WindowsDualBoot")_

---

### Post by oldfred on 2014-08-20
Did you make a complete backup of Windows before erasing it?

Otherwise you have to contact vendor of system and see if they have the DVD set that is the image of your hard drive as purchased. Some offer it just for shipping, others do not have anything.

Or you have to totally purchase a new copy of Windows. Your product key is imbedded in the UEFI and is only valid for the vendor version not any other version.

---

### Post by yancek on 2014-08-20
I haven't used windows 8 but earlier versions, if you got an OEM (pre-installed) system, you would have been prompted to create a recovery CD/DVD when you first used it and you could now use that  to access the Recovery partition and reset to factory default thus erasing Ubuntu.

Again, if it was an OEM, you could have obtained and installation medium from the manufacturer at an additional cost, still much less than buying from any computer store.  Use that.

If you purchased windows installation medium, no problem just install it again.

---

### Post by George_Lawrence on 2014-08-20
Ok. I don't have a recovery disk but would I be able to burn one from the Alienware computer my friend has and use it to get windows back?

---

### Post by oldfred on 2014-08-20
Only if you have an Alienware computer that is the same model. They internals are tied to each vendor and then to the model number.
One user did post that the store he purchased from still had the same model on the floor and the tech was able to make a Recovery DVD set for him. I call that really good customer service, but do not expect that from most stores.

---

### Post by lisati on 2014-08-20
> **George_Lawrence said:**
> Ok. I don't have a recovery disk but would I be able to burn one from the Alienware computer my friend has and use it to get windows back?

Be very careful where you get your recovery disk from. Apart from licensing issues (we take a dim view of circumventing EULAs here) and the risk of malware, you'll probably find that the recovery disk for a machine from one manufacturer is less than ideal for using with a machine from another manufacturer.

---

### Post by George_Lawrence on 2014-08-20
Ok. So once I get a recovery disk from toshiba, how do I restore it back to windows? How do I boot from the recovery disk? 

I know y'all think I'm an idiot.

---

### Post by George_Lawrence on 2014-08-20
And how does a recovery disk work? How does it get windows back if it's not the full version of windows?

---

### Post by lisati on 2014-08-20
> **George_Lawrence said:**
> And how does a recovery disk work? How does it get windows back if it's not the full version of windows?

The disks I've used (including two different model Toshiba laptopss, a Compaq laptop, and a Compaq desktop) work a bit like an installation disk that restores the machine to the condition it was when you first open the box.

---

### Post by overdrank on 2014-08-20
Hi and I am no expert :) but could you post the output of this command
```
sudo fdisk -l
```
The last letter of the command is a L just not capital. 
Just to make sure there is no window restore partitions on the hard drive.

The windows recovery disc are usually dvd because the about of data for the installation of windows.
lisati beat me to it :P

---

### Post by yancek on 2014-08-20
The Recovery disk will access a recovery partition on your hard drive if you have an OEM (pre-installed) version of windows.  It will set it back to factory default erasing everything else on the disk including your Ubuntu.  Since you don't have an installation medium for windows I guess we are asssuming you have an OEM install which should have a recovery partition.  The problem may be that when you installed Ubuntu you overwrote everything including this partition.  Running the fdisk -l command suggested above and posting the output here should tell us if you still have any windows partitions.

---

### Post by craig10x on 2014-08-20
Exactly....the restore disc(s) will totally wipe the system and restore windows as it was when you first fired up the computer after you took it out of the box...

---

### Post by oldfred on 2014-08-20
Some may just erase drive & restore it. 
Others may require you to remove the Linux partitions first and/or have the standard partitions that Windows expects. 

If you look at a lot of the BootInfo reports you often see even more partitions than this suggestion. Not sure why but some have another FAT32 not flagged as efi but with vendor efi files. Some have extra recovery partitions. Or it can vary. Hopefully yours just restores entire drive. But then back up anything related to Ubuntu that you may want to save first.

 Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)

---

### Post by Cliff_Simonds on 2014-08-21
The easiest way to reinstall windows 8.1 when you don't have a disk is in[ this]("http://www.howtogeek.com/186775/how-to-download-windows-7-8-and-8.1-installation-media-legally/") How to Geek article. Read it thoroughly, hope it helps.
ps: this way you have windows without the bloatware, but then you can download the oem drivers and any programs you want or need at the manufacturers site for your model. I did this two years ago, works like a dream. This is why I like ubuntu no bloatware, or shareware. ha!

---

