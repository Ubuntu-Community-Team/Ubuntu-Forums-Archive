---
title: "booting up to any computer"
date: 2015-07-28
forum: General Help
---

### Post by flipflip47 on 2015-07-28
I have a dilemma and was wondering if anyone could help.  First, I will start by giving some detail of the situation.  Then, I will ask my question in hopes that it will be easy to understand.  Ok, so here it goes:

I am currently using an usb stick, which I created an Ubuntu live usb startup disk with.  The live usb works great.  I can startup on any computer using the live usb, even on the mac computer I currently have.  No issues whatsoever, when it comes to booting up.  The issue I start to see is when I install ubuntu to that same usb stick.  I can boot up to that usb stick just fine on the computer I used to install ubuntu with.  The problem I am facing is as follows:

1- whenever I remove the usb stick, the current ubuntu install I have (on the hard drive), will not startup.  I then run boot repair, but then I cannot start up from the usb stick anymore.  I have a work around for that, so not really a big deal, but I would like it to startup using the usb stick ubuntu, when plugged, but use the hard drive ubuntu, when the flash drive is not connected.

2- when I plug the flash drive into the mac, it will not load, or boot up.  It does boot up if I have ubuntu live on it, but not the actual Ubuntu os install.


My question, is there a way to make my flash drive boot up on any computer (having installed ubuntu on it), the same a live cd/usb does, except for the option to install ubuntu?  If so, can someone point me in the right direction to get this accomplished?  Boot repair does not seem to accomplish what I want to do as it repairs the files to meet current computer's setup.  Thank you for any and all help.

---

### Post by kerry_s on 2015-07-28
when you install, select custom(something else)
in the drop down for grub make sure you select the usb stick.

---

### Post by flipflip47 on 2015-07-28
Thank you Kerry for your answer.  I tested that as well, but it did not seem to startup on a mac computer.  I will give it another shot and see if it works.  Also, that option stops my hard drive from booting to ubuntu, it boots to windows fine, though.  The grub disappears altogether.  My hard drive is setup for dual boot (windows, ubuntu).

---

### Post by oldfred on 2015-07-28
USB installer is both BIOS & UEFI.

Macs use UEFI and should be configured to boot with UEFI. But I do not know details.

Is PC UEFI or BIOS?
       Flash drive to boot in UEFI or BIOS - sudodus
[https://help.ubuntu.com/community/Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)
[https://help.ubuntu.com/community/Installation/FromUSBStick#Ubuntu_single_boot_in_UEFI_mode](https://help.ubuntu.com/community/Installation/FromUSBStick#Ubuntu_single_boot_in_UEFI_mode)
A new and so far successful attempt to create a stable portable system, that works in UEFI and BIOS mode
[URL="http://ubuntuforums.org/showthread.php?t=2213631&p=13262506#post13262506"]http://ubuntuforums.org/showthread.php?t=2213631&p=13262506#post13262506
[/URL]
 One pendrive for all PC (Intel/AMD) computers - single boot, dual boot, multi boot - sudodus
[http://ubuntuforums.org/showthread.php?t=2259682](http://ubuntuforums.org/showthread.php?t=2259682)

[URL="http://ubuntuforums.org/showthread.php?t=2213631&p=13262506#post13262506"]
[/URL]

---

### Post by flipflip47 on 2015-07-28
Thank you as well, oldfred.  It is uefi boot, I even tried install efi boot on a seperate partition on the usb stick, with no luck.  I will read all of the articles you have posted and get back to you.  I will post back and let everyone know if it works, with details on how I got it to work, or not.  Thank you again for the information.

---

### Post by oldfred on 2015-07-28
If a flash drive or any USB drive, UEFI only boots from /EFI/Boot/bootx64.efi.

But you need /EFI/ubuntu/grub.cfg which is just a configfile to your actual grub.cfg.
I have had to manually edit my configfile entry as my installs to sdb & flash drives all overwrite the ubuntu folder in my sda drive. But since grub is same version only change is the grub.cfg and the UUIDs it is telling grub in UEFI to find full install in.

Copy everything in /EFI/ubuntu on sda to efi partition on sdb (or whatever flash drive is).
Then also copy to /EFI/Boot and rename grubx64.efi or shimx64.efi to bootx64.efi.

---

