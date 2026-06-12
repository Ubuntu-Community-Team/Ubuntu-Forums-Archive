---
title: "Dual Boot Windows 8 and Ubuntu on ASUS K55A"
date: 2013-06-21
forum: General Help
---

### Post by septimushodge on 2013-06-21
I'll apologize in advance, I found some earlier threads on this topic, though I couldn't find one that worked for me.

I received an ASUS laptop as a gift with Windows 8 preinstalled. I burned Ubuntu 13.04 to a DVD and made a USB key. I tried to restart from it, got to the

Try Ubuntu
Install Ubuntu
...

Screen. However, when I select any option, the computer just goes to a black screen and sits there. When I boot to the BIOS, I can disable the FastStartup, but I don't see the other two options listed here: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

I've tried various things in the other threads on this topic, and gotten nowhere.



If nothing else, I'll probably just wipe the HD and install Ubuntu (can someone point me to some how-to that won't totally destroy my laptop, if I go that route?)

THanks!


//EDIT

BIOS Options:
Advanced:
Start Easy Flash
Internal Pointing Device [Enabled]
Wake on Lid Open [Enab]
Power Off Enerdge Saving [En]
Intel Virtualiz [En]
Inel AES-NI [En]
> SATA Config
>Graphics Config
>Intel Anti-Theft Config
>USB Config
>Network Stack

Boot
Fast Boot [DISABLED]
Launch CSM [DISABLED]

---

### Post by oldfred on 2013-06-22
Those with K55N have had video issues that could not be resolved to dual boot in UEFI mode. Other Asus have worked.

I would make sure you have the newest UEFI/BIOS version.

       ASUS K55A  Windows 8 & Ubuntu   Some Asus need this boot parameter pci=nomsi
[http://ubuntuforums.org/showthread.php?t=2088499](http://ubuntuforums.org/showthread.php?t=2088499)

      
   [SOLVED] Dual Boot on Asus K55vd SX696H - 8 GB (Solved) EFI
[http://ubuntuforums.org/showthread.php?t=2151394](http://ubuntuforums.org/showthread.php?t=2151394)
Asus N56VJ-SH71-CD Shows default Windows partitions Post #25 install instructions
[http://ubuntuforums.org/showthread.php?t=2105622](http://ubuntuforums.org/showthread.php?t=2105622)

 Asus UltraBook - kernel comparisons K56CA
[http://www.phoronix.com/scan.php?page=news_item&px=MTMzOTI](http://www.phoronix.com/scan.php?page=news_item&px=MTMzOTI)

Is your model an UltraBook? That adds complications of dual video needing Bumblebee and Intel SRT which uses RAID.

See also link in my signature.

A few with UEFI systems have erased Windows and just install Ubuntu. Some with UEFI and others had to convert back to BIOS or CSM/legacy to make it work.

---

### Post by septimushodge on 2013-06-22
I actually got it working- in the BIOS I disabled the secure boot option under 'Security' and it worked...


Thanks!

---

