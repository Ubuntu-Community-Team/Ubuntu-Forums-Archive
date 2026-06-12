---
title: "pnpbios"
date: 2004-11-09
forum: General Help
---

### Post by Changeling on 2004-11-09
When I start my computer I get the following message;

  9 00:35:45 localhost kernel: PNPBIOS fault.. attempting recovery.
Nov  9 00:35:45 localhost kernel: PnPBIOS: Warning! Your PnP BIOS caused a fatal error. Attempting to continue
Nov  9 00:35:45 localhost kernel: PnPBIOS: You may need to reboot with the "nobiospnp" option to operate stably
Nov  9 00:35:45 localhost kernel: PnPBIOS: Check with your vendor for an updated BIOS
Nov  9 00:35:45 localhost kernel: PnPBIOS: get_dev_node: unexpected status 0x28

Its an AMI Bios and it's the latest version. The motherboard is a Soyo Dragon2 V1.0
I don't seem to be having any problems running ubuntu , I'm just curious about this message. It also occurs when I boot a Simply Mepis live cd.
Any ideas?

---

### Post by jdong on 2004-11-09
Your BIOS has a buggy / nonstandard implementation of PCI Plug n Play. Don't worry about it; recent kernels can gracefully disable pnpbios upon detecting failures.

---

### Post by rosvall on 2004-11-12
I have same "problem" with ami bios. Is there any way to get that kernel do not everytime prompt about it? Just curious...

---

### Post by Nico666 on 2005-01-21
I have the same problem with a amibios a7nvm 1003 updating from the base bios of a motherbroad Asus a7n8x vm400.
Please Help!!

---

### Post by Rancoras on 2005-01-22
[QUOTE=Nico666]I have the same problem with a amibios a7nvm 1003 updating from the base bios of a motherbroad Asus a7n8x vm400.
Please Help!![/QUOTE]

Why are you updating a mobo with the bios from another board?  It seems that is just asking for trouble.  Anyway, have you tried passing the nopnpbios option to the kernel like the error tells you?  You can do that by using the instructions here:  [http://ubuntuguide.org/#gainrootmodifykernel](http://ubuntuguide.org/#gainrootmodifykernel) but when it talks about adding "rw init=/bin/bash" to the line, add "nopnpbios" instead (minus quotes of course).

---

### Post by wheelerview on 2005-03-10
edit:
Figured out what I posted below edit.
I reinstalled once more, and it still didn't work.  I then took the hard drive out and put it in my XP machine, then I got it formatted again.  Put it back in where it started, reinstalled Ubuntu again and it now seems to work fine.  Only thing is it doesn't like my windows modem but everything else looks ok.
end edit:

I just got my install cds today, and I am getting the same error message when I run the 

live cd as the first post, but it does not boot.  I have tried the nobiospnp option by 

editing the live cd boot, then it will boot, but only if I edit the "safe" mode one 

(don't think it's called safe mode, but I can't think what else now).  It will not boot 

if I try to keep the normal boot settings, it has to be the safe mode.     I can 

install Ubuntu from the install cd, it gets all the way through, but when it says to 

remove the disk and then reboots, it boots to the text screen that says loading the 

grub, and freezes after the second line of text on that first page, I can't esc to get 

to anything at all, or any other button, no matter how long I leave it on.   If I edit 

the live cd safe one, I can get in and see that all files appear to be on hda1, I can 

get in on root and edit those files as well.  Does anyone have any suggestions?  I have 

never used or configured Linux at all before today.

specs
Soyo P4I865PE Plus Dragon 2 v1.0
2.4 ghz celeron 400fsb
256 ddr
80gb IDE Western D HD 8mb cache, (chose to use entire drive in setup)
IDE cdrw
floppy
Gigabyte ATI Radeon 9200SE

I had both Windows 98se and XP on the drive at different times, I know the system works 

well, used quite a bit, no probs, no bad ram, etc.  Also since installing ubuntu, for 

some reason, I can no longer boot from a 98se boot floppy or an XP cd or the Western 

digital setup cd, it freezes in those too, but the ubuntu live cd boots fine....  If I 

unplug the hard drive, it boots fine off floppy or cd.  I know the drive is not bad, I 

can access the whole thing.  I've reset the bios with the internal jumper, I've now 

updated it to a bios dated 12/29/04 and still have the problem.

---

