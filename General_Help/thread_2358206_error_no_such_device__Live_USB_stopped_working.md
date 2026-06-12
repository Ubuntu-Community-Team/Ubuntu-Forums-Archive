---
title: "error: no such device / Live USB stopped working"
date: 2017-04-10
forum: General Help
---

### Post by finchyy on 2017-04-10
I know this sort of error message has been posted on here a lot, and I have honestly gone through as many as I could. I would do anything to get this fixed and I'd be incredibly grateful for your  advice

Due to these issues, I'm currently restricted to my phone, so please forgive lack of technical detail. From the start then:

I placed a Ubuntu ISO onto a USB stick and booted from it with only my C:/ drive in my PC (a 120GB Samsung SSD).

The installation went just fine and it restarted. I got a black screen, and discovered that it was something to do with nomodeset. I tried running Ubuntu from the SSD with nomodeset, but it didn't work.

I eventually found a way to get it to work by starting Ubuntu in recovery mode and reinstalling grub via the options listed. Once inside Ubuntu, I installed the NVidia proprietary drivers and restarted.

When I restarted, I was greeted with the "error: no such device: 00371400-xxxx-xxxx-etcetera" error in the grub rescue menu. I looked the problem up and discovered I should try running from the USB stick to access the terminal. However, when I attempted to boot from the USB stick, I get exactly the same error message.

Additionally, the USB stick used to say "Ubuntu" but now just says "Kingston" (the brand of the stick).

I have absolutely no idea what to do. I plugged the USB stick into another laptop and it claims to have only 500MB in space of total, though it has a 13GB healthy partition (which, presumably, has Ubuntu on it), so I don't know if that's the issue.

In addition, my boot options are a bit insane. Instead of it being just "SSD" and "USB", it's flooded with "UEFI OS (114473MB)".

Given that I have no other operating system discs on me and I only have the one USB stick, I'd really like some advice. Ideally, I want to format the drive and reinstall Ubuntu on it, but I don't know how to do that from the grub rescue menu, if that's even possible.

Thanks in advance,

~Jordan

Edit: Interestingly, when I try to boot from one of the "UEFI OS" drives, it goes to a "GNU GRUB" menu

Edit #2: Also, typing "insmod normal" in grub rescue under any scenario brings up "unknown filesystem", which is scary

Edit #3: Here is a picture of what my boot options screen looks like. There is only an SSD and a USB stick connected. [http://imgur.com/NQMqcU3](http://imgur.com/NQMqcU3)

Edit #4: I think the main issue here is that it no longer boots Ubuntu from the USB stick. Would it be safe for me to delete the volumes on the USB stick in order to format it?

---

### Post by yancek on 2017-04-10
You have a 120GB SSD with windows on it, correct?  You have a Kingston usb on which you put Ubuntu to boot so, how exactly did you do that?  Which software did you use to create a bootable Ubuntu flash dirve?  Also, where were you trying to install Ubuntu, on the SSD with windows?  Your BIOS boot options indicate UEFI.  Which version of windows is it?  If it is 8 or 10 then it is probably installed UEFI and you would need to boot and install Ubuntu UEFI or it would not be bootable.  The link below to the official Ubuntu documentation gives a detailed explanation of it.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Read through it and see if you followed the correct steps to install Ubuntu UEFI.

The 'no such device' error means it is looking for a specific partition by UUID and it doesn't exist. 

> 
I have absolutely no idea what to do. I plugged the USB stick into  another laptop and it claims to have only 500MB in space of total,  though it has a 13GB healthy partition (which, presumably, has Ubuntu on  it),

What operating system was on that computer?  windows won't accurately display info on Linux filesystems.  You indicate earlier you tried to boot Ubuntu from the SSD so where exactly did you try to install it, the SSD or another usb drive?  The flash drive with the bootable Ubuntu installer on it would not take up much more than 1GB.

Formatting from Grub is not possible, it's just a bootloader.  What can you boot, if anything?

---

### Post by finchyy on 2017-04-11
> **yancek said:**
> You have a 120GB SSD with windows on it, correct?  You have a Kingston usb on which you put Ubuntu to boot so, how exactly did you do that?  Which software did you use to create a bootable Ubuntu flash dirve?  Also, where were you trying to install Ubuntu, on the SSD with windows?  Your BIOS boot options indicate UEFI.  Which version of windows is it?

I installed the Ubuntu iso onto the USB stick on Windows 10 (which was on my SSD) using Rufus.

