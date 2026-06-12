---
title: "UEFI USB Boot Disk"
date: 2014-08-27
forum: General Help
---

### Post by Francis_Bouchard on 2014-08-27
I want to create a UEFI USB boot disk for Linux.  I am trying with grub-install but my BIOS does not detect it as a valid UEFI USB device, it seems to detect it as a hard drive.  I can only boot into Linux as long as I don't boot into Windows.  If I do boot into Windows, my BIOS does not recognize my USB disk at all anymore.  How could I create a boot disk ?

---

### Post by sudodus on 2014-08-28
I made an installed system, that can boot from UEFI as well as BIOS. See these links
[URL="http://ubuntuforums.org/showthread.php?t=2213631"]
Portable installed system that boots in UEFI as well as in BIOS mode[/URL]                 

[https://help.ubuntu.com/community/Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)

Is that what you want? Otherwise, you can make a persistent live drive from a current 64-bit Ubuntu family desktop iso file.

You may need to shut Windows down completely, not have it hibernated or semi-hibernated. So it helps to switch off fast boot and maybe also secure boot.

---

### Post by grahammechanical on 2014-08-28
My BIOS sees a Ubuntu live USB stick as an external USB hard disk. I can change boot priority in the hard disk section of the BIOS. We should be able to enter the BIOS/UEFI set up program before we load Windows.

---

