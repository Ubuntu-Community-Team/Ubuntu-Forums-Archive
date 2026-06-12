---
title: "Ubuntu won't boot properly"
date: 2013-03-29
forum: General Help
---

### Post by Quail2 on 2013-03-29
I have a dual boot with Windows 7 and Ubuntu 12.04. Yesterday, Ubuntu stopped booting properly for a reason I can't determine. When I try to boot Ubuntu, it stays on the purple loading page for a long time (maybe 10 minutes), before giving me a black screen. I can't manage to bring up a terminal. A friend suggested that it might be a problem with the bootloader, so I have tried using Super Grub Disk to fix it, but that failed. I've also tried to boot Ubuntu from a CD, but for some reason that wouldn't boot up properly either (and I checked the disc for errors before I tried). Windows is booting up fine, in fact I'm using it now. I can't remember whether I installed any updates yesterday which might have caused this, and there didn't seem to be anything wrong with my laptop earlier yesterday, although Clementine was causing the laptop to freeze periodically.

Any help would be much appreciated.

Edit:
I should add that I've just tried booting up again and actually I don't get a completely black screen. It says:

> BusyBox v1.18.5 (Ubuntu 1:1.18.5-1ubuntu4.1) built in shell (ash)
Enter 'help' for a list of built-in commands.

I don't really know which commands I could use from there to fix the problem.

---

### Post by fantab on 2013-03-29
If it were a bootloader issue you wouldn't see the "purple loading page". Tell us more about your laptop specs, especially Graphics. IS there any proprietary graphics driver in question?

---

### Post by Quail2 on 2013-03-29
Some info from Dxdiag:
> Time of this report: 3/29/2013, 18:30:35
       Machine name: LYSANDER-HP
   Operating System: Windows 7 Home Premium 64-bit (6.1, Build 7601) Service Pack 1 (7601.win7sp1_gdr.130104-1431)
           Language: English (Regional Setting: English)
System Manufacturer: Hewlett-Packard
       System Model: HP Pavilion g6 Notebook PC      
               BIOS: InsydeH2O Version 03.61.01F.63
          Processor: Intel(R) Core(TM) i3-2330M CPU @ 2.20GHz (4 CPUs), ~2.2GHz
             Memory: 6144MB RAM
Available OS Memory: 6092MB RAM
          Page File: 2123MB used, 10058MB available
        Windows Dir: C:\Windows
    DirectX Version: DirectX 11
DX Setup Parameters: Not found
   User DPI Setting: Using System DPI
 System DPI Setting: 96 DPI (100 percent)
    DWM DPI Scaling: Disabled
DxDiag Version: 6.01.7601.17514 32bit Unicode

Card name: Intel(R) HD Graphics Family
       Manufacturer: Intel Corporation
          Chip type: Intel(R) HD Graphics Family
           DAC type: Internal
         Device Key: Enum\PCI\VEN_8086&DEV_0116&SUBSYS_166F103C&REV_09
     Display Memory: 1696 MB
   Dedicated Memory: 64 MB
      Shared Memory: 1632 MB

I edited my above post, by the way.

---

### Post by Quail2 on 2013-03-29
I've found this: [http://bernaerts.dyndns.org/linux/232-ubuntu-boot-failure-initramfs](http://bernaerts.dyndns.org/linux/232-ubuntu-boot-failure-initramfs)

I'll update later with whether or not it worked.

---

### Post by Quail2 on 2013-03-29
I fixed it using the link in the post above :)

---

