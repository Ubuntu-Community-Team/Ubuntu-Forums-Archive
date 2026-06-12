---
title: "Bootloader of ubuntu can't start"
date: 2016-11-12
forum: General Help
---

### Post by sandrag2 on 2016-11-12
Hi,
Excuse me for my english but it isn't my language... I installed Ubuntu in dual boot with Windows 10 but when I turn on the PC, the screen that should make me choose between ubuntu and windows does not appear and Windows start automatically... 
Then I went into the Bios to check on the Secure boot and It was enabled but I can't disable it...
On the right there is the indication: "Secure Boot can be enabled only when Platform Key (PK) is enrolled ..." but I don't know what does it mean...
Can someone help me, please?

---

### Post by oldfred on 2016-11-12
What brand/model system.
Normally the Secure boot keys are there as Windows only uses one and everyone else currently uses that same one.
Often easier just to turn secure boot off. Some may require setting of password in UEFI.

Both UEFI and Grub are boot managers or they give you a boot menu. Can you boot ubuntu entry from UEFI boot menu? Often f10 or f12, but varies by brand, check manual.

---

### Post by sandrag2 on 2016-11-12
Uhm My Pc is an Asus Zenbook Ux303Ub 
on my device when I press Esc during the boot of PC I can have the boot menu where I can choose Windows Boot Manager, Ubuntu, or the USB if there is a usb plugged in.
Do I have to set a password to make the secure boot off?
Thank you

---

### Post by oldfred on 2016-11-12
Some other Asus. Issues are often common by brand.
Perhaps more differences if Intel or AMD versions. And then brand of UEFI/BIOS used by vendor.
Do you have the lastest UEFI from Asus for your model system?

 Some have had to turn on CSM/Legacy boot to be able to boot USB flash drive in UEFI mode?
[http://blog.technotesdesk.com/how-to-enable-boot-from-usb-drive-in-bios-asus-zenbook/](http://blog.technotesdesk.com/how-to-enable-boot-from-usb-drive-in-bios-asus-zenbook/)
Asus UX303UB hardware problems - a list  15.10
[http://ubuntuforums.org/showthread.php?t=2319066](http://ubuntuforums.org/showthread.php?t=2319066)
Asus M32CD desktop - Skylake several boot parameters  pci=nomsi  i915.preliminary_hw_support=1
[http://ubuntuforums.org/showthread.php?t=2312977](http://ubuntuforums.org/showthread.php?t=2312977)

---

### Post by sandrag2 on 2016-11-12
My Processor is Intel's and I tried to check into C:\Windows\Panther and I found " Callback_BootEnvironmentDetect: Detected boot environment: EFI ".
I have also a good new, In some way now I have switched secure boot off, but ubuntu can't boot yet :(
I don't know what to do... when I tried to force him to boot by pressing ESC during the boot, after choosing the first time "ubuntu" nothing happened... and after re-choosing the second time "ubuntu" windows booted again... 
When I plugged in the USB for the live version, everything was ok and Ubuntu is successfully installed, but now I can't boot him...

---

### Post by sandrag2 on 2016-11-12
Sorry, now I found also this:
[http://i64.tinypic.com/w1rc5e.jpg](http://i64.tinypic.com/w1rc5e.jpg)
I hope that it can be useful...

---

### Post by oldfred on 2016-11-12
If you go to UEFI boot menu, do you have an ubuntu entry. You may even have two as one is grub and one shim. Shim is for secure boot, but works if secure boot is off. Grub entry only works if Secure boot is off. But in UEFI menu both only show as ubuntu.

And several models of Asus need a boot option. 
You may have to press escape at start of boot, or from a full power down, remove battery and hold power switch to get a "cold" boot.
Then at grub menu add pci=nomsi replacing quiet splash on linux line.
 Problems Installing on ASUS F555U   needed boot option pci=nomsi
[http://ubuntuforums.org/showthread.php?t=2303665](http://ubuntuforums.org/showthread.php?t=2303665)
Asus x555u w/o pci=nomsi - space issue on drive and runaway log files filling drive
[URL="http://ubuntuforums.org/showthread.php?t=2327103&page=3"]http://ubuntuforums.org/showthread.php?t=2327103&page=3
[/URL]
 How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters) 

[URL="http://ubuntuforums.org/showthread.php?t=2327103&page=3"]
[/URL]

---

