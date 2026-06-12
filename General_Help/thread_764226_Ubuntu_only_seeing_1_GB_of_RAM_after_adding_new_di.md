---
title: "Ubuntu only seeing 1 GB of RAM after adding new dimms"
date: 2008-04-23
forum: General Help
---

### Post by shmoe010 on 2008-04-23
I recently installed 2x1GB of G.skill DDR 3200 ram onto my machine, adding that to the existing 2x512MB I had. The PC boots and everything without any errors, but it does not see the added ram. I have looked around online for a fix, because I don't know if it is Ubuntu or my motherboard that is causing the problem, but I'm leaning toward the Mobo.

PC specs:

DFI LanParty NF4-SLI Socket 939
AMD Opteron 165
(now) 2x512MB Crucial Ballistx DDR and 2x1MB G.skill ddr 400
eVGA 7800 GTX
1kW PC P&C psu
OS: Ubuntu 7.10 (gave up on 8.04 lol)

Any insight would be helpful. I know that if it's my motherboard this may not be the best place to put a question, but I couldn't find any answers anywhere else, and for all I know it could be something in the OS.

Thanks in advance for any insight you guys might have.

---

### Post by LausArndon on 2008-04-23
When your PC is first booting you should be able to see how much RAM is installed. If it shows all 3 gigs, your problem is with Ubuntu. If you can't see it, do you have another OS you could boot to to check it?

---

### Post by jespdj on 2008-04-24
Boot your computer, and in the GRUB menu choose to boot the memory test program (memtest86). See if it sees all the RAM. If it does, let it run for a few hours to test the RAM.

Is your new RAM the same type and speed as what you already had in your computer? Are all the BIOS settings correct? Are you sure the RAM is compatible with your motherboard? Most motherboard manufacturers have a QVL (Qualified Vendor List) which lists the brands of memory that are certified to work with your motherboard.

Does the computer work with only the new RAM (remove the old 2 x 512 MB)?

---

