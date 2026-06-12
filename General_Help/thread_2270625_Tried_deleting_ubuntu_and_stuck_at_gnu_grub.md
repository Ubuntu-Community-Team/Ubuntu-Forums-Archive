---
title: "Tried deleting ubuntu and stuck at gnu grub"
date: 2015-03-24
forum: General Help
---

### Post by StarFawks_ on 2015-03-24
Hello, I'm a noob to ubuntu, was able to install and get my duel boot running with Windows 8.1 and Ubuntu 14.04.  I deleted ubuntu from my partition, expanded the rest of my windows memory, and tried to boot and now I'm stuck at the gnu grub screen. Have looked around on 50+ pages and can't find a solution that works. I have a Windows recovery on a USB, new to ubuntu so don't know commands really. Please help! Thanks!

---

### Post by yancek on 2015-03-24
If you installed both using MBR to boot and were using the Grub bootloader from Ubuntu to boot that would be easily explained.  windows 8 usually does UEFI installs so that would not apply.  If you could boot the Ubuntu CD/DVD and go to the site below and download and run the boot repair script, select the option to Create Bootinfo Summary and post it here, someone should be able to suggest options to your.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by StarFawks_ on 2015-03-24
I don't have ubuntu on a cd/dvd, I think I have it on a hard drive but can't loose any of the data on it

---

### Post by yancek on 2015-03-24
What did you use to get Ubuntu on the hard drive?  You needed a DVD or flash drive to do that.
You forgot to post the boot repair info.  Without that, there's not much anyone can do to help.

---

### Post by Vladlenin5000 on 2015-03-24
I see where this is going and it's not good...

@yancek - the OP *supposedly* already removed the partitions where Ubuntu resided and don't want to have it back.
If that's really the case what needs to be done is boot the **Windows **installation media and follow the instruction on how to repair the already installed Windows. Bottom line: Windows tools, Windows troubleshooting and... Windows **forum**!!!

---

### Post by StarFawks_ on 2015-03-24
@yancek  used the hard drive I have, but not sure if it will delete all the data on it when I try and use it in this situation, and sorry about the boot info, wasn't sure how to get it, like I said I'm a noob with ubuntu. At this point I don't care if I'm running ubuntu and Windows. As long as I can get my computer running again.

---

### Post by Vladlenin5000 on 2015-03-24
Noobs shouldn't be deleting partitions, just sayin'... That's how bad things happen and those may or may not be easy to correct. 
Right now you must decide what you want to do because the instructions/suggestions are way different, depending on what operating systems you want to have. I suppose you want Windows only, why would you take the time and effort to delete the partitions otherwise? If so, my previous post -#5- already mentioned what you need to do to get back the Windows bootloader and that bootloader only... Then, in a regular Windows section and using Windows native tools only you can manage the now unallocated space where the deleted partitions were.
If this ISN'T what you want please explain clearly what you really want to do.

---

### Post by oldfred on 2015-03-24
You really need to know if your Windows is BIOS or UEFI.
And if UEFI, you should be able to just go into UEFI and choose to boot Windows and reset that as new default.
If BIOS you need to install a Windows boot loader to the MBR to overwrite grub. That is the fixMBR command in your Windows repair flash drive.

All Windows since Vista use same configuration and even XP used essentially the same MBR boot loader if your Windows 8 is BIOS.

If UEFI
 Windows 8 UEFI fixes
[http://superuser.com/questions/460762/how-can-i-repair-the-windows-8-efi-bootloader](http://superuser.com/questions/460762/how-can-i-repair-the-windows-8-efi-bootloader)

If BIOS this would be the same for Windows 8

 Restore MBR for win7
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)


 [http://www.eightforums.com/](http://www.eightforums.com/)

---

### Post by yancek on 2015-03-24
> the OP *supposedly* already removed the partitions where Ubuntu resided and don't want to have it back.

I was a ware of that and was suggesting he use whatever medium he used to install Ubuntu to get the boot repair software to post some info.  Also, if he does only want windows then using the windows installation medium would be the way to go, if he has it?  If it is a UEFI machine, I don't know why he is having the problem since he should be able to make the adjustment suggested by oldfred.

---

### Post by StarFawks_ on 2015-03-24
@oldfred pretty sure it's bios because I am stuck at gnu grub, cannot get to anything else no matter what I try. I have my recovery drive on a USB, but don't know how to change mbr from gnu grub. @yancek I have the ubuntu software on a portable hard drive, but don't know how to boot it from gnu grub, and if I am able to will it delete everything else on the drive?

---

### Post by oldfred on 2015-03-24
Whether BIOS or UEFI you should be able to get into system with system key (see owners manual often f2 or del key) and select to boot recovery drive or USB drive, if it is correctly configured as a bootable repair drive.

If you are going to be a Windows user you need to know how to repair it regularly.

---

### Post by StarFawks_ on 2015-03-24
Got everything figured out, thanks everyone

---

