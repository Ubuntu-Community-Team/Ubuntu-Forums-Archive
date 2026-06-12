---
title: "Booting problem --No GRLDR"
date: 2013-05-15
forum: General Help
---

### Post by sharlos on 2013-05-15
Hello, I need to get this fixed asap in order to get some files I need urgently, help tonight would be greatly appreciated.

Here is the situation:

I have windows 7 (64 bit) and Ubuntu 12.04 (64bit) installed on my laptop. Upon installing windows 7, the ubuntu boot menu disappeared, and I tried to fix this using a variety of software. Long story short, i'm not sure what I've done, but the computer wont boot any longer. 

Here is what the output looks like:
-------------------
Try (hd0,0) FAT16: No GRLDR
Try (hd0,1): Invalid or null
Try (hd0,2): This partition is ntfs but with unknown boot record. Please install Microsoft NTFS boot sectors to this partition correctly, or create an FAT12/16/32 partition and place the same copy of GRLDR and MENU.LST there*
Try (hd0,3): Extended:
Try (hd0,4): non-ms: skip
Try (hd0,5): Extended:
Try (hd0,5: EXT2:*
----------------------
* 1) I cannot type at all. Nothing I can do on the keyboard changes this screen.
* 2) I believe that windows is on partition (hd0,2)
------------------------
I tried using my ubuntu live boot USB go fix this problem; I downloaded ubuntu from the main website, and used UNbootin to boot the ISO. It works on other computers.

Here is the output that comes out when I insert the USB:
------------------------------
Try (hd0,0): This partition is ntfs but with unknown boot record. Please install Microsoft NTFS boot sectors to this partition correctly, or create an FAT12/16/32 partition and place the same copy of GRLDR and MENU.LST there.
Try (hd0,1): Invalid or null
Try (hd0,2): Invalid or null
Try (hd0,3): Invalid or null
Try (hd1,0) FAT16: No GRLDR
Try (hd1,1): Invalid or null
Try (hd1,2): This partition is ntfs but with unknown boot record. Please install Microsoft NTFS boot sectors to this partition correctly, or create an FAT12/16/32 partition and place the same copy of GRLDR and MENU.LST there
Try (hd1,3): Extended:
Try (hd1,4): non-ms: skip
Try (hd1,5): Extended:
Try (hd1,5: EXT2:*
-----------------------------------------
*Again, I cannot type or do anything to change the screen.
----------------------------------------
When I tried entering a blank usb in order to get into the grub rescue options, whenever I try to ls one of the partitions on my drive, I get this message : error, unknown filesystem.

Please help, I need to get this sorted asap.

---

### Post by ajgreeny on 2013-05-15
See section 13 of [Grub 2 Basics]("http://ubuntuforums.org/showthread.php?t=1195275") which should give you back a working grub, then run ```
sudo update-grub
``` to add in your windows OS to the menu.

---

### Post by oldfred on 2013-05-15
I believe grldr is from EasyBCD. That is actually from grub4dos that it uses.

But NTFS partitions have to have an NTFS boot signature in all NTFS partitions. It sound like that may not be the case? Testdisk can restore from the backup if only overwritten once.

May be best to see all the details. Boot-Repair cannot fix internal Windows issues or run chkdsk which may also be required. You need your Windows repairCD or flash drive for that.

 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)

---

