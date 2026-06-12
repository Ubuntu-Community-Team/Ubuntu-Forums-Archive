---
title: "Fix External HDD NTFS"
date: 2017-09-28
forum: General Help
---

### Post by makez on 2017-09-28
Yesterday I installed Ubuntu and when I connected my external HDD (with important files) I saw I couldn't open it, **it said some thing like**:
```
Error mounting /dev/sda3 at /media/sergioandvar/Datos: Command-line  `mount -t "ntfs" -o  "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,dmask=0077,fmask=0177"  "/dev/sda3" "/media/sergioandvar/Datos"' exited with non-zero exit  status 14: The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Failed to mount '/dev/sda3': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.
```

**It didn't say exactly that**, I got this message from a forum because I know it what something like this.

I tried to solve that problem so I could open the external HDD and I executed a command, I can't remember what command it was, I got it from a forum from someone with the same problem. When I executed the command the HDD icon disappeared from Ubuntu. 

Now I cannot access the HDD from Windows (it says RAW type). Same in Ubuntu, if I go to Gparted I can see it there, it says it is NTFS but I don't know what to do.

[IMG]https://i.imgur.com/DFJ9aWgh.png[/IMG]

---

### Post by yancek on 2017-09-28
Not knowing what command you ran is going to make it very difficult to help.  The message you posted tells you what the problem is and the solution, turn off hibernation and fastboot in windows.  Have you done that?  If not do so, and reboot you may simply need to mount it again but that depends upon what command you ran.

---

### Post by oldfred on 2017-09-28
+1 on yancek's suggestions.

RAW in the Windows world means the partition is not formatted internally. 
Both partition table and partition boot sector (PBR or BS)must match and be NTFS.

NTFS does have a backup of the PBR and testdisk can restore that. Also various Windows tools may do the same. If you reformat it, you may lose your data.

        PBR - partition boot sector NTFS must be Windows
[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)
[http://askubuntu.com/questions/655290/grub-is-not-letting-me-switch-to-windows-8-dual-boot-process-ubuntu-15-04/655486#655486](http://askubuntu.com/questions/655290/grub-is-not-letting-me-switch-to-windows-8-dual-boot-process-ubuntu-15-04/655486#655486)
As described, testdisk has an option to "Recover NTFS boot sector from its backup"
If Backup BS isn't available, choose RebuildBS, otherwise Windows repairs will not work 
Instructions - see section on NTFS partition boot sector recovery
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)
select [Advanced] instead of [Analyse] and select [BackupBS]
Also check for /boot/grub in addition to /Boot  

If you have to run the Rebuild BS from testdisk, then you may have the XP type (nt52) of BS/PBR and need to convert to the Windows 7 or newer type (NT60).
       
 [http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
Use bootsect.exe to repair XP & older or Vista/7 bootsectors - Use diskpart, then list volumes to see which drive to use 
bootsect.exe /nt52 c:  *compatible* with operating systems older (XP) than Windows Vista.
bootsect.exe /nt60 c:  *compatible* with Windows Vista, Windows Server 2008 or later

---

### Post by dragonfly41 on 2017-09-28
Run command ..
```
history
```
to review the last few commands you ran.

Can't remember the tail arg to shorten the list.

[edit]

It is this ..

```
history | tail -30
```

---

