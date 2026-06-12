---
title: "Boot Live USB from grub rescue mode"
date: 2020-01-22
forum: General Help
---

### Post by timufa123 on 2020-01-22
Hello 


I accidentally deleted the GRUB partition (of course) and now there is only grub rescue mode.

I want to boot the Live USB (Ubuntu 16.04 that i made in Ubuntu Disk Creator) from the grub rescue mode. The same version i hade before the disaster.

Is this even possible?

I check many websites and forums and it's all about finding the GRUB partition (it didn't work for me) and set the right partition but nothing about how to boot from Live USB.


People advice to use Rescue Disk or Windows USB BUT i can't boot from USB even if i did the right settings in the BIOS and UEFI Legacy stuff.
I booted the Ubuntu USB from GRUB2 and i thought it was possible to do it in the grub rescue mode.

The Live Rescue Disk is Linux too and if i can't boot even Ubuntu USB it wouldn't work Or is it?

Ruffus, Unetbootin, UDC, etc didn't work. 

Switched USB ports.

Nothing...


My options is to connect other hard drive? Tech support?


I couldn't find nothing about this issue even in Ubuntu Wiki or GRUB manual page.

Thank you.

---

### Post by CelticWarrior on 2020-01-22
Your post is very confusing (Note: I'm being nice)...

There's no "Grub partition". In UEFI systems Grub resides in a special partition - ESP (EFI System Partition) - but that cannot be named as such, it's independent from Grub, it exists in all UEFI systems and contains the .efi files for all installed OSes, including Windows. [B]Is this the partition you said you deleted? 
[/B]In old BIOS systems GRub is installed in the MBR and MBR is not a partition.

You can boot any (bootable) mediaas usual, from BIOS/UEFI settings or one time boot menu; **you cannot boot live media from Grub rescue.**

I won't comment on the remaining incoherent sentences. Please explain what are you trying to do. Are you trying to recover the installed OS? If so, Boot Repair might help but it depends on what you actually did that resulted in the current situation.

Perhaps better to boot from a live session, do your backups and then just reinstall.

---

### Post by timufa123 on 2020-01-22
Solve it 
Set default settings in BIOS
Thank you

---

