---
title: "Can't boot from USB"
date: 2016-02-25
forum: General Help
---

### Post by mike407 on 2016-02-25
I know this is kind of ironic because I'm on an Ubuntu forum. But I will get to the point. I want Ubuntu off of my computer and I have tried everything in my power to get it off. Nothing has worked. My computer refuses to boot off of the flash drive and boots into Ubuntu no matter what I do. I've used UNetBootIn and installed the windows 8.1 iso onto the flash drive and it did not work. I tried 100s of programs that make a usb stick bootable and install an iso to it, and none of them worked! I even went into my bios and set it to boot off a usb stick first and it didn't do that either. I feel like I'm stuck in an endless black hole and I can't escape. Someone PLEASE help me. I have nothing left to think about doing. :confused:

---

### Post by buzzingrobot on 2016-02-25
The selection of a drive to boot from is entirely the function of the BIOS.  You always need to set the BIOS to boot from your intended drive.

If you have a valid ISO correctly burned to a functioning undamaged USB stick and the BIOS is told to boot first from that USB stick, then it should boot the Windows installation program if all those conditions have been met. 

You might burn the image to a DVD and try booting from that.  DVD's seem, at least for me, free of some of the annoying foibles of USB sticks. 

(You don't really need to remove Ubuntu before installing Windows.  The partitioner built into the Windows installer will quite happily let you delete every Ubuntu partition. Windows will also overwrite the existing Linux bootloader, without asking.

---

### Post by Bucky Ball on 2016-02-25
Changing the BIOS to boot from USB was your first step rather than what seems like it was a last resort. If the USB is then not booting, there could be something wrong with the burn or the ISO. Legal copy of Windows?

In my last desktop, setting the BIOS to boot from USB did nothing but hitting F12 at boot and getting to a list of boot device options did. Don't ask why, don't know. You might give that a shot.

As far as I know UNetbootin doesn't work with Win ISOs. I could be wrong. You might like to try a USB creator that does or a different one. Whichever you choose, format the USB to one FAT32 partition prior to  creating the USB. If you have an unclean USB with files and cruft on it, you will possibly have issues.

PS: I have changed your thread title as this has you're not trying to boot the USB on Ubuntu. You just can't boot from USB, period.

---

### Post by mike407 on 2016-02-25
Okay. Thank you for changing. And I actually installed Ubuntu from a flash drive a while back. I went into bios and set it to boot off of the flash drive and it worked perfectly. It was already set while I was on Ubuntu, so changing the bios was my last resort, as it was already changed. I do indeed have a valid ISO and my brother's computer and my macbook will boot off of it and run it perfectly. My laptop that has Ubuntu **only** on it however, doesn't boot off of a USB **period**. Help is appreciated greatly. Thank you!

---

### Post by yancek on 2016-02-25
Did you read the unetbootin page when you downloaded it.  The quote below is directly from that page.

> UNetbootin allows you to create bootable Live USB drives for Ubuntu and other Linux distributions 

Also, ISO files for non-Linux operating systems have a different boot mechanism, so don't expect them to work either.

So as it states at the unetbootin site, you can't use unetbootin to create a bootable windows 8 usb.  You can put Grub on the usb and then extract the windows files from the iso and copy them to the drive to an ntfs formatted partition marked as active and create your own grub.cfg menu file.

I would think there would be some software designed to do this for windows and you might be better off looking at a windows forum.  I can't think of any reason why Linux developers would have any interest in creating software to install another operating system.
Do you not have a DVD drive?
How old is this laptop?  Any computer manufactured in the last ten years should be able to boot from a usb.

---

### Post by mike407 on 2016-02-26
My laptop is a fairly new model. Maybe around 2-3 years old at most. My laptop was able to boot from a usb perfectly fine before I installed Ubuntu, and UNetBootIn was not my first option. It was suggested after I tried numerous different programs. And I do think that it's very relevant on an Ubuntu forum, because my computer had no problems with this until I installed Ubuntu, so Ubuntu obviously is the problem here, not my actual computer. My USB was formatted to an NTFS partition, and I will try to reformat it and try what you suggested above and get back to you.

---

### Post by steve63752 on 2016-02-26
There are two types of 'PC's, those which have a BIOS and those which have UEFI firmware. They boot in two completely different ways.
Unetbootin only makes a USB drive that is compatible with BIOS PCs (and UEFI PCs which have Legacy\CSM support enabled).
If your laptop is the UEFI-type, then look for a 'Legacy Enabled' or 'CSM Enabled' option and a 'Secure Boot Disabled' option and 'Fast Boot Disabled' and set these options.
If your laptop does not have these options then it is either a UEFI-only version (and will only UEFI-boot), or is the older BIOS version (and should boot OK from a Unetbootin USB drive).
For more info on UEFI, see [http://www.easy2boot.com/useful-things-to-know/](http://www.easy2boot.com/useful-things-to-know/)

---

### Post by buzzingrobot on 2016-02-26
If there's a Secure Boot option in the BIOS, enable it. It's possible it was disabled to install Ubuntu. Some BIOSes also have a "Legacy" setting that disables the settings Windows 8 wants. Enable any other settings the vendor may have added to the BIOS to "enhance" Windows.

The BIOS has control of the machine when it boots.  The last thing it does is pass control to the bootloader for the OS on the drive that it's told to boot from first.  This setting is usually a cascading affair, with the BIOS moving on to other drives in order if the first does not contain a bootable OS, i.e., no bootloader.  (The bootloader's job is to boot the OS.  The BIOS stops caring once it passes control to a bootloader.) So, if a USB stick doesn't provide that, it moves on to the next drive.

---

### Post by mike407 on 2016-02-26
Yes, there is indeed a legacy option that was disabled in the BIOS. I will see what happens when I try to boot with this enabled and get back to you shortly.

---

### Post by mike407 on 2016-02-26
Well, it goes to a screen that says > A change to the operating system Secure Boot mode is pending. Please enter the pass code displayed below to complete the change. If you did not initiate this request, press the ESC key to continue without accepting the pending change

Operating system Boot Mode Change (021)

Knowing my luck, the screen is cracked EXACTLY where it shows me what to enter to complete the change. :icon_frown: I tried to hook it up to several screens and none seemed to display nothing unless I booted into Ubuntu. Does anyone by chance know what pass code you have to enter to complete the change? Or is there a setting in BIOS to turn this off? Thank you!

---

