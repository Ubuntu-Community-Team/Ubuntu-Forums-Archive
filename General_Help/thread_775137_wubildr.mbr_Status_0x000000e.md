---
title: "wubildr.mbr Status: 0x000000e"
date: 2008-04-29
forum: General Help
---

### Post by fbaerkir on 2008-04-29
First off: I didn't know where this should go, so I posted it on the install forum as well. Sorry about the cross-posting.
I've tried everything I can think of to install Ubuntu, and nothing works. I tried using dmraid to get it to share my RAID with Vista, with no luck. I tried adding a separate HD, but installing on that disabled my Windows MBR. I tried manually editing Grub, with no luck. I tried telling Grub not to alter other drives, but it stilled altered my Windows mbr. I also tried putting Grub on a floppy; that didn't work, either. Nor did editing Grub on that floppy.
Finally, I tried just using Wubi. Of course, no dice.
Using Wubi, I'm trying to put the files on a separate partition that's not part of my RAID. It looks like it installs OK, but when I select Ubuntu to boot, it fails.
I get the following message:
file:\ubuntu\winboot\wubildr.mbr
Status: 0x000000e
Selected entry could not be located because the application is missing or corrupt
I've looked around on the forums and see no solutions to this.
Does anyone know of any way, using RAID5, a separate HD, or Wubi, that I can get Ubuntu up and running?

---

### Post by ago on 2008-04-30
Well for Wubi/Ubuntu you cannot use raid disks and encrypted disks.
But other than that it should be fine.

I haven't seen the error above before though. Can you try with a clean installation?

Uninstall, run chkdsk /r on the target drive, defragment, install.

Tinybit and Bean123 are the grub4dos expert maybe they can add some color here.

---

### Post by fbaerkir on 2008-04-30
Thanks! I'll try that.
About the RAID disks, though. I'm trying to put Ubuntu on a separate, non-RAID disk. My Windows install, though, is on an array. So when you say Ubuntu can't work with RAID, does that setup count?

---

### Post by ago on 2008-04-30
That depends on whether grub4dos can access the raid. Tinybit and Bean123 could provide a definitive answer. You can check that from grub4dos prompt.

Certainly if the root.disk and ISO are on a software raid they cannot be accessed since the initrd does not contain the appropriate modules.

---

### Post by fbaerkir on 2008-04-30
Well, I checked the CD, uninstalled Wubi, reformatted the standalone HD, and then tried again. No dice.
Apparently there's just no way to use Ubuntu in a machine that has a RAID (granted, it's a mobo RAID, but it's still run through the chipset, not the OS), even if it's not used for the Linux install. Seems strange, but I've tried everything I can think of.

---

### Post by bean123 on 2008-05-01
I don't think this is a grub4dos related problem. The error is reported by bcdedit, grub4dos hasn't started yet.

---

### Post by Ibotster on 2008-06-22
I have a similar problem. Well... similar.. 

I believe the error ís caused by Grub4dos.

I do not believe Grub4dos is capable of handling Windows Vista in a RAID array, I am installing Windows Vista Unattended on my PC, and the person who created it, had implemented Grub4dos into the installation... 

The Installation works fine, rebooting, changing everything, no problem.. But the second I put 2 of my extra hard drives in a RAID-0 it's over, when I try to reboot, the startup doesn't work, i get the following errors:
```

Booting Windows Vista

acpi 
Vista Loader 2.1.2

Done! 
fallback 1
find --set-root /bootmgr

Error 17: File Not Found
Booting 'Windows NT/2000/XP'

fallback 2
find --set-root /ntldr

Error 17: File Not Found
Booting 'Enter Command Line'

Boot failed! Press any key to enter command line
```

If I press a key, I end up in a boot menu of some sort, I can enter commands or press escape to edit the lines?

I never heard of Grub4dos before today, but I dont like it :) 

The problem you have with the RAID... I think it s because of Grub4dos...

---

### Post by tinybit on 2008-06-22
@Ibotster
> 
......
Vista Loader 2.1.2
......
I think it s because of Grub4dos...

This is a pirated VISTA. It used a modified older version of grub4dos to boot VISTA. This version of grub4dos is not recognised by the grub4dos team. We can't approve of this sort of thing.

---

