---
title: "Secure boot questions/problems"
date: 2016-08-09
forum: General Help
---

### Post by archaeometrist on 2016-08-09
I just discovered that my Virtualbox installation was broken, and tried to fix it.  It's taken me several hours to get to where I can try to start virtual box but without the extension pack, it still won't work.  To get to this point, I had to disable secure boot.  I had a deadline last night that was compromised because virtualbox was broken - and these problems are threatening my education (and any hope I have for a future).

I'm using 14.04LTS and WILL NOT UPGRADE.  The change from 12.04 to 14.04 took me weeks to figure out and get back to the way I wanted things (as well as getting all of the software I use to work) - admittedly that was on an old system and this one is new - a Dell preloaded with 8 which took me hours to kill (trashed 8 to where it wouldn't even start - and then I could boot from a Ubuntu CD).  I am in the middle of the dissertation phase and cannot afford to have this system go down for days if not weeks, trying to get all of the different programs working again.  So I'm staying with 14.04.  I also can't have any more sudden crashes of software I regularly use!  (Everything points to Secure Boot as being the problem.)

Question #1: Why Secure Boot?
Question #2: Why should I run it if I'm not doing dual boot or anything like that - and run widely different and esoteric software packages (specialized scientific analysis and amateur radio SDR for instance) that most people don't even have any use for - some of which is a few years old?
Question #3: How can I completely remove it - and still be secure when online or working?  (I'm the only user on this computer.)

I run Virtualbox because I have some older Windows-only software that I run which isn't available under Linux (wXP, wXP SP3, W98, W95).  Otherwise, I will never use Microsoft products again (unless forced as I am now).  Thus, I should not have to deal with anything connected with that company.  I won't be doing dual boot or ever using 10.

---

### Post by grahammechanical on 2016-08-09
Secure boot is part of the motherboard's UEFI boot system program. We cannot remove it but we can turn it off. Older motherboards with a BIOS boot system do not have secure boot. Ubuntu has been compatible with secure boot from version 12.10.

If you originally set up this system with secure boot enabled I do not understand how turning secure boot off would fix this problem. Anyway, secure boot does not come from Ubuntu and it is our choice whether to keep it on or off.

As I remember, the main issue with dual booting with Windows 8 was not secure boot but having Windows 8 installed in EFI mode and Ubuntu installed in BIOS/Legacy/CSM mode. The same issue applies to dual booting with Windows 10. With UEFI boot systems every OS installed has to be installed in the same mode. And that would be either EFI mode or BIOS/Legacy/CSM mode. Ubuntu can be installed in either mode. 

[https://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](https://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

> The UEFI 2.3.1 Errata C specification (or higher) defines a protocol known as *secure boot*, which can secure the boot process by preventing the loading of drivers or OS loaders that are not [signed]("https://en.wikipedia.org/wiki/Public-key_cryptography") with an acceptable [digital signature]("https://en.wikipedia.org/wiki/Digital_signature").

Regards

---

### Post by archaeometrist on 2016-08-09
Thanks!  I don't remember how it was set up in the beginning, but I had a hell of a time getting the system to boot from a Ubuntu CD in the beginning - I didn't pay attention to it except to be angry at Windows 8 and Microsoft.  I finally killed 8 by repeatedly booting the computer and halfway through the boot, yanking the power cord.  Then when it tried to re-install 8 (because it was too corrupted), I did it a couple times more, until I got to where I could get it to run from a CD - and immediately repartitioned and reformatted the entire drive.  So the original state - unknown.  I remember when Secure Boot started showing up on this system (it rather bugged me) but it didn't seem to create a problem (I think I had it set to be turned off).  The last update did something, however... and that led to last night's panic attack.

If it's not absolutely necessary, I want no part of it.

---

