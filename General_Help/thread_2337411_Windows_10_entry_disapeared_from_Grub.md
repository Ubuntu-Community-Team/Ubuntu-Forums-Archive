---
title: "Windows 10 entry disapeared from Grub"
date: 2016-09-17
forum: General Help
---

### Post by guillaum2 on 2016-09-17
[COLOR=#111111][FONT=Ubuntu]Hello I had a dual boot with Xubuntu and Windows 10. Everything worked fine until tonight. I got this error when trying to boot on windows:

[/FONT][/COLOR]> [INDENT]error: no such device [UUID]
Setting partition type to 0x83
Press any key to continue ...
[/INDENT]


[COLOR=#111111][FONT=Ubuntu]When I pressed a key it went back to grub. I then booted on Xubuntu again and found the UUID for the windows partition with blkid and then compared it whith the entry in grub.cfg. As it wasn't the right UUID I replaced it in grub.cfg with the right one and rebooted but it didn't work.
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]On my second attempt I tried a sudo update-grub which did a bigger mess than it already was as it removed the windows 10 menuentry from grub.cfg
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Here is the link to the pastebin from boot-repair : [http://paste.ubuntu.com/23194498/](http://paste.ubuntu.com/23194498/)
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]If anyone knows what the problem is or what to do to find out that would be really apreciated.[/FONT][/COLOR]

---

### Post by leunam12 on 2016-09-17
Ubuntu 15.10 is no longer supported, I suggest you upgrade to 16.04 or downgrade to 14.04

---

### Post by Jimysbil on 2016-09-17
When you are booted on Xubuntu can you access this partition.
It could be a corrupted partition.
Also the partition ID should be set 0x07 (0x83 should be for an ext2 partition type).I would ask you if the /dev/sdXX you had on your windows menuentry was the right one but as long as you run update-grub and it isn't creating a menuentry I think your partition should be damaged.Use a Windows CD/DVD/USB and make a checkdisk.

---

### Post by oldfred on 2016-09-18
Windows only boots from, repairs or installs to a primary NTFS partition with the boot flag. Grub does not use boot flag (active partition in Windows) and just looks for bootmgr & BCD files to know which Windows partition to chainload to. It is possible to boot Windows in a logical partition if the Windows Boot partition (typically 100MB) is still a primary NTFS partition.

But you are not showing any larger primary NTFS partition with boot flag, nor bootmgr & BCD in any NTFS partition.

Windows 10 also has fast start up which is always on hibernation. The Linux NTFS driver will not mount NTFS that is hibernated nor if it needs chkdsk. So that may be why no Windows boot files not shown. If you have a Windows boot partition move boot flag back to it with gparted or Windows (set active), as it cannot be on a logical partition. And then use Windows repair tools to fix Windows.
       Windows 10 repair disk
[http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html](http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html)
[http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html)
Repair/backup/restore
[https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive](https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive)
[http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options](http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options)

---

