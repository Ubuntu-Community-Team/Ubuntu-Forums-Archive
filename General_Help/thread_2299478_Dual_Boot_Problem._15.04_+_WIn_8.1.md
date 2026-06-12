---
title: "Dual Boot Problem. 15.04 + WIn 8.1"
date: 2015-10-18
forum: General Help
---

### Post by udfyme on 2015-10-18
After much research Ive come here to post. I deleted my ext4 partition and created a new one then installed 15.04. I was using a previous version of ubuntu before all of this and everything worked perfectly. When I select windows to boot in GRUB the screen flashes and reloads GRUB. Here is my boot-repair url [http://paste.ubuntu.com/12856250/](http://paste.ubuntu.com/12856250/) Any help would be appreciated.

---

### Post by tristan16 on 2015-10-18
When you deleted your ext4 partition, did you also delete the Grub partition? If not, Grub is probably still looking for your previous version of Ubuntu. Try booting from a Live USB and running ```
 sudo update-grub 
```

---

### Post by udfyme on 2015-10-18
Cold boot of computer will auto boot into Ubuntu through grub2. Running that command has zero effect.

---

### Post by oldfred on 2015-10-19
You installed grub to sda1, your NTFS Windows boot partition (PBR). But Windows has essential boot information in the PBR including partition start & size that must match partition table and which boot loader to use, ntldr for XP or bootmgr for all Windows after XP.

NTFS does keep a backup PBR, and usually you can restore from backup with testdisk. It may say PBR is valid as grub can be valid in other than NTFS partition PBR, but with grub in a NTFS PBR, it cannot be really valid. If backup is valid restore it. If not valid use the option to create a new BS, but it will be an XP type and you then have to run chkdsk from Windows. 
       You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)
select [Advanced] instead of [Analyse] and select [BackupBS]
[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)

If testdisk does not work you have to use your Windows repair flash drive and bootsect.exe. But Windows may not recognize partition with grub in it, and you must use the testdisk new BS command to at least make it an XP type that then can be repaired.
       
 How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
Use bootsect.exe to repair XP & older or Vista/7 bootsectors - Use diskpart, then list volumes to see which drive to use 
bootsect.exe /nt52 c:  *compatible* with operating systems older (XP) than Windows Vista.
bootsect.exe /nt60 c:  *compatible* with Windows Vista, Windows Server 2008 or later

---

