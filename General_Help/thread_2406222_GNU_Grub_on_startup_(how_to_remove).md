---
title: "GNU Grub on startup (how to remove?)"
date: 2018-11-17
forum: General Help
---

### Post by THEKINGDOM on 2018-11-17
Hi guys,

I've finally got around to posting this question after months of dealing with this. 
Every time I restart or start Ubuntu I'm greeted with the GNU Grub screen. I've tried repeatedly searching the internet for solutions on how to remove, but cannot find anything that works or is conclusive. 
[B]
Issue Started[/B]: when I updated to [B]Ubuntu 18.04LTS
[/B]
The only way to bypass this screen is by typing "exit" once or twice and then the system proceeds to boot as normal.

Please any help is greatly appreciated.
*tried posting attach[IMG]https://photos.google.com/photo/AF1QipPwky2dVT_1-tzz4b2BmHMPfCiVmg-C5HefLYGA[/IMG]ment, it's not allowing attachment.

---

### Post by #&amp;thj^% on 2018-11-17
The post by Gilles [here ]("https://askubuntu.com/questions/157925/how-do-i-skip-the-grub-menu-on-a-dual-boot-system")seems straight forward.

---

### Post by ajgreeny on 2018-11-17
Is Ubuntu your only OS or do you have another on your computer?

1fallen's link is for a dual boot system but if you really have only one OS we will need to look a bit deeper.
It will be best to see exactly where you are at present so go to **Boot-Repair** in my signature below and follow the instructions there to run the Boot-Info-Script.
You can do this either from a live system or your installed system. 

**Do not run any repair just yet** but simply copy back here the pastebin link you get which will show us a lot more about your system and we will be able to see if you have more than one OS.

---

### Post by THEKINGDOM on 2018-12-08
> **ajgreeny said:**
> Is Ubuntu your only OS or do you have another on your computer?

1fallen's link is for a dual boot system but if you really have only one OS we will need to look a bit deeper.
It will be best to see exactly where you are at present so go to **Boot-Repair** in my signature below and follow the instructions there to run the Boot-Info-Script.
You can do this either from a live system or your installed system. 

**Do not run any repair just yet** but simply copy back here the pastebin link you get which will show us a lot more about your system and we will be able to see if you have more than one OS.

Hi ajgreeny,
I'm not running a dual boot Ubuntu only.

