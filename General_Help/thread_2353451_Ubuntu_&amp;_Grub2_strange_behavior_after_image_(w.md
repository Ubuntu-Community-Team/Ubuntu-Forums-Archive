---
title: "Ubuntu &amp; Grub2 strange behavior after image (with uefi)"
date: 2017-02-21
forum: General Help
---

### Post by the.spy.c on 2017-02-21
(In advance, sorry for my bad English and thanks for your time) 

Hello there. I am encountering a very weird problem. 
 
My friend and I, were asked to clone the disk from a computer (Dell Optiplex 3040 -14 times, to make a lab). Previously we installed in the computer Windows 7 and Ubuntu 16.04, both 64-bit. 
We used Clonezilla server, and cloned some disks (from other OP3040s but wore them instead on older pcs). 
The cloning seemed ok, but when we put a cloned disk in a second OP3040, only Windows 7 were capable to boot (after secure boot gone off and legacy roms on) even if ubuntu was visible as a boot option...  

The weird (for me the amateur) thing is that all the clones are working properly in the "cloned" OP3040 (the one that we set up at first), even with seemingly same bios setup. 

Do you believe that i must recover the grub or there will be something on bios settings that can make the other OP3040s to read the grub2 properly?

---

### Post by oldfred on 2017-02-22
Are systems really identical.
Vendors may use different parts (equivalent function) in same model during production. But drivers may need to be different.

Was Windows 7 installed in BIOS or UEFI mode? Windows 7 DVD is the 35 year old BIOS/MBR configuration, not the newer UEFI/gpt configuration.
But new systems are usually configured for UEFI/gpt with Windows 8 or 10. 
And installing any version of Windows in BIOS mode converts the gpt drive to MBR incorrectly.

You also can convert a Windows 7 DVD to UEFI boot by copying to flash drive and moving files around to make it UEFI bootable for installing in UEFI mode.

A clone often does not clone MBR, you may need to also copy that or run repairs.

Post link this for original system and one of the non-working systems and we can see the difference. If simple reinstall of grub to MBR, Boot-Repair can easily do that, or you can manually reinstall grub from live installer.
 May be best to see details, you can run from Ubuntu live installer or any working install:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[URL="https://sourceforge.net/p/boot-repair/home/Home/"]https://sourceforge.net/p/boot-repair/home/Home/

[/URL]
 How to restore the Ubuntu/XP/Vista/7/8/10 BIOS bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System) 

If really UEFI see many of the links in my signature below.

[URL="https://sourceforge.net/p/boot-repair/home/Home/"]
[/URL]

---

