---
title: "Create a bootable GRUB on a USB stick in order to format Ubuntu and to install Window"
date: 2015-08-29
forum: General Help
---

### Post by RocknRollTim on 2015-08-29
Hi there,

Can anyone advise on how to create a bootable GRUB on a USB stick in order to format Ubuntu and to install a Windows OS on a PC? It's just I want to set a PC back to factory defaults but unable to as the PC ignores the boot priority and boots up Ubuntu after setting the preferred device order i.e. USB stick, external CD/DVD drive and then Hard Disk. The PC's internal CD/DVD drive is broken and won't open and haven't got a spare internal CD/DVD drive onsite to replace it. I would preferably like to create the GRUB in Windows using a utility but don't know which one to go for nor do I know how to go about programing it. I have tried various methods to format the drive in order to install Windows i.e. using an IDE kit to convert it into an external drive and trying to format it in Windows using Disk Management on another PC as well as making the drive a Slave drive in Windows using the same PC but no joy in getting to recognise it. Your ideas and suggestions would be appreciated.

Kind regards,

RocknRollTim

---

### Post by yancek on 2015-08-29
> Can anyone advise on how to create a bootable GRUB on a USB stick in  order to format Ubuntu and to install a Windows OS on a PC? 

You can install Grub on a usb stick but Grub is a bootloader and you can't format anything from it.  You could use pretty much any Linux system on a Live CD/flash drive to do it.  If you still have your Ubuntu install medium, you can use GParted which is on it.  Ubuntu and Grub don't have anything to do with your BIOS and don't control it and can't change it.  One thing you might check is to see if the usb you are using is actually listed under hard drives in the BIOS.  

How are you planning to install windows if you don't have a CD/DVD drive?  If you have it on a flash drive, why can't you just boot it to install windows?

> I would preferably like to create the GRUB in Windows using a utility  but don't know which one to go for nor do I know how to go about  programing it 

That won't work.  Are you using the term "drive" to mean a partition or do you have multiple physical hard drives and is Ubuntu on one and windows on another?  I'm not sure why you feel you need to format the Ubuntu partitions.  The windows installation medium should be able to do that during the install.

---

### Post by RocknRollTim on 2015-08-30
Hi yancek,

Thank you for responding to my thread but as well as trying a live CD/flash drive to boot and to overwrite Ubuntu as well as trying GParted from the Ubuntu install medium, I might first try using Seagate DOS Tools before resulting to one of your suggestions in your post.

With regards to using GParted from the Ubuntu install medium, would it matter if I recreated it using the latest ISOs on a CD/DVD or a USB stick? It's just I have misplaced the original Ubuntu install medium for when I installed on the PC.

I have tried changing the boot order in BIOS for either a USB stick or an external CD/DVD drive to boot first with having the media inserted but the PC just kept ignoring it both with the original Windows CD and with the Windows CD mounted onto a USB stick using Refus and the Windows 7 CD/USB Tool.

As you said that a GRUB that can't be used to format a file system but can used as a boot loader, are there any utilities to create a GRUB in Windows as well as in Linux OSs such as Ubuntu?

If I was to create a GRUB (boot loader) for Windows using a recommend suggestion, would you be able to post the code on how to create this?

Like I said before my intention is to either use an external CD/DVD drive or a USB stick to boot Windows and also like I said before I can't boot Windows from a USB stick as it just gets ignored by the PC even when changing the boot order in BIOS. I might also try changing the filesystem format of the stick from NTFS to one of the file system formats such as exFAT, FAT and FAT32.

Lastly I'll let you know how I get on with most of the suggestions apart from the GRUB which I don't know how to create and need some assistance in order to create it as I have very little knowledge of how Linux works including Ubuntu and is my first time using it plus the PC was setup by one of my friends and so used to using Windows.

Kind regards,

RocknRollTim

---

### Post by yancek on 2015-08-30
> With regards to using GParted from the Ubuntu install medium, would it  matter if I recreated it using the latest ISOs on a CD/DVD or a USB  stick? It's just I have misplaced the original Ubuntu install medium for  when I installed on the PC.

