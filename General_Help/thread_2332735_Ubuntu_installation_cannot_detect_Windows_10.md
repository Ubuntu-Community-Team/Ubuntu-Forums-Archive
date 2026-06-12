---
title: "Ubuntu installation cannot detect Windows 10"
date: 2016-08-03
forum: General Help
---

### Post by stardusthacker on 2016-08-03
So, I have Windows 10 installed on my laptop and am trying to install Ubuntu 16.04 alongside it.
I followed these links for instructions:
[http://www.everydaylinuxuser.com/2015/11/how-to-install-ubuntu-linux-alongside.html](http://www.everydaylinuxuser.com/2015/11/how-to-install-ubuntu-linux-alongside.html)
[http://www.tecmint.com/install-ubuntu-16-04-alongside-with-windows-10-or-8-in-dual-boot/](http://www.tecmint.com/install-ubuntu-16-04-alongside-with-windows-10-or-8-in-dual-boot/)
The problem is I don't get the "install Ubuntu alongside Windows Boot Manager" option.
I have disabled secure boot. I had 3 primary partitions which I turned to 2 now. Yet, there is no such option. I am a little afraid to try and manually create the partitions by selecting "something else".
It just won't detect the already installed Windows. 
Is there any way to get it detected? Or will the "something else" option work properly without harming windows?

---

### Post by oldfred on 2016-08-03
If down to 2 partitions, sounds more like BIOS/MBR not UEFI/gpt.
Post this from terminal in live installer's live mode.
sudo parted -l

Windows 10 has a fast start up which really is just hibernation. But Linux NTFS driver will not normally mount Windows that is hibernated nor needs chkdsk. And it needs chkdsk after any resize.
       Fast Startup off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)

If UEFI, see link below in my signature for more info.

---

### Post by stardusthacker on 2016-08-04
Turned off the fast starup. Still won't detect Windows.

This came up after sudo parted -l

[ATTACH=CONFIG]270567[/ATTACH]

---

### Post by oldfred on 2016-08-04
You have a whole lot more than two partitions. And then a standard UEFI install.

Lots more details in link below in my signature.

Best to use Windows own tools to shrink the main NTFS partition and reboot immediately to let Windows run chkdsk as that can also cause issues on Linux seeing Windows.

If terminal output, just copy & paste into forum. If longer use code tags. Easy to add code tags with Forum's advanced editor and the # icon.

---

### Post by stardusthacker on 2016-08-05
Still not working. I deleted the recovery partitions. Now the disk management is showing 3 partitions. The C drive, Q drive(which I had made long back) and the UEFI partition. But EaseUS is showing 4 partitions. The 4th being the Reserved Partition. So, is it because the disk management is not showing the reserved partition that the Ubuntu installer cannot detect it either?


Edited: So the partition type is shown to be GPT. And windows allows 128 partitions on a GPT drive. Then why this issue?

---

### Post by oldfred on 2016-08-05
The reserved partition is a Windows required partition. It is unformatted so it may show as an error in gparted (missing format) but that is the requirement. And it is not the issue.

Are you sure fast startup is off in Windows?
And that no NTFS or FAT32 partitions need chkdsk? 
Those are the most common issues.

---

### Post by stardusthacker on 2016-08-05
Yes, the fast startup is off. Hibernation is off. Secure Boot is disabled. 
I just ran the chkdsk and no problems occurred. Still it won't detect.

Fast  Boot is off. Boot mode is UEFI. There is 40mb  of unallocated space. C drive (a primary partition). Another drive Q,  also a primary partition. An EFI partition. One reserved partition,  which the disk management does not show. And since the partition type is  GPT, there shouldn't be any question of limited number of primary  partitions, should there?

Seems like all the requirements are taken care of. I don't know what to do now.

---

### Post by oldfred on 2016-08-05
When you created partitions with Windows did you convert it from basic to dynamic? Dynamic does not work with Linux?

Post these:
sudo fdisk -lu
        sudo parted /dev/sda unit s print 
sudo gdisk -l /dev/sda

Also is drive set for AHCI in UEFI, not IDE nor RAID?

---

### Post by stardusthacker on 2016-08-05
The output for the first command was : 

```
Disk /dev/ram0: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram1: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram2: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram3: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram4: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram5: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram6: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram7: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram8: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram9: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram10: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram11: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram12: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram13: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram14: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram15: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/loop0: 1.3 GiB, 1433468928 bytes, 2799744 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 060B85DA-765F-446A-AEAD-07A509C23CB1

Device          Start        End    Sectors   Size Type
/dev/sda1        2048    1026047    1024000   500M EFI System
/dev/sda2     1107968    1370111     262144   128M Microsoft reserved
/dev/sda3     1370112 1441527175 1440157064 686.7G Microsoft basic data
/dev/sda4  1441527176 1953525127  511997952 244.1G Microsoft basic data
```

---

### Post by stardusthacker on 2016-08-05
The output for sudo parted /dev/sda unit s print was:
```
Model: ATA ST1000LM024 HN-M (scsi)
Disk /dev/sda: 1953525168s
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start        End          Size         File system  Name  Flags
 1      2048s        1026047s     1024000s     fat32        EF    boot, esp
 2      1107968s     1370111s     262144s                   Mi    msftres
 3      1370112s     1441527175s  1440157064s  ntfs               msftdata
 4      1441527176s  1953525127s  511997952s   ntfs               msftdata


```


Output for sudo gdisk -l  /dev/sda was:
```
GPT fdisk (gdisk) version 1.0.1

The protective MBR's 0xEE partition is oversized! Auto-repairing.

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sda: 1953525168 sectors, 931.5 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 060B85DA-765F-446A-AEAD-07A509C23CB1
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 1953525134
Partitions will be aligned on 8-sector boundaries
Total free space is 83941 sectors (41.0 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048         1026047   500.0 MiB   EF00  EF
   2         1107968         1370111   128.0 MiB   0C01  Mi
   3         1370112      1441527175   686.7 GiB   0700  
   4      1441527176      1953525127   244.1 GiB   0700  


```




No, I did not convert the partitions from basic to dynamic. 
Yes, it is AHCI. Not IDE or RAID.

---

### Post by oldfred on 2016-08-05
Looks like you forgot the space after the -l or before the /dev/sda?

Others look very normal.

Have you tried shrinking the larger NTFS partition with Windows and reboot so it can run chkdsk which is required after any resize.
While installer should see fully partitioned drive, it generally is better to shrink NTFS with Windows tools.

---

### Post by stardusthacker on 2016-08-05
Yes, I got that. Just edited that part.
Well, I can try shrinking it again. That's the C drive. The larger partition. But, I have this 40 MB of unallocated space which is to the left of the C drive. So, I cannot merge it now. 
I will try shrinking and rebooting it now.

---

### Post by oldfred on 2016-08-05
Note that gdisk said auto repairing but I think that is only in memory, not written back to drive unless you tell it.

> The protective MBR's 0xEE partition is oversized! Auto-repairing.


[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/) 
    
 sudo gdisk /dev/sda
Command (? for help):  
            Use gdisk and verify partitions are correct with p, or v to review issues,  and use w to write the partition table. If not correct just use q to quit. That should update primary, backup & protective MBR. Details:
[http://www.rodsbooks.com/gdisk/repairing.html](http://www.rodsbooks.com/gdisk/repairing.html)

---

### Post by stardusthacker on 2016-08-06
Output of command p
```
Disk /dev/sda: 1953525168 sectors, 931.5 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 060B85DA-765F-446A-AEAD-07A509C23CB1
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 1953525134
Partitions will be aligned on 8-sector boundaries
Total free space is 41043941 sectors (19.6 GiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048         1026047   500.0 MiB   EF00  EF
   2         1107968         1370111   128.0 MiB   0C01  Mi
   3         1370112      1400567175   667.2 GiB   0700  
   4      1441527176      1953525127   244.1 GiB   0700  

```


output of command v
```
No problems found. 41043941 free sectors (19.6 GiB) available in 4
segments, the largest of which is 40960000 (19.5 GiB) in size.


```


the w command says it will overwrite the existing partitions. So, I didn't proceed with that. Should I?

---

### Post by stardusthacker on 2016-08-06
I read the two links of rodsbooks.com but am confused. I mean am not sure what to do now.

---

### Post by oldfred on 2016-08-06
Only with the w command will the entry be updated. I would execute the w command.

You do have full backups of the system? You should not be making any major change to system without full backups and should have the backups as part of your normal system maintenance.

---

### Post by stardusthacker on 2016-08-11
Oh. No, I don't have backups of the system. I'll try after the backups then. 
Thanks for your help.

---

### Post by oldfred on 2016-08-11
discussion of alternatives/strategy backups
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)
[https://help.ubuntu.com/community/CategoryBackupRecovery](https://help.ubuntu.com/community/CategoryBackupRecovery)
[http://ubuntuforums.org/showthread.php?t=2236636](http://ubuntuforums.org/showthread.php?t=2236636)
[http://askubuntu.com/questions/2596/comparison-of-backup-tools](http://askubuntu.com/questions/2596/comparison-of-backup-tools)
If you install your own system you are the system admin
Sysadmins: Everything they told you about backup WAS A LIE
[http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/](http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/) 


Oldfred's list of stuff to backup May 2011 (still mostly current, see added links below):
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
Adding extra commands to rsync 
[http://ubuntuforums.org/showthread.php?t=2260658](http://ubuntuforums.org/showthread.php?t=2260658)
More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)
Some files(temp, cache etc) to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)
[http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders](http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders)
[http://askubuntu.com/questions/40992/what-files-and-directories-can-be-excluded-from-a-backup-of-the-home-directory/40997#40997](http://askubuntu.com/questions/40992/what-files-and-directories-can-be-excluded-from-a-backup-of-the-home-directory/40997#40997)

---

### Post by fabio.formosa on 2017-08-03
@[**[COLOR=#000000]stardusthacker[/COLOR]**]("https://ubuntuforums.org/member.php?u=2039914") How did you solve? I'm in the same case.

---

### Post by fabio.formosa on 2017-08-03
I've solved on my own: I've switched SATA from Intel Smart Technology to AHCI, into the BIOS setup panel.

---

### Post by oldfred on 2017-08-03
You often have to add AHCI drivers in Windows before chaging to AHCI in UEFI/BIOS settings.
[https://samnicholls.net/2016/01/14/how-to-switch-sata-raid-to-ahci-windows-10-xps-13/](https://samnicholls.net/2016/01/14/how-to-switch-sata-raid-to-ahci-windows-10-xps-13/)

---

