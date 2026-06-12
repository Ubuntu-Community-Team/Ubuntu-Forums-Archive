---
title: "No Windows 7 boot after bionic LTS install"
date: 2019-09-21
forum: General Help
---

### Post by MimziM on 2019-09-21
I have used dual boot on other machines, as well as this one, Samsung NP300E7A, was running Win 7 and 10.04 sda configuration:
sda1 - 100MB Primary - SYSTEM (Off limits)
sda2 - 189GB Primary -  NTFS Win 7
sda3 - 540GB Extended
sda5 - 469GB Logical - Ext2
sda6 - 67GB   Logical - Ext4 Ubuntu 10.04
sda7 - 5GB    Linux swap
sda4 - 20GB  Primary - NTFS SAMSUNG_REC

The dual boot was fine, GRUB menu had all options. Then Ubuntu got  corrupted and wouldn't start after an upgrade, but GRUB menu remained  and could still operate Win 7.
I downloaded 18.04 LTS and created a live USB. I changed sda using gparted from live USB to this:
sda1 - 100MB Primary - SYSTEM (Off limits)
sda2 - 189GB Primary -  NTFS Win 7
sda4 - 65GB   Primary - Ext4
sda3 - 540GB Extended
sda6 - 5GB    Linux swap
sda7 - 1GB    EFI
sda5 - 469GB Logical - Ext2
sda8 - 20GB   Logical - NTFS SAMSUNG_REC

I only realised my mistake too late, by removing the old linux logical  drive and creating a primary Ext4 when I installed 18.04 it didn't pick  up the Windows OS.
I used boot-repair to no effect, I ran boot-repair again and again using  different options until my boot died and I got GRUB RESCUE, tried a few  things, but found it easier just to reinstall 18.04.
Then I created a Win repair USB and attempted to fix boot from msdos  command prompt again I had problems ```
x:\>bootrec /fixboot
element not found
``` so went into: ```
x:\> diskpart
DISKPART>select partition 1
partition 1 selected
DISKPART>active
``` and pc hung.   When I restarted was back to GRUB RESCUE.  
Booted from live USB, ran boot-repair then restarted and I could boot in  bionic again, but sda5 and sda6 have repeated them selves up to sda255,  sda5 odd numbers, sda6 even numbers can't see previous sda7 and sda8  and can't open gparted, libpart error overlapping partitions.
This is boot-repair summary:

[URL="http://paste.ubuntu.com/p/cfYZ6F3ffn/"]http://paste.ubuntu.com/p/cfYZ6F3ffn/ 
[/URL]
Any advice on how to rectify the dual boot, would also like to sort partition issue.

---

### Post by oldfred on 2019-09-21
Your Windows looks like a BIOS  Windows boot which requires MBR partitioning. 
UEFI installs normally use gpt partitioning & Windows requires it. Ubuntu will let you install in UEFI mode to MBR (probably should not). And you cannot dual boot Windows in BIOS and Ubuntu in UEFI from same drive. You can only have one boot flag per drive and Windows has to have boot flag on its boot partition, your sda1 and UEFI has to have boot flag on the ESP - efi system partition. 
Grub also will not dual boot systems installed in different boot mode. So both must be BIOS or both UEFI to dual boot from grub.

Logical partitions are a linked list. Or the PBR in one logical list says which is the next logical partition. You somehow created a loop, so sda5 says sda6 is next & sda6 says sda5 is next.

I would try this first from Ubuntu live installer:
       sudo fdisk /dev/sda 
   Press "w". That rewrites the partition table. Reboot so that the changes take effect.

---

### Post by MimziM on 2019-09-22
Thanks, the fdisk did fix the repeated partitions, however, sda7 EFI and sda8 SAMSUNG_REC have been wiped, this is how it looks now: 

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=284109&d=1569837929[/IMG]

About the boot, I am aware that there cannot be 2 boot flags, when I deleted the old ubuntu and created the new primary I wiped out all the boot info along with the grub. 
My intention was/is to fix the windows boot, which then would probably only boot to windows afterwards, then booting from a Live disc/usb I could either update-grub or use boot-repair to recreate GRUB, it should then pick them both up and give them the same flag.  No?

---