No.  Use any current release with GParted on it or download GParted from the site below if you do not have it.

[http://gparted.org/download.php](http://gparted.org/download.php)

> As you said that a GRUB that can't be used to format a file system but  can used as a boot loader, are there any utilities to create a GRUB in  Windows as well as in Linux OSs such as Ubuntu?

Grub is a bootloader, that's its only function although it is fairly complex.  
My understanding of your current situation is that you have some version of Ubuntu currrently installed as the only operating system on the computer and that you are able to boot and use it but you want to replace it with some version of windows.  Which windows are you planning to use?  I think the problem may be more basic as Ubuntu/Grub don't control your BIOS and if you can't change it to boot from usb it may be a hardware problem.  Check all options under the 'Boot' menu in the BIOS.  I have several options for usb drives on my HP but only one setting will boot.  How old is this computer, have you booted with usb before.

Take a look at the link below on how to boot a windows installation medium with Grub.  The detailed explanation refers to booting it from a usb/flash drive but it should work.  It works booting from a hard drive but you will need to read carefully and do things exactly and in the proper order.  You will need a flash drive on which to put the windows extracted iso files.  I used this to boot a downloaded windows 10 iso, extracted to an ntfs partition on an internal hard drive and it booted an the install started.  Read it through a couple of times first before starting and post back if you have questions. 

[http://onetransistor.blogspot.ch/2014/09/make-bootable-windows-usb-from-ubuntu.html](http://onetransistor.blogspot.ch/2014/09/make-bootable-windows-usb-from-ubuntu.html)

The problem seems to me to be unrelated to Ubuntu/Grub but the inability of your BIOS to boot a usb and the failed DVD drive.  Have you booted from a flash/usb drive before, in other words is the machine capable?

---

### Post by RocknRollTim on 2015-08-30
Hi yancek,

Thank you for your responses to my questions, I'll follow your suggestions as well as mine to see how I get on with reinstalling Windows and won't hesitate to ask if I have got any further questions. 

Another suggestion I could try is to use KillDisk which is also a Live CD/USB in order to format the volume and to reinstall Windows.

The version of Windows I am planning to install is the original version Windows XP without Service Packs.

I've checked and amended all boot options under the BIOS in as many possible ways I can think of with resetting the BIOS after trying each option and still can't get Windows to boot both off the original CD using an external CD/DVD drive and off a USB stick with mounting the image from the original CD using the default settings in both Refus and using the Windows 7 CD/USB Tool.

The PC is a Compaq from 2003 with a brown chassis, can't remember the model number and the PC isn't onsite nor online to remotely access as I haven't put it back together yet in which I am trying to find it in Google images but with no luck, I have booted successfully with USB on other PCs that had Windows XP installed as well as PCs that didn't have Operating Systems installed using a later versions of Windows mounted on USB sticks as well as DVDs i.e. Vista and beyond but not on PCs that have got Linux installed. 

Again I have booted successfully with USB on other PCs that had Windows XP installed as well as PCs that didn't have Operating Systems installed using a later versions of Windows mounted on USB sticks as well as DVDs i.e. Vista and beyond but not on PCs that have got Linux installed. I'm aware that the BIOS hasn't been upgraded since it was purchased so maybe that's the problem? I know the hard disk boots fine in the PC as Ubuntu loads. I also forgot to mention that the battery on the Motherboard doesn't work as the BIOS keeps saying that the date and time are incorrect so maybe that's another problem too? I should be able to suss out the problem with all the options discussed and thank you for your help.

Kind regards,

RocknRollTim

---

### Post by yancek on 2015-08-30
> The version of Windows I am planning to install is the original version Windows XP without Service Packs.

Good luck with that!  I'm sure you are aware xp is not longer supported, no security updates,etc.  If you don't plan to use the internet with it then might not be problematic.

If the computer was built/purchased in 2003, it probably isn't capable of booting a usb.  Have you ever booted a flash drive from it?

Do you get any error messages when you try to boot the original xp installation CD?  If so, what?  Some windows systems don't know what to do if there is non-windows code in the master boot record and just stop.  You might try the microsoft support site or a windows forum and ask how to install windows and remove Linux.  Usually they tell you to get a Linux Live CD??  See the microsoft article at the link below:

 [https://support.microsoft.com/en-us/kb/314458](https://support.microsoft.com/en-us/kb/314458)

---

### Post by RocknRollTim on 2015-08-30
Hi yancek,

Thank you for your response, I'm aware that XP is no longer supported i.e. no security updates etc and don't plan to use it on the Internet.

Only recently I have tried booting a flash drive from it but with very little success though which is why I came to this forum for help as the PC currently has Ubuntu installed on it.

No error messages were present when trying to boot from the original XP installation CD and loads up Ubuntu, however the only error message I notice when Ubuntu loads is the one where it says it has found errors and advises you to fix them using the parameters recommended but can't remember the error message at the top of my head though, I suspect this is due to the fact that the PC wasn't cleanly shut down.

I'll follow your advice with regards to consulting the Microsoft Support site or consulting a Windows Forum for further help on how to install Windows and to remove Linux, I too suspect users will recommend using a Live CD.

Lastly I will also consider the link you posted in your last post to also help troubleshoot the issue, thank you for your help once again.

Kind regards,

RocknRollTim

---

### Post by RocknRollTim on 2015-08-30
> **yancek said:**
> You can install Grub on a usb stick but Grub is a bootloader and you can't format anything from it.  You could use pretty much any Linux system on a Live CD/flash drive to do it.  If you still have your Ubuntu install medium, you can use GParted which is on it.  Ubuntu and Grub don't have anything to do with your BIOS and don't control it and can't change it.  One thing you might check is to see if the usb you are using is actually listed under hard drives in the BIOS.  

How are you planning to install windows if you don't have a CD/DVD drive?  If you have it on a flash drive, why can't you just boot it to install windows?

 

That won't work.  Are you using the term "drive" to mean a partition or do you have multiple physical hard drives and is Ubuntu on one and windows on another?  I'm not sure why you feel you need to format the Ubuntu partitions.  The windows installation medium should be able to do that during the install.

Apologies for missing the question about the term drive, I meant a partition and not to refer to the term as having multiple physical hard drives. Also the PC has only one partition and has Ubuntu installed inside of it. I agree the Windows installation medium should have been able to perform the task of formatting the partition during the install but as it won't let me boot from the medium that is the problem I face.

---

### Post by RocknRollTim on 2015-08-30
Also the make and model of the PC I'm trying to restore back to factory defaults is a Compaq Evo D310, it took me all this time to remember, sorry about that.

---

### Post by yancek on 2015-08-30
I'm not sure if this method will work in your case but it might and it would probably be a lot easier.  Not much to be lost by trying.  I booted Ubuntu from my internal hard drive and had the entry below in the grub.cfg menu and labelled it Windows 10 Installation.  This was the windows 10  Technical Preview which I loop mounted and then copied all the extracted windows files/folders to another ntfs partition on an external drive and it booted.

> menuentry "Start Windows Installation" {
 insmod ntfs
 search --no-floppy --fs-uuid 770E690217836CBB --set root 
 chainloader +1 
 boot
}

Change the line beginning with menuentry to whatever you want, xp install.  On the third line this number will need to be replace:   770E690217836CBB 
You can find that UUID by opening a terminal in Ubuntu and running the command:  sudo blkid
You will need to know what your usb drive shows, probably sdb1 but??   You can show the partitions with:  sudo fdisk -l(Lower Case Letter L in the command)
Good luck.

---

### Post by RocknRollTim on 2015-08-31
Hi yancek,

Thank you for getting back to me with another suggestion, I'll also give this whirl and see how I get on.

Kind regards,

RocknRollTim

---

