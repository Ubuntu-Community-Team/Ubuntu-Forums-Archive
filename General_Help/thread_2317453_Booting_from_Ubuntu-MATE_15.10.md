---
title: "Booting from Ubuntu-MATE 15.10"
date: 2016-03-16
forum: General Help
---

### Post by TicoJohn on 2016-03-16
I downloaded Ubuntu-MATE 15.10 so I can try it out in the LIVE mode on a NUC5i5RYH that I am soon to receive.
Do I need to make any changes in the BIOS prior to booting from the USB stick, such as;
Do I need to turn off Secure Boot ?
Do I need to set BIOS mode to Legacy or can I boot in EFI mode ?
Do I need to set the OS to Windows 8.x (if not already set) ?
Are there any other settings that I might need to adjust ?

Thanks for your assistance.

---

### Post by grahammechanical on 2016-03-16
If Windows 8.1 came pre-installed on that machine then do not set the UEFI to BIOS/Legacy/CSM mode.

With a UEFI boot system all OS have to be installed in the same mode and that is either EFI mode or BIOS mode. If we mix modes then we have trouble loading the 2 OS.

You should not need to turn off secure boot. You most likely will need to enter the UEFI boot system settings utility to set it to load from an external USB drive (memory stick).

Regards.

---

### Post by TicoJohn on 2016-03-16
There is NO OS installed so presumably I could set it to legacy mode. But would that work with the Ubuntu MATE live mode. Does the live mode even use EFI?
Since I am going to be booting from a Ubuntu MATE LIVE usb, how can the EFI settings be established for that stick? Do I have to set up a persistent memory on the stick? And, yes I understand that I have to set the BIOS to boot from the USB device.

After further investigation, using Archive manager, I see that there is an EFI folder in the .iso . Since no OS has been installed what do I set the OS to? I have heard that it should be set for Windows 8.x. Don't know if there is an option for OTHER. What about Fast Boot? Should that be turned off?

---

### Post by yancek on 2016-03-16
> There is NO OS installed so presumably I could set it to legacy mode. 

That means you have deleted or formatted your windows partition(s) so since you have nothing on the drive, you can select either UEFI or MBR.


>  Does the live mode even use EFI?

 I'm not sure what you mean by that.  It's the operating systems on the hard drives on the computer which can use or not use UEFI.  The installation media you use should give you an option to install EFI or MBR.

You don't need persistence on the flash drive.

There is an EFI folder because the files are use to install in EFI.  I'm not sure why you would want to set boot to windows since you said you have removed it from the computer.  The settings for EFI vary so much from manufacturer to manufacturer it's impossible to say.  Do you have a manual for the computer?  Otherwise you could post some info on it, who the manufacturer is and someone might be familiar with it.  You could also do an online search for the manual for the specific model of computer you have.

---

### Post by TicoJohn on 2016-03-16
Okay. First, I don't yet have the computer. It should arrive any day not. The computer is an Intel NUC5i5RYH (previously discussed in this post). Since it is not yet here I have not had a chance to look at the BIOS (I'll see if I can search Intel for info). As to selecting an OS, there is a requirement in the BIOS to set something, and I don't think Linux is an option (again, I'll look for info). I initially intend to select "Try before you install" just to see if there are any problems, so that was why I asked the question regarding EFI.

Regarding setting the OS in BIOS, I found this at Intel. "Select Windows 8.x if you plan to install Windows 8, Windows 8.1, or a Linux distribution "

---

