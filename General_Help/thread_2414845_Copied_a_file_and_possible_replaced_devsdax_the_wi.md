---
title: "Copied a file and possible replaced /dev/sdax the windows partition"
date: 2019-03-15
forum: General Help
---

### Post by joeraid on 2019-03-15
I copied a file into /dev/sda3 thinking that it was the root directory of my windows partition (C:\). The result is that I no longer see an entry for the partition in "Other Locations" and, of course, I can no longer boot into windows (for the few first attempts windows gave a message about using the recovery option from the installation disk but is no longer the case after I used testdisk. The screen now hangs and the computer reboots upon pressing Enter). Some of the suggestions that I read online about windows failing to load involved working with testdisk. After using it for a while I landed on the option "rebuild boot sector" which, I suppose, failed with the following message: "Extrapolated boot sector and current boot sector are different". I was however successful at recovering my most needed files by selecting the "list" option under "boot" (not sure if this was available before I ran "rebuild boot sector"). Now, I don't have much at stake but I do wish to bring windows back without having to re-install since I read people usually run into issues installing windows atop an existing installation of Linux. I'm currently on my ubuntu partition with dual boot set up and was hoping if there is something I can do from ubuntu since I don't have the windows installation disk currently available to me right now (although if a solution pops up requires it, I will sure try to obtain one as soon as possible). Any help on the matter would be appreciated, thanks.

---

### Post by oldfred on 2019-03-15
Testdisk used to create a XP type partition boot sector & then you had to run chkdsk from your version of Windows to convert to Windows 7 or later type boot sector. Not sure if updated or not, yet.

Do not run auto-fix until someone has reviewed report. Often advanced repairs are better, or you need Windows repairs, which Boot-Repair cannot fix.
       May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by joeraid on 2019-03-16
Boot-Repair report: "http://paste.ubuntu.com/p/6YPbPJbScY/". I would like to re-affirm that the windows entry in the partition table was sda3. Thanks for your time.

---

### Post by oldfred on 2019-03-16
It is not even seeing any type on your NTFS partition sda3.
Or it does not look like you either recovered the back up Boot sector nor wrote a new one.
I would first try testdisk again as Windows will not let you run chkdsk unless it is seen as NTFS. try first to recover a backup boot sector, if not create a new BS.
Then you have to run chkdsk using your Windows repair disk.

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

---

### Post by joeraid on 2019-03-16
Following your last suggestion, I used testdisk and ran "Backup BS". "Rebuild BS" now returns the following message: "Extrapolated boot sector and current boot sector are identical". I now also can use the "Undelete" option to recover deleted files in windows and am able to "List" the files from lost partition. Previously those two options from the **main** **menu** returned a message about the file system being missing or possibly corrupted. The windows partition is listed under "Other Locations" but I can't mount it. I receive the following error when I try to mount it: "Unable to access location. Volume not mounted". I am still unable to boot into windows from the grub menu. Is this my cue to run "[COLOR=#000000]chkdsk"?[/COLOR] I generated a second Boot-Repair report "[http://paste.ubuntu.com/p/f5G72b7QVX/](http://paste.ubuntu.com/p/f5G72b7QVX/)". Thanks for your time.

---

### Post by oldfred on 2019-03-16
Now you are showing grub in the PBR. And you never can have grub in the partition boot sector of a NTFS partition as Windows has to have its own info in it.
Go back to previous post.
If it shows BS & backup BS as identical, you must have installed grub twice, so backup is also corrupted.
Use the testdisk command to run the rebuild BS. Then you should be able to run chkdsk from a boot of Windows and f8 for its repair console.

---

