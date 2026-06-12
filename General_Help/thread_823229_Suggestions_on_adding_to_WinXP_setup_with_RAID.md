---
title: "Suggestions on adding to WinXP setup with RAID"
date: 2008-06-09
forum: General Help
---

### Post by theedudenator on 2008-06-09
I have a single harddrive with WinXP on it.
I own partition magic, so I can resize and make room for Ubuntu on this drive.

My programs drive for windows is RAID 0.  I really want to hide this drive from Ubuntu so I do not cause problems.

Any suggestions?

---

### Post by Titan8990 on 2008-06-09
If it is a software or fakeRAID then there is a good chance you will not be able to see it anyways. If you are not installing Ubuntu on the same drive (I hope you are not thinking about rezizing an already unreliable RAID set) then the RAIDED drive will not mount automatically if you dont specify it a mount point during installation or later.

---

### Post by fjgaude on 2008-06-09
RAID 0 requires normally at least two drives. You say you have only one drive?

---

### Post by theedudenator on 2008-06-09
Sorry...  Let me clarify

1st drive is C: for windows
I will resize and add a partition for Ubuntu

2nd drive(s) are D:
This is 2 drives in RAID 0  - this is my programs drive

3rd drive is Swap and working data for D:
Will resize to add Ubuntu swap also

4th Drive is mirror of RAID (0)

5th Drive is data back-up

---

### Post by fjgaude on 2008-06-09
Okay, how are you going to create the raid0 array? Using **mdadm** or in your **BIOS** and then using **dmraid** to see the array in Ubuntu?

---

### Post by theedudenator on 2008-06-09
I am not worried about the RAID because I do not want/need to see it in Ubuntu.  So it should be ok.

I tried to install Ubuntu today and nothing went well.
At the boot menu I got the "beyound 1024 cylinder BIOS limit)

I have no clue what went wrong...
I think it might be my 1st harddrive is actually external

1st harddrive (External)
2nd harddrive
  50meg as boot - this is where I said to put the bootmanager
  35gig (WinXP)
  35gig ext3 (Ubuntu)

---

### Post by fjgaude on 2008-06-09
I'm having troubles understanding why and what you are wishing to do. What is the raid for, how to be used?

To install Ubuntu, you are using the LiveCD?

Is your BIOS pointing to the drive from which you intend to boot?

---

### Post by theedudenator on 2008-06-09
The RAID drive is for windows only, I just don't want ubuntu to use it for anything.

I now had to reinstall windows on the C: drive.
It works and boots fine again.

So what I have to work with.

30meg blank - for bootmanager??
35gig WinXP64
35gig blank - for Ubuntu

I have the live CD to install from. 
But obviously I did something wrong.

In the partitioner for Ubuntu how should I set each drive?

---

### Post by theedudenator on 2008-06-09
Should I install GRUB before and make sure it works with windows before I try to install ubuntu?

---

### Post by theedudenator on 2008-06-09
Is this something I should follow to setup dual boot?

[http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html?page=3](http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html?page=3)

---

### Post by fjgaude on 2008-06-09
After you install Windows on the raid, and it is working fine, you can install Ubuntu using the LiveCD on the other drive... you will then be able to boot either Ubuntu or Windows from grub which is automatically installed when you install Ubuntu. The LiveCD takes care of swap and the like, just go slow so you understand what you are doing.

The link you gave shows how to boot from Windows... most folks don't do that; I've never.

The only thing is to install Windows first. Then use the LiveCD.

---

### Post by theedudenator on 2008-06-09
I installed WinXP64 and it works fine.

I then installed Ubuntu with GRUB on the first partition.
When I rebooted I only get the windows boot manager.

So this is what I think I did

Disk1
30meg GRUB?
35gig WinXP64
35gig Ubuntu


Do I need to make GRUB active?
Did I need to install GRUB in the first 30meg partition?
Or could I have installed it in my 35gig Ubuntu?

I am not sure where to put it at, and I don't want to mess with the windows MBR

---

### Post by fjgaude on 2008-06-10
Go to msg #10, your posted link, and follow that. I've never done what you are doing... the Windows MBR is something that always goes with grub taking over, the way it's usually done. But be my guest... do it your way. Good luck.

---

### Post by theedudenator on 2008-06-10
I have no problem losing Windows MBR.

But anyway... I did it my way and it seems ok.


Grub now loads at boot time and I have the option to boot Ubuntu or  WinXP64.

Thanks everyone for the help!

---

