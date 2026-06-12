---
title: "Booting one way when there is one hard drive, and another when two"
date: 2007-05-27
forum: General Help
---

### Post by Ryan Marcus on 2007-05-27
I'm in an interesting situation. I've got two hard disks in my machine, and 80 GB (secondary master) and a 20 GB (secondary slave). I've got Windows Vista on the 80 GB, and GRUB is installed on the 80. Linux is on my 20, and thus, when I start up, the GRUB on the 80 GB drive gets the menu.lst file from the 20 GB drive.

Looking back, I probably should have made the 20 GB drive the master, but I don't think I can just switch them.

My ultimate goal is to make machine show me my grub menu when both hard drives are inserted, and when I remove the 20 GB drive, to just boot right into Windows.

Right now, if I remove the 20 GB drive and try to boot, I get a GRUB error 21, which makes sense, because it can't find the menu.lst file because that hard drive is not inserted.

The reason I want my machine to do this is interesting... I run Photoshop CS3 in Vista (along with games), and I do everything else in Linux. In a normal day, I have to reboot 10 to 12 times to switch between my Linux environment and Photoshop, which is very inconvenient.

So I installed VMWare Server, and set up a VM to boot from my 80 GB drive. The grub loads, but it gives me the expected "Error 21" because VMWare did not mount my 20 GB drive.

The way I see it, I've got two solutions:

1) Redo my entire internal setup, making the 20 GB drive the master. Then, install GRUB into the 20 GB drives MBR and have it chain load the 80 GB drive when I want to boot Windows. Then, the 80 GB drive is an unmodified Windows boot. However, I'm sure there are quiet a few issues that could occur from making my 20 the master and the 80 the slave... like the fact that I've already GRUB into the MBR. I'd rather not.

2) Use the Windows Bootloader (I am told there is one) and chain load Linux every time I want to boot it. Then, when the 80 GB drive boots in VMWare without the 20 GB drive, the Windows Bootloader will automatically boot Windows (I hope.) The only problem is, I've already loaded GRUB into the MBR, and I don't know anything about the WIndows boot loader.

3) Find a way to get GRUB to boot into the hard drive it is on even if it can't find a menu.lst file.

Any help would be great.

---

### Post by rillip on 2007-05-27
There's a much easier setup.  Install grub on the 20 and have it point to the 20 menu.lst.

Unplug the 20, use fxmbr and fixboot to restore Vista as the default loader on the 80.

Most BIOS's allow you to chose your HDD boot order.  Simply chose the 20 first and the 80 second.  20 is there, it boots grub.  20 isn't there, it boots the 80 with Window's Bootloader.

Edit: You know, thinking about it some more, why don't you just set grub to load, and add Vista to the menu.lst?  Then you can... you know, just choose, and not unplug HDD and such?

---

### Post by Ryan Marcus on 2007-05-27
Thanks for the reply, that makes more sense, assuming my P4PE is going to let me modify the boot list to that extent. I don't see why not, though.

Is there anything I should know about fixmbr and fixboot, or can I figure it out from the man page?

> 
Edit: You know, thinking about it some more, why don't you just set grub to load, and add Vista to the menu.lst? Then you can... you know, just choose, and not unplug HDD and such?

Because I can't mount both of them in VMWare.

---

