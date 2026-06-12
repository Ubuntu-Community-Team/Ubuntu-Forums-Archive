---
title: "Win Boot Loader won't start XP after selecting it from GRUB"
date: 2015-02-28
forum: General Help
---

### Post by Stephen_H on 2015-02-28
Hello,

Let me start off by saying I'm new to Ubuntu and the Forum, and I really appreciate any help.

PROBLEM: I installed Ubuntu and GRUB on a second hard drive, leaving the original with Win XP untouched. I switched the HDD info cables so that the drive with GRUB was the default boot drive on start up. **When I select Windows XP in GRUB, it takes me to the Windows boot loader like it should. But when I select to boot to XP in Win Boot Loader, the computer restarts.** Now, if I disable the second drive with Ubuntu on it, the machine boots into Windows XP just fine. 

Any Ideas?  Thanks.

---

### Post by yancek on 2015-02-28
Once you select xp from the Grub menu. neither Linux/Ubuntu or Grub are involved so the problem is windows only.  Most likely because you have windows on the second drive.  You need to map the boot entry in Grub so the windows bootloader thinks it is on the first drive, not something ordinarily done by beginners, change the windows drive to the frist drive or install Grub to the windows drive MBR and update-grub from Ubuntu.

---

### Post by Stephen_H on 2015-02-28
Thanks for the reply yancek. I did try editing the Windows boot.ini file so that the default boot disk is the second one. This didn't seem to work (it just made it so that I couldn't boot into windows at all until I went back and changed it through Ubuntu), although maybe I did it wrong. The red text is what I changed (from 0 to 1):

[boot loader]
timeout=30
default=multi(0)disk([COLOR=#ff0000]1[/COLOR])rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk([COLOR=#ff0000]1[/COLOR])rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect

It looks like you can also add an operating system ([http://support.microsoft.com/kb/289022](http://support.microsoft.com/kb/289022)). Could I add my Ubuntu OS with the disk and partition info? Maybe I'm not even close here but I thought maybe I was on to something. Again, thanks.

---

### Post by oldfred on 2015-02-28
Best to change Windows drive back to sda or first drive in BIOS.
Can you from BIOS directly boot sdb drive? Most can, a few cannot.

The actual entry is the rdisk one, but BIOS reports drive to operating system as 0 or 1. 

But boot drive is always 0, so it makes a big difference on grub entries and whether it is correctly remapping drives with its map device command, which drive you boot from and then the drive numbers in boot.ini. With multiple drives they all have to be correct. 

Often then easier just to have Windows as first drive as that is what it usually expects.

---

### Post by Stephen_H on 2015-03-01
Yeah, that's my problem oldfred. My BIOS doesn't actually list the two hard drives separately. Otherwise, I think I could just keep the Windows drive in slot 1 but have it boot to the second drive first which would (I think) fix the problem. Back to the boot.ini though, are you saying if I changed rdisk it should boot correctly?

Also, I was looking at EasyBCD. I tried using it and putting an Ubuntu entry on windows bootloader but it gave me an error when I tried to boot into it. I'm guessing because it's on the second hard drive and not mapped correctly. Any ideas about how I would go about using EasyBCD to put GRUB on the windows boot loader and have it boot into Ubuntu on my second HDD?

---

### Post by oldfred on 2015-03-01
Do not know about EasyBCD but it does not work with XP as XP has boot.ini not  a BCD like Vista or later.

Still easier to make Windows sda, and then once you get Windows booting, install grub to the MBR of sda. Then you should be able to boot both.

---

### Post by Stephen_H on 2015-03-01
How would I install GRUB to the sda MBR? Also, would this erase windows boot loader?

---

### Post by Mark Phelps on 2015-03-01
IF you switched the boot drives AFTER you installed GRUB, then you need to do the following:
1) Keep booting from the Linux drive
2) Boot into Ubuntu, open a terminal, and enter "sudo update-grub".  This will regenerate the GRUB configuraration file.
3) You should see it find Windows boot loader
4) When done, you should then be able to reboot and then select Windows without a problem.

---

### Post by Stephen_H on 2015-03-01
Hey Mark. Unfortunately, that didn't work but I appreciate the response. And yes, I did switch the boot drives after I installed ubuntu on the second hard drive (as well as grub). I'll leave this thread open a while longer but if I can't figure it out within a day or so, I'll just close it. I can always just turn off the first drive and switch between OS's that way (a pain, but better than screwing something up). 

Any other ideas would be greatly appreciated though. Thanks guys.

---

### Post by oldfred on 2015-03-01
If booted into Ubuntu you can install grub to any MBR. It will erase the Windows boot loader, but you should be able to restore a Windows boot loader if needed with either Linux tools or your Windows repair/install disk.

       sudo grub-install /dev/sda
Can be any drive, sda, sdb, sdc and they in BIOS select to boot that drive.

      
 How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

---

### Post by Stephen_H on 2015-03-01
Oh okay, that's actually pretty easy then. I've restored win boot loader before w/the repair tool so I'm not terribly worried about it. I'll try that, thanks oldfred.

---

### Post by Stephen_H on 2015-03-01
woops, didn't mean to post again. My bad.

---

