---
title: "boot repair issues with pastebin( 16.04)(Windows not loading)(sound driver issues)"
date: 2019-02-10
forum: General Help
---

### Post by rithviksharma on 2019-02-10
I had performed the recommended boot repair.
However, 


[LIST]
[*]I am still  not able to boot into Windows( laptop hangs).
[*] Ubuntu screen is also  frozen for 5 minutes on booting.
[*]The sound system has to be reset on  every boot(unmute using alsamixer).
[/LIST]

During the repartition of my dual boot( 16.04 and windows 10), during the usb live boot( "try linux"), I had encountered grub rescue.
 I used the following commands to get out of there from this link:[https://askubuntu.com/questions/142300/how-to-fix-error-unknown-filesystem-grub-rescue](https://askubuntu.com/questions/142300/how-to-fix-error-unknown-filesystem-grub-rescue) 
```
set root=(hd0,6)
set prefix=(hd0,6)/boot/grub
insmod normal
normal

```  Now once you boot into Ubuntu, run the following two commands as well:
  ```
sudo update-grub
sudo grub-install /dev/sda

```


[LIST]
[*]After this I simply repartitioned my system ( allocated extra 100 GB to linux from initial 20GB).
[*]I encountered multiple problems after this ( my mouse  pointer wouldn't be visible sometimes- I managed to solve this). My windows partition couldn't be detected for which I ran the recommended boot repair ( pastebin link is given)
[/LIST]
Currently my linux works fine apart from the problems listed above.
For sound, I used to run the the following commands and reboot after which it was temporarily fixed until the next boot.

```

echo options snd-hda-intel model=auto | sudo tee -a /etc/modprobe.d/alsa-base.conf
sudo alsamixer 
shutdown -h now


```
However even these don't work now
  


link to pastebin
[http://paste.ubuntu.com/p/dWXNGNb6jR/](http://paste.ubuntu.com/p/dWXNGNb6jR/)

---

### Post by yancek on 2019-02-10
The problems shown in boot repair are almost all in regard to the second partition (sda2).  What is/was that partition?  Windows 10 is generally (if pre-installed) UEFI/GPT which yours is not but is rather a Legacy/MBR install with msdos partitionng.  It looks like the first small partition (sda1) is a boot partition as it has the expected boot files.  However, neither sda2 or sda3 show any boot files.  Normally the show in boot repair although because they don't show, does not necessarily mean they are not there.

I see that you have Grub Legacy installed in the boot sector of sda2, the problem partition.  Ubuntu has not used Grub Legacy in over 9 years so I"m not sure where that came from?  The additional problem with it is that it is on a windows ntfs partition which should not happen.   Your windows boot files on sda2 may have been overwritten when Grub Legacy was mistakenly written to that partition.  Note on line 1060 of boot repair the reference to the software Flexnet.  That combined with Grub Legacy on the windows partition is part of the problem.

The manual boot method you post referencing "set root=(hd0,6)", was that after you re-installed Grub and re-partitioned?  Reason I ask is because that would be sda6 and that is shown as your swap partition??  The grub.cfg file shows Ubuntu booting from sda5 (hd0,5).  The grub.cfg file also shows a correct entry for windows pointing to the boot partition (sda1).  Unfortunately, the additional boot files needed that should be on the system partition (sda2?) do not exist.  

If you want to repair windwos, you will need a windows 10 installation DVD, a recovery CD with the Repair option or some type of windows recovery software you can download from the microsoft site.

---

### Post by oldfred on 2019-02-10
NTFS does keep a backup Boot sector or PBR, you may be able to recovery that with testdisk.
Windows repair tools will not work with grub installed in PBR as then it is not seen as a Windows partition.

       [http://www.ntfs.com/fat-partition-sector.htm](http://www.ntfs.com/fat-partition-sector.htm)
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

---

### Post by rithviksharma on 2019-02-10
That was a typo, the command I gave was "set root=(hd0,5)". This was  before I repartitioned. The grub rescue opened when I put in the live  usb after which I reinstalled grub.

---

