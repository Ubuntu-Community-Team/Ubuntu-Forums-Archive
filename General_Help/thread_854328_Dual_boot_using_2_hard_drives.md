---
title: "Dual boot using 2 hard drives?"
date: 2008-07-09
forum: General Help
---

### Post by timmyjoe42 on 2008-07-09
I tried a search and couldn't find anything exactly like I want to try.

I have a pc that I want to set up to dual boot. I have 2 hard drives each having it's own operating system that I can swap out if I need.  I'd like to leave them both in and set it up to dual boot.  One hard drive has ubuntu in it and the other has Windows 2K Pro.

Do I simply set up the ubuntu drive as the slave and edit the boot.ini file in windows?
If so, how do I edit the .ini file?

---

### Post by T2manner on 2008-07-09
I'm not sure what you mean by set it up as a slave, but I also have 2 hdd's and one with Ubuntu and one with XP.

I just select which one I want to boot into when the Grub menu pops up.

---

### Post by highonv8splash on 2008-07-09
should be as easy as having them both connecting on editing your /boot/grub/menu.lst file to make sure both of the OS's are listed there. There's a lot of good guides on google on how to setup another operating system in the file.

---

### Post by werries on 2008-07-09
the only thing you need to do is make sure GRUB is installed on the harddrive that your BIOS boots first. So essentially, the master harddrive.

---

### Post by timzak on 2008-07-09
Here is an alternate method I used to use when I dual-booted.  Your motherboard's system BIOS must have a boot menu option for this to work.

1) install Win2k on the hard drive you prefer.  Make sure no other hard drives are plugged into the motherboard.
2) unplug Win2k hard drive; plug in Ubuntu hard drive, then install Ubuntu.
3) enter system BIOS and set Ubuntu hard drive as 1st in boot order.

Now, when you turn your computer on, it boots into Ubuntu by default.  If you want to boot into Win2k, simply hit the function key that accesses your motherboard's boot menu.  On my system it is F11.  So when I turned my computer on, I hit F11 and selected the hard drive with Win2k on it and it automatically loaded up Windows.

Hope this helps you out.

Regards.

---

### Post by Titan8990 on 2008-07-09
The above post sounds more complicated then just letting GRUB handle it.

---

### Post by timzak on 2008-07-09
> **Titan8990 said:**
> The above post sounds more complicated then just letting GRUB handle it.

It might be less complicated to someone who is unfamiliar with modifying grub.  Just presenting as another option.

---

### Post by Titan8990 on 2008-07-09
> It might be less complicated to someone who is unfamiliar with modifying grub. Just presenting as another option.

Yes, but people need to get their feet wet sometime.

---

### Post by timmyjoe42 on 2008-07-10
What is GRUB?

Can I install it on the Windows 2K hard drive?  I want that to be primary or the default operating system and have Ubuntu as an option so I can experiment with it in my free time.

---

### Post by confused57 on 2008-07-10
Here's how I have 2 of my pc's set up:
[http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot](http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot)

---

### Post by Titan8990 on 2008-07-10
GRUB stands for Grand Unified Bootloader. It will boot virtually any OS. Whenever you install Ubuntu it uses GRUB to boot. It can also boot your Windows OS most of the time without even changing settings.

---

### Post by Dragonbite on 2010-01-04
> **timzak said:**
> Here is an alternate method I used to use when I dual-booted.  Your motherboard's system BIOS must have a boot menu option for this to work.

1) install Win2k on the hard drive you prefer.  Make sure no other hard drives are plugged into the motherboard.
2) unplug Win2k hard drive; plug in Ubuntu hard drive, then install Ubuntu.
3) enter system BIOS and set Ubuntu hard drive as 1st in boot order.

Now, when you turn your computer on, it boots into Ubuntu by default.  If you want to boot into Win2k, simply hit the function key that accesses your motherboard's boot menu.  On my system it is F11.  So when I turned my computer on, I hit F11 and selected the hard drive with Win2k on it and it automatically loaded up Windows.

Hope this helps you out.

Regards.

I'm going to be doing something similar with my system. I will have one hard drive with Windows 7 (hda) and another with Ubuntu (hdb).

I am planning on setting the BIOS to boot from the Ubuntu (hdb) hard drive first, followed by the Windows (hda) second.  This way, if the Ubuntu (hdb) hard drive is removed, it will boot to Windows without missing a beat.  Likewise, if the Windows (hda) hard drive is removed, the system boots to Ubuntu's GRUB (on hdb) and everything is fine unless I select the Windows option.

In Ubuntu I am hoping to edit the GRUB listing to point include the Windows(hda) after the install.  I am probably going to install Ubuntu on the (hdb) first and start setting everything up before getting Windows 7 installed.

Between the new GRUB, and Windows 7 changes, what and how do I enter into the GRUB menu a listing for Windows 7?

---

