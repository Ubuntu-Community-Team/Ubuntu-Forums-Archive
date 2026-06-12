---
title: "Triple booting, removed Vista partition, error 17"
date: 2007-12-26
forum: General Help
---

### Post by Whoozit on 2007-12-26
Warning: long question ahead. I try to give as much info as possible. Thanks in advance for the help.

When I built my new machine, I originally wanted to run Vista and Ubuntu. I am a reasonably savy Windows XP user, but I had never used Vista or Linux. 

I have a 300 GB SATA HDD as my primary hard disk and a 320 GB SATA HDD as the secondary data disk. After realizing that some of my old Windows programs wouldn’t run on Vista, I decided to install Windows XP in addition to Ubuntu.

So my 300 GB HDD looked like this 
- 160 GB Windows Vista 64 bit Home Premium
- 40 GB Windows XP 32 bit w/ SP 2
- 80 GB Ubuntu Linux version 7.04, 64 bit

Everything ran smoothly for a few months. When I booted, GRUB gave me the option to boot Ubuntu, (several other Ubuntu options,) or “Windows Vista/Longhorn”. When I selected “Vista/Longhorn”, I was then given the choice to boot either “Windows Vista” or “Earlier Version of Windows,” which booted XP.

I never used Vista so I decided I wanted to get rid of it and reclaim the space on my HDD. For some reason, I thought I could simply use Windows Disk Utility to delete and reformat the Vista partition (I know, not smart.)

I booted into XP as usual. I deleted the Vista partition. I rebooted to see what would happen. I saw error 17 and the machine failed to boot.

I used an old machine to make a boot disk with Super GRUB. I was able to get Windows to boot by selecting 

Super Grub with Help -> English -> Windows -> Boot Windows

After I did this, I was taken to the screen with the two familiar options “Windows Vista” or “Earlier Version of Windows.” When I select “Earlier Version of Windows”, Windows XP boots as normal. Of course, when I select “Windows Vista” it fails to boot. 

Now here is my question. Super GRUB says that I can select the option “Fix Boot of Windows” to get rid of the GRUB boot loader and have my machine boot directly into Windows. But I am afraid to select this option. I want to boot directly into Windows XP, but the first OS I had installed was Windows Vista (now deleted.) 

When I turn my computer on, I want it to give me the option to boot Windows XP or Ubuntu (and have Vista taken out of the equation completely.) I could also have it boot directly to Windows XP because then I can delete all other partitions and reinstall Ubuntu and GRUB (I think.)

I have all of my files backed up on my second internal HDD, and all of my important files backed up on a USB flash drive.

**Should I select “Fix Boot of Windows”?** Any help is much appreciated.

---

### Post by stalker145 on 2007-12-26
> **Whoozit said:**
> Now here is my question. Super GRUB says that I can select the option “Fix Boot of Windows” to get rid of the GRUB boot loader and have my machine boot directly into Windows. But I am afraid to select this option. I want to boot directly into Windows XP, but the first OS I had installed was Windows Vista (now deleted.) 

When I turn my computer on, I want it to give me the option to boot Windows XP or Ubuntu (and have Vista taken out of the equation completely.) I could also have it boot directly to Windows XP because then I can delete all other partitions and reinstall Ubuntu and GRUB (I think.)

If you could post the contents of /boot/grub/menu.lst (all after ## ## End Default Options ##) and we can try to help you through it. Just off the top of my head, it sounds like you need to remove any references to Vista in that file. 

If you make any changes to that file, please make sure to back up a copy of it before rebooting.

---