> What operating system was on that computer?  windows won't accurately display info on Linux filesystems.  You indicate earlier you tried to boot Ubuntu from the SSD so where exactly did you try to install it, the SSD or another usb drive?  The flash drive with the bootable Ubuntu installer on it would not take up much more than 1GB.

I checked the USB stick on a Windows 8.1 laptop. I installed Ubuntu from the USB to my SSD in an attempt to overwrite Windows.

> Formatting from Grub is not possible, it's just a bootloader.  What can you boot, if anything?

I can attempt to boot from all options (though there is only actually one SSD in the system, which is odd) listed in the image I linked, but it only shows grub rescue or another grub screen with "minimal bash commands" and a "grub>" input.

Thanks for your reply, I'll look through the information provided for sure!

---

### Post by finchyy on 2017-04-11
> **yancek said:**
> https://help.ubuntu.com/community/UEFI[/url]

Read through it and see if you followed the correct steps to install Ubuntu UEFI.


I just read through the documentation and it appears that I have done so, as the USB stick shows one folder, "EFI" when I plug it in to my laptop.

---

### Post by yancek on 2017-04-11
> I just read through the documentation and it appears that I have done  so, as the USB stick shows one folder, "EFI" when I plug it in to my  laptop. 		

Well, that's the installation media so it doesn't matter.  If you installed on the SSD, you should see an EFI partition there which would have had windows EFI files under a Microsoft directory.  Installing Ubuntu UEFI to the SSD should have created another directory on that partition in which the Ubuntu Grub boot files would have been placed.  Can you boot the Ubuntu installation usb?  If so, go to the site below while booted to it and download and run the boot repair as instructed there.  Make sure you just select the option to Create BootInfo Summary.  When it finishes, it will give you a link which you can post here and it will provide details on the system and someone should be able to help.

  [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by finchyy on 2017-04-11
> **yancek said:**
> Can you boot the Ubuntu installation usb?

I've made a new USB with the Ubuntu installation on it. However, when i try to boot from it, the screen shows a purple screen, a blinking cursor, then goes black and the monitor goes into power saving mode.

Edit: Never mind, fixed that. I'll follow your advice given

---

### Post by finchyy on 2017-04-11
Here is the information provided by Boot-Repair:

[http://paste2.org/3mZjp0UN](http://paste2.org/3mZjp0UN)

Any help would be greatly appreciated :)

---

### Post by yancek on 2017-04-11
Your boot repair output shows you have two drives.  One is shown as a 111.8GB drive and the other is a 14.3.GB drive.  The second shows that it has Ubuntu on it and this is the installation usb.  You didn't install Ubuntu anywhere.  The larger drive shows only two partitions and both are windows (ntfs) partitions and they take up the entire SSD so there is no where to install Ubuntu.  If you want to install Ubuntu to the SSD, you need to get into windows and shrink the larger partition to make room for it.

I don't see any sign of an EFI partition on the SSD, no files for windows or Ubuntu and the only sign of anything Linux/Ubuntu is the Grub code in the MBR, none of the boot files needed to boot are on any Ubuntu partition because there is no Ubuntu partition.

If you can't boot windows but have a windows installation DVD, you can boot that and use the commands to reinstall windows code to the MBR to enable it to boot and shrink the largest windows partition.  If you can't boot windows and don't have the installation DVD, your options are more limited.  You can borrow a DVD from someone but it need to be the same release and version of windows or you can boot the usb with Ubuntu on it and shrink the windows partition and reinstall Ubuntu as an MBR install which is what your windows is.  The latter option is basically a last resort.  It will probably work but doing this type of thing to a windows partition is always better done with windows.

---

### Post by finchyy on 2017-04-11
I'm pleased to announce that I have solved the issue :) 

I bought a new USB stick, whacked Windows 10 on it and formatted the SSD and re-installed it. I then installed Ubuntu alongside it following this guide: [http://www.everydaylinuxuser.com/2015/11/how-to-install-ubuntu-linux-alongside.html](http://www.everydaylinuxuser.com/2015/11/how-to-install-ubuntu-linux-alongside.html)

The only "issues" I have now are lack of surround sound for my headset - which I don't think is solvable - and a buttload of "UEFI OS" labels on the list of boot options in my BIOS for some reason.

Thanks for your help, I really appreciate it! :)

~Jordan

(From Ubuntu!)

---

