---
title: "Can't boot Ubuntu installer"
date: 2023-07-20
forum: General Help
---

### Post by douzep on 2023-07-20
Hello guys,

I'm trying to install Ubuntu for school on my computer (HP Pavilion 15-eg0xxx) but I can't figure out the installation. I don't have any USB or External Drive to mount the ubuntu ISO on so I tried first with unetbootin. At restart it shows me the option to boot Windows 10 or Unetbootin, and when I load Unetbootin I get an error with the file \ubnldr.mbr state 0xc000007b. I couldn't figure anything about that so I tried another tutorial using Universal usb installer.
I managed to make a partition of my disk upon which I mounted the ISO of the version of ubuntu I downloaded (23.04) but I can't find the booting option in the booting menu of my computer.
It only proposes to boot from OS Boot Manager (UEFI) - Windows boot manager (...) or from  and EFI File. I have browsed a bit around in the EFI file option but couldn't make sense of what it was so I didn't dig too deep afraid of making a mistake. If anyone can help me go through the process of installing ubuntu on my device withtout using an external device it would help me a lot !

Thanks in advance :)

---

### Post by MAFoElffen on 2023-07-20
Why?

That laptop has 2 USB-A and 1 USB-C ports. Why are you not using a flash drive? (which is easy to burn the ISO to with Rufus...)

Why are you using Ubuntu 23.04, which is an interim release that would need to be upgraded every 6 months, instead of a Long Term Stable (LTS) of 22.04.2?

After burning the image to the USB Flash drive, 

Then start up Windows and use the Disk managemnet application to shrink a partition to give room for your install. Then go to settings to tell it to reboot into "Safe Mode". When it goes to reboot, go into the UEFI BIOS setting to disable SecureBoot, then check the SATA Mode. If it is set to "RAID", change it to "AHCI", then save and continue the boot. Let windows start up in "Safe Mode". You don't need to do anything there (just let it boot into it). Doing that in that mode, it will see that the setting has changed to AHCI and load the correct drivers for that. Exit / Restart.

Press F12 to load the boot menu and boot from the USB drive...

---

### Post by yancek on 2023-07-21
Windows will not boot a non-windows OS on a UEFI machine.  The error indicates it is a Legacy installer option so I'm not sure the Unetbootin method you are using will work on a UEFI machine either.  You need to use a USB/DVD.

[https://neosmart.net/wiki/easybcd/uefi/](https://neosmart.net/wiki/easybcd/uefi/)

---

