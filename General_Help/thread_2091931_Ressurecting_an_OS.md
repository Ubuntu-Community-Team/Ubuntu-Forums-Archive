---
title: "Ressurecting an OS"
date: 2012-12-06
forum: General Help
---

### Post by Sirius3 on 2012-12-06
I have a windows 7 HDD/OS that I've been working on repairing from a BSOD. I have fixed the bad sectors and made the file system recognizable with testdisk. The HDD was previously unmountable and the windows 7 OS, instead of being listed as OS, was listed as "Unknown" which test disk has also fixed. Now, how do I format the other partitions so that it boots properly into the fixed windows 7 OS partition? 

Here is what I'm looking at 



[IMG]http://i.imgur.com/Eeg4J.png[/IMG]




and here is the only HDD (with a working OS) I have for comparison. 



  [IMG]http://i.imgur.com/y3w4Y.png[/IMG]



Note that it is linux, so it may be different from how windows 7 partitions are set up.

I believe the original partitions were overwritten for recovery purposes. How should I format "Dell Utility and "RECOVERY" so that my windows 7 boots properly?

I know it's possible to do this. Please refrain from suggesting "Forget it. Just recover data, wipe, and reinstall OS". That's lazy. 

Thank you in advance.

---

### Post by lildigiman on 2012-12-06
That's spam (Never seen it here though haha).

As for your question, I think you must be using GRUB as your bootloader to load both windows 7 and Ubuntu linux. What happens when you boot up your computer? Does it just go straight to Ubuntu?

---

### Post by Sirius3 on 2012-12-06
> **lildigiman said:**
> That's spam (Never seen it here though haha).

As for your question, I think you must be using GRUB as your bootloader to load both windows 7 and Ubuntu linux. What happens when you boot up your computer? Does it just go straight to Ubuntu?

How do I set grub as my bootloader? 

When I start up my computer if I set it to boot from the External USB HDD it would go straight to unbuntu (that's where Unbuntu's OS is located).  The Internal HDDs are windows 7. One disk is the OS and the other is a non OS memory disk. I think I set the wrong partition as bootable (using Unbuntu's "disks" program), so it skips my system drive and goes straight to non system drive. The non system drive just brings up a blank window with blinking hyphen in the corner (I think that's normal for non system drives though.)

I'm trying to figure out how to format the partitions on my window OS drive, and which ones should be set as bootable. How are working windows 7 HDDs partitioned and which partitions are flagged as bootable? If I know this than I believe my windows 7 OS will boot properly again.

---

### Post by oldfred on 2012-12-06
If you can boot Ubuntu just install this, or download a full repair CD and use that. Run just the BootInfo report and post link it gives you.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by lildigiman on 2012-12-06
oldfred beat me to it.

If you're familiar with GParted, it may be as simple as setting your Windows 7 partition with the Bootable Flag. Google can be your friend here.

I should also mention that your choice of words is not the best: 'Formatting' your drive will delete everything on that drive!

Hopefully those BootRepair CD's that oldfred posted will be what you need to solve your problem.

---

### Post by Sirius3 on 2012-12-06
Here is a simple way to answer my question...

Will anyone with a working (and bootable) windows 7 HDD, use Unbuntu's app "Disks" to highlight it, take a screenshot, and upload it here like I have done here with my disks? It would be very much appreciated. 

Thank you. :p

---

### Post by Sirius3 on 2012-12-06
> **oldfred said:**
> If you can boot Ubuntu just install this, or download a full repair CD and use that. Run just the BootInfo report and post link it gives you.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

But those tools are for Unbuntu though right?  It's not the Unbuntu OS that is having the problem.

---

### Post by lildigiman on 2012-12-06
> **Sirius3 said:**
> Here is a simple way to answer my question...

Will anyone with a working (and bootable) windows 7 HDD, use Unbuntu's app "Disks" to highlight it, take a screenshot, and upload it here like I have done here with my disks? It would be very much appreciated. 

Thank you. :p

Unfortunately a screenshot of Disks isn't going to show you how your computer should boot up, simply put.

---

### Post by Sirius3 on 2012-12-06
> **lildigiman said:**
> Unfortunately a screenshot of Disks isn't going to show you how your computer should boot up, simply put.

So restoring everything is a strictly rigid process and not flexible to alternative methods? I have all my data backed up. I'm not afraid of messing it up. I just want to try it my way. If it doesn't work then I will reformat, reinstall the OS, and start over.

---

### Post by lildigiman on 2012-12-06
Okay, that's good that you've backed things up. I used to have Windows 7 and Ubuntu installed on separate hard drives with a dual boot. The GRUB bootloader is what instructs the computer which drive to boot off of. Disk formatting inside of Disks can only manipulate the disks formatting and partition sizes.

A windows 7 installation disk has the ability to repair the master boot record if it has been corrupted or overwritten by grub

---

### Post by grahammechanical on 2012-12-06
This is what concerns me about your first post:

> Now, how do I format the other partitions so that it boots properly into the fixed windows 7 OS partition? 

If you format any partition you will loose all data (including an OS) that is on it. But if you want to do it your way and if you only want Windows 7 on that hard disk, then by all means just re-install Windows 7.

If its not booting properly then may be a re-install is the only answer. But without knowledge of the error messages that you get when trying to load Windows 7 and knowledge of any other OS that you may or may not have. I do not think that it would be wise to give you exact advice.

---

### Post by oldfred on 2012-12-06
Boot-Repair can fix booting of Windows if it is just a boot issue. Otherwise you may need the Windows repairCD to run chkdsk or other Windows repairs.

Did you make this when Windows was working or do you have access to another Windows install. It just has to be either 32 or 64 bit to match yours.

       Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

    Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)
Windows 8 UEFI repair USB must be FAT32
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)

---