Pastebin:
[http://paste.ubuntu.com/p/VYbkVV5G88/](http://paste.ubuntu.com/p/VYbkVV5G88/)

---

### Post by THEKINGDOM on 2019-01-05
BUMP.

Can anybody assist? I'm not running a dual boot

Thanks in advance

---

### Post by oldfred on 2019-01-06
Is system shutting down normally?
Grub sets flag & as part of normal shutdown unsets it. But if not shutdown correctly, it sees flag & presents grub menu so you can run repairs or recovery boot.

Do not know ZFS, does that require extra commands to shutdown correctly?
Boot-Repair did not have ZFS driver, so could not mount it, but gave a lot of errors on trying to mount as NTFS. You can ignore those.
Also report is not updated to include all the details on NVMe drives.

Are you booting in the 35 year old BIOS/MBR configuration with a new system and very new NVMe drive? 
Looks like you booted Boot-Repair in BIOS mode. Not then sure about install.

---

### Post by THEKINGDOM on 2019-01-06
Hi all the equipment is new. No 35 year old BIOS/MBR. 
No dual boot. 
Computer shuts down normally and restarts normally but it hits the GRUB screen whenever doing a restart or turning the computer back on. 

Any help would be greatly appreciated.
Thank you

---

### Post by THEKINGDOM on 2019-01-14
@ajgreeny Did you have a chance to review my Boot-Info-Script?

Thanks in advance

---

### Post by THEKINGDOM on 2019-03-23
guys can anybody help with this? I'm trying to prevent a complete system reinstall..  it's not affecting my system performance or anything else but it really sucks having to type exit every single time I startup my system.
Help is greatly appreciated

---

### Post by oldfred on 2019-03-30
Only a few run ZFS, so if that is issue then not many will be able to help.

Is UEFI fully updated, if SSD is firmware updated?

Is issue only on cold boot, but also on warm reboot?

Quick search found this.
Often Arch has good technical info and much of it applies to any Linux.
[https://wiki.archlinux.org/index.php/Installing_Arch_Linux_on_ZFS](https://wiki.archlinux.org/index.php/Installing_Arch_Linux_on_ZFS)
Seems like a bug with grub & ZFS & special requirements to work around it.

---

### Post by THEKINGDOM on 2019-03-30
I'm not running ZFS on the boot drive.
ZFS should only be running on a RAID drive setup I have for general storage..
Do the boot logs say otherwise?

---

### Post by oldfred on 2019-03-30
Your Boot-Repair report expired. 
Post a new one.

---

### Post by THEKINGDOM on 2019-03-31
> **oldfred said:**
> Your Boot-Repair report expired. 
Post a new one.


New one, thanks:

[http://paste.ubuntu.com/p/pgh5YtK3tr/](http://paste.ubuntu.com/p/pgh5YtK3tr/)

---

### Post by oldfred on 2019-03-31
Do not run any autofix in Boot-Repair. 
Not sure if advanced mode works with your configuration or not.

Report has not been updated to show details on NVMe drives. And it looks like Boot-Repair does not like ZFS drives either.

But issues then really are only on NVMe drive as that is boot drive.

It looks like you have newer UEFI hardware system, but are booting in old BIOS boot mode.
Generally BIOS works, but there may be some issues where BIOS drivers are not as complete as UEFI drivers. Microsoft did not want vendors to update or create any new BIOS drivers in 2012 when it released Windows 8. But demand by large users overrode that.
Ubuntu developers work separately, but since UEFI has been standard since 2012 for vendor hardware, not sure  what status is. Many still use BIOS boot only older systems with Ubuntu. And I have seen users with standard hardware use BIOS.
But you have NVMe drive and ZFS.

Have you updated UEFI?
And many NVMe drives need firmware update, but most only offer that via Windows tools.

---

### Post by THEKINGDOM on 2019-04-01
> **oldfred said:**
> Do not run any autofix in Boot-Repair. 
Not sure if advanced mode works with your configuration or not.

Report has not been updated to show details on NVMe drives. And it looks like Boot-Repair does not like ZFS drives either.

But issues then really are only on NVMe drive as that is boot drive.

It looks like you have newer UEFI hardware system, but are booting in old BIOS boot mode.
Generally BIOS works, but there may be some issues where BIOS drivers are not as complete as UEFI drivers. Microsoft did not want vendors to update or create any new BIOS drivers in 2012 when it released Windows 8. But demand by large users overrode that.
Ubuntu developers work separately, but since UEFI has been standard since 2012 for vendor hardware, not sure  what status is. Many still use BIOS boot only older systems with Ubuntu. And I have seen users with standard hardware use BIOS.
But you have NVMe drive and ZFS.

Have you updated UEFI?
And many NVMe drives need firmware update, but most only offer that via Windows tools.

updating UEFI right now, let's see what happens. Thanks

---

### Post by THEKINGDOM on 2019-04-01
> **THEKINGDOM said:**
> updating UEFI right now, let's see what happens. Thanks

updated issue still here.
I thought it was an easy fix to move past the GRUB screen. I have to type "exit" every time to boot ubuntu..

---

### Post by oldfred on 2019-04-01
Boot-Repair uses bootinfoscript as first part of report, but bootinfoscript has not been updated to include NVMe drives.
[https://github.com/arvidjaar/bootinfoscript/issues/5](https://github.com/arvidjaar/bootinfoscript/issues/5)
A user posted an updated version in bug report, could you download it and run it. It is command line only. And if longer post in code tags, or if too long you have to manually upload to a pastebin site.

Not sure it will show anything. Probably more curious if it works on a NVMe drive. And if it works we can report that, so maybe fix gets incorporated into bootinfoscript & then Boot-Repair.

---

### Post by THEKINGDOM on 2019-11-06
Hi guys, circling back here. 
I'm using an Intel M.2 PCIe 3.0 x4 128GB-SSD --- as the boot drive.

This issue was _not always occuring_ it started if I recall a the update to Ubuntu 18.04

I really need help here to fix this issue please, I've tried a GRUB purge-reinstall/repair.. still having the GRUB screen everytime I restart computer. 

New Boot-Repair log below:
[http://paste.ubuntu.com/p/PBxyry8Fm5/](http://paste.ubuntu.com/p/PBxyry8Fm5/)

---

### Post by oldfred on 2019-11-07
Have you updated UEFI and SSD firmware?
Many have solved various issues, just with firmware updates, even on new hardware.

---

### Post by THEKINGDOM on 2019-11-07
> **oldfred said:**
> Have you updated UEFI and SSD firmware?
Many have solved various issues, just with firmware updates, even on new hardware.

Hi, thanks for the help. 
I'm going to update the bios, I'm a couple of versions behind. However, ASRock website is saying: * Please install "[AMD all in 1 with VGA driver ver:18.50.16.01_WHQL]("http://asrock.pc.cdn.bitgravity.com/Drivers/AMD/AllIn1/AllIn1(v18.50.16.01_WHQL).zip")" or a later version before updating to this BIOS." -- I can't seem to find the Ubuntu compatible install file to update the AMD VGA drivers. 
Any suggestions?

I am running a Nvidia EVGA GTX 1070 - so I assume I'm not relying on the integrated graphics. Is this still necessary when operating outside of the dedicated graphics card?

---

### Post by oldfred on 2019-11-07
Do not know AMD well, seen several posts.

I believe newer versions of Ubuntu will now see your nVidia card & install drivers as part of install, if you select that.
Before you always had to use nomodeset both for live installer & first boot or until you install nVidia driver.
AMD had its own drivers, and supposedly just works as does Intel. But AMD also has a update or pro version also.

Very new AMD Ryzen based boards had to have a UEFI/BIOS update to work with 19.10 (only).
AMD UEFI/BIOS update for Ryzen 3000 series
[https://www.phoronix.com/scan.php?page=news_item&px=Ryzen-3000-BIOS-Update-Good](https://www.phoronix.com/scan.php?page=news_item&px=Ryzen-3000-BIOS-Update-Good)
AMD Releases BIOS Fix To Motherboard Partners For Booting Newer Linux Distributions July 2019
[https://www.phoronix.com/scan.php?page=news_item&px=AMD-Releases-Linux-Zen2-Fix](https://www.phoronix.com/scan.php?page=news_item&px=AMD-Releases-Linux-Zen2-Fix)
[https://www.phoronix.com/scan.php?page=article&item=ryzen-3700x-3900x-linux&num=2](https://www.phoronix.com/scan.php?page=article&item=ryzen-3700x-3900x-linux&num=2)
400 series cchipsets need BIOS/UEFI update for Ryzen 3000, 500 seires standard with 3000
[https://ubuntuforums.org/showthread.php?t=2430149&p=13904266#post13904266](https://ubuntuforums.org/showthread.php?t=2430149&p=13904266#post13904266)

It looks like Boot-repair is reinstalling grub in BIOS boot mode. But report has not been updated to show all the details on NVMe drives, so cannot tell all info.
Probably better to be in UEFI boot mode, but then drive must be gpt and you have to have an ESP - efi system partition.

A lot of errors with report are trying to see partitions as NTFS which they are not. You can ignore those.
May need to add zfs driver & manually mount those partitions if you want to eliminate some of the extraneous error messages.

---

### Post by THEKINGDOM on 2019-11-07
> **oldfred said:**
> Do not know AMD well, seen several posts.

I believe newer versions of Ubuntu will now see your nVidia card & install drivers as part of install, if you select that.
Before you always had to use nomodeset both for live installer & first boot or until you install nVidia driver.
AMD had its own drivers, and supposedly just works as does Intel. But AMD also has a update or pro version also.

Very new AMD Ryzen based boards had to have a UEFI/BIOS update to work with 19.10 (only).
AMD UEFI/BIOS update for Ryzen 3000 series
[https://www.phoronix.com/scan.php?page=news_item&px=Ryzen-3000-BIOS-Update-Good](https://www.phoronix.com/scan.php?page=news_item&px=Ryzen-3000-BIOS-Update-Good)
AMD Releases BIOS Fix To Motherboard Partners For Booting Newer Linux Distributions July 2019
[https://www.phoronix.com/scan.php?page=news_item&px=AMD-Releases-Linux-Zen2-Fix](https://www.phoronix.com/scan.php?page=news_item&px=AMD-Releases-Linux-Zen2-Fix)
[https://www.phoronix.com/scan.php?page=article&item=ryzen-3700x-3900x-linux&num=2](https://www.phoronix.com/scan.php?page=article&item=ryzen-3700x-3900x-linux&num=2)
400 series cchipsets need BIOS/UEFI update for Ryzen 3000, 500 seires standard with 3000
[https://ubuntuforums.org/showthread.php?t=2430149&p=13904266#post13904266](https://ubuntuforums.org/showthread.php?t=2430149&p=13904266#post13904266)

It looks like Boot-repair is reinstalling grub in BIOS boot mode. But report has not been updated to show all the details on NVMe drives, so cannot tell all info.
Probably better to be in UEFI boot mode, but then drive must be gpt and you have to have an ESP - efi system partition.

A lot of errors with report are trying to see partitions as NTFS which they are not. You can ignore those.
May need to add zfs driver & manually mount those partitions if you want to eliminate some of the extraneous error messages.

Thank you
Indeed my Nvidia drivers are fully up to date. The package posted by ASRock was to update the integrated graphics on the motherboard and they'd said via phone all also to update firmware on the motherboard

Just to clarify the ZFS drives are not actaually partitions, they are separate drives for media that I only use for media, in a RAID-1 ZFS for data integrity. No OS or boot data should reside on those drives. 
On my boot drive Intel SSD NVMe - there should be no ZFS at all..?

You'd mentioned "Boot-repair is reinstalling grub in BIOS boot mode. But report has not been updated to show all the details on NVMe drives, so cannot tell all info.
Probably better to be in UEFI boot mode, but then drive must be gpt and you have to have an ESP - efi system partition." 
- How can I have boot-repair reinstall grub in UEFI boot mode vs BIOS boot mode? 

I'm also coincidentally planning to install Win10 to a separate drive for dual boot this evening if I can get to it. I'm not sure how that may impact any steps I take to fix this issue now.

---

### Post by THEKINGDOM on 2019-11-07
> **oldfred said:**
> Do not know AMD well, seen several posts.
A lot of errors with report are trying to see partitions as NTFS which they are not. You can ignore those.
.

[COLOR=#000000][s][/COLOR]Damn! after all this time it's FIXED! [COLOR=#000000][/s] - Issue returned once I switched motherboard during a migration from AMD hardware back to Intel.
[/COLOR]
I went into the UEFI and remove the fall back boot drive options and disabled the ZFS drives (as options for boot), I have no idea why they were selected as potential boot drive fall backs..... 
Now it boots straight to my default SSD/Ubuntu-OS right away.
I'm not sure why it was showing a GRUB screen every time on startup but it seems as if it wasn't defaulting to any one particular boot drive..?

Thank you for the help here!

---

### Post by oldfred on 2019-11-07
If drive is MBR, not easy to convert to UEFI boot. UEFI normally uses gpt partitioning and Windows requires gpt for UEFI boot or MBR for BIOS boot.
With Ubuntu you can boot in UEFI mode from MBR, but that is not the UEFI standard.

Probably easier just to backup your data and do a new clean install in UEFI boot mode.
Converting from MBR to gpt:
[http://ubuntuforums.org/showthread.php?t=1454252](http://ubuntuforums.org/showthread.php?t=1454252)

Both Windows & Ubuntu install in the mode that you use to boot install media. 
More details on UEFI in link in my signature.

---

### Post by THEKINGDOM on 2019-11-09
> **oldfred said:**
> If drive is MBR, not easy to convert to UEFI boot. UEFI normally uses gpt partitioning and Windows requires gpt for UEFI boot or MBR for BIOS boot.
With Ubuntu you can boot in UEFI mode from MBR, but that is not the UEFI standard.

Probably easier just to backup your data and do a new clean install in UEFI boot mode.
Converting from MBR to gpt:
[http://ubuntuforums.org/showthread.php?t=1454252](http://ubuntuforums.org/showthread.php?t=1454252)

Both Windows & Ubuntu install in the mode that you use to boot install media. 
More details on UEFI in link in my signature.

Thanks for the info oldfred. 
Based on PasteBin Boot Repair Summary - It appears I'm already GPT, not MBR.
PasteBin Boot Summary - "[COLOR=#000000]nvme0n1    : GPT,    BIOS_boot,    has-correctEFI,     not-usb,    not-mmc, has-os"[/COLOR] 
[COLOR=#000000]Image below from Gparted:
[/COLOR]
[ATTACH=CONFIG]284363[/ATTACH]

I've just changed my motherboard/CPU from AMD to Intel, thought I'd elimited the GRUB screen showing on start-up (back on AMD the day prior) but now it's back again with the new MSI motherboard. Even with the latest bios firmware updates and disabling boot drive alternatives/priorities, still won't seem to prevent it from showing on boot. 
I'm booting in either UEFI or UEFI/Legacy to show drives. 

>  Probably easier just to backup your data and do a new clean install in UEFI boot mode. 
Did you mean to do a clean install of Ubuntu all together and enable UEFI? 

At this point with the consistent issues fo GRUB screen appearing on startup I'm quite happy to do a complete re-install, this has been going on for a year and can't find a reliable fix to prevent the GRUB screen from showing on startup, not understanding why it's occuring the first place. 
My quick method to "_bypass the GRUB Screen_ " has been to type "**exit" each time **but it's very annoying to have to do this every time on startup. 
You may also notice that GParted shows a partition "grub2 core.img" 1MiB filesize - not sure what this signifies..?

**PasteBin log (for reference):**
[http://paste.ubuntu.com/p/9WjWk2smF5/](http://paste.ubuntu.com/p/9WjWk2smF5/)


Again any help anybody can provide is greatly appreciated

---

