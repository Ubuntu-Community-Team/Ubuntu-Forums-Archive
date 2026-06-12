---
title: "Bootloader Boot Loop"
date: 2018-06-12
forum: General Help
---

### Post by kale0uts on 2018-06-12
Hi All!!

New here, sorry if this is in the wrong place (figured it'd be the best) but I have a bit of an interesting situation right now, and being relatively new have searched through but haven't found much. Heres what:

Recently installed Ubuntu 16.04lts (upgraded to18.04lts if that matters)
during this install I got a couple of issues
I either:
-Could not install the boot manager, or
- ended up installing this on my windows 7 boot disc (where it currently resides until I can recover. I was an idiot and didn't back up before I did this)
2 issues: I don't have my windows 7 install (long story) and I have files I need in that OS. like *NEED* not just "need cause whatever".
 Now, I've tried booting to windows 7 but what happens is that I end up getting a blank screen for about 1-2 seconds and then it takes me back to the boot loader with Ubuntu. All help and suggestions would be awesome, appreciated, and I am willing to try as long as I'm not wiping. 

Sorry for the list of instructions but I hope it helps info wise. 
thx
kale0udz

---

### Post by oldfred on 2018-06-17
May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by kale0uts on 2018-06-23
[http://paste.ubuntu.com/p/CV3K33VKhj/](http://paste.ubuntu.com/p/CV3K33VKhj/) this was created from the install. sorry for the late reply.

---

### Post by oldfred on 2018-06-23
With 2 drives, do not run auto fix from Boot-Repair, only use advanced mode.

You installed grub to the PBR (partition boot record) or BS (boot sector) of sdb1 which is NTFS and the Windows boot partition. 
That breaks Windows as the Windows boot process is from MBR to PBR to boot files in boot partition or sometimes if all boot files are in main partition then main install.
       Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
    
You must first repair the NTFS boot sector. NTFS does keep a backup, and normally you can just restore the backup. Testdisk may say grub is valid as it can be installed to a PBR, but never should be installed to a NTFS PBR. Testdisk uses BS for partition boot sector.
       You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)
[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)
Also check for /boot/grub in addition to /Boot  

Since you have two drives often better to have each install separate or on its own drive.
But you still can have grub installed to sda even though Ubuntu is on sdb, and keep Windows boot loader in sdb. And set BIOS to boot from sda. Then when (not if) Windows has issues you can often directly boot Windows on sdb using BIOS. Grub only boots working Windows.

Since sda is gpt, you first need a bios_grub partition for grub to correctly install. From Windows shrink any NTFS partition by 3 or 4 MB. Reboot and run chkdsk on that partition from Windows.,
Then use gparted to create a new 1MB unformatted partition with the bios_grub flag. 
And then use Boot-Repair's advanced mode, choose your Ubuntu install and sda to install grub.

---

