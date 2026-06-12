---
title: "Unable to boot into live ubuntu"
date: 2018-07-18
forum: General Help
---

### Post by scog2 on 2018-07-18
I have win 10 dell desktop and I burn the ubuntu iso onto usb and when I live boot into it, it stuck and shows nothing. I see the lubuntu logo load up then screen go stuck with the cursor _ at the top left of the screen. I can't type or do anything. I am burning the iso with rufus and I tried on another computer and it loaded the live version correctly. I tried burning another iso kali linux with yumi and tried the live version but my desktop went into grub command when trying live version. What's going on with my desktop? I did mess with the UEFI setting a bit, I don't know if it has effect.

---

### Post by oldfred on 2018-07-18
What Dell model?
What video card/chip?
If nVidia, you will need nomodeset.
Have you updated UEFI from Dell to latest for your system? And if SSD updated its firmware?

Are drives set for AHCI, not RAID, Intel SRT, nor IDE. If not AHCI add Windows AHCI driver before changing.

Are you booting in UEFI or BIOS boot mode from UEFI boot menu. It should have two entries if UEFI Secure Boot is off.

       Dell XPS 8920 desktop GTX 1060, needed UEFI/BIOS update
[https://ubuntuforums.org/showthread.php?t=2370434](https://ubuntuforums.org/showthread.php?t=2370434)
Dell XPS 8920 & Nvidia GTX 1060 & PCIe M2 drive Raid change to AHCI
[https://ubuntuforums.org/showthread.php?t=2360929](https://ubuntuforums.org/showthread.php?t=2360929)
Dell support - Update on XPS 13/15 2016 Developer Edition availability
[http://en.community.dell.com/techcenter/os-applications/f/4613/t/19670562?pi22229=9](http://en.community.dell.com/techcenter/os-applications/f/4613/t/19670562?pi22229=9)
[http://www.dell.com/support/article/ca/en/cabsdt1/SLN301754/en](http://www.dell.com/support/article/ca/en/cabsdt1/SLN301754/en)

General UEFI install instructions in link below.

---

