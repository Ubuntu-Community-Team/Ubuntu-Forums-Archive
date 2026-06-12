---
title: "Recover Win8 partitions after messing up with raid and installing Ubuntu 12.04"
date: 2013-12-05
forum: General Help
---

### Post by misha-2 on 2013-12-05
Hello everyone!
[COLOR=#333333][FONT=Ubuntu]Recently I've bought a new laptop (Asus Zenbook Prime UX31A), with Win8 preinstalled. For 2 years I've been using Ubuntu, so the decision was made to install Ubuntu 12.04 along with existing Win8 to dual-boot.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]In order to do that, I downloaded an image to make LiveUSB and install from it. However, the notion of '64-amd' verstion confused me, so I preferred 32-bit. That was an awful mistake: grub wouldn't work at all, and my installation process showed me something like 'grub-install failed on /dev/sda'. While running installation after installation, I've sort of ruined my partition table (it happened after taking some action in GParted, but I'm not so sure) and Win8 refused to boot anymore - only LiveUSB.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]After a night of trial and error, finally I've installed** 64-bit Ubuntu 12.04 from UEFI mode**, and used* boot-repair* tool to set up grub correctly (log [http://http://paste.ubuntu.com/6498097/](http://http://paste.ubuntu.com/6498097/)). Ubuntu is on /dev/sda (first SSD disk), while /dev/sdb is the other, with many corrupted partitions and damaged filesystem.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]The hard part for me is that this laptop has 2 64Gb SSD disks, previously connected into RAID with GPT partitions on them. At this moment Ubuntu is presented on just one of them, and can't see the other. Moreover, I'm still hoping that Win8 is presented somewhere on that other disk, I recall there was a 'Recovery' partition 20Gb\NTFS and somewhat like 40-50Gb Win8 partition, with a bunch of others (like boot partition).[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]So, the questions are - how do I access data on that other disk? Is it possible? Will I be able to recover Win8?[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]I've read through a bunch of web-pages describing data recovery on GPT partitions (like [/FONT][/COLOR][https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)[COLOR=#333333][FONT=Ubuntu] or *testdisk* guide), but it all got mixed in my head, and having 2 disks that were somehow connected totally blows my mind.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]What I've done after success in Ubuntu installation is running *testdisk *several times to look at what partitions it can find. Last (and the first) time I've written something with testdisk is this [/FONT][/COLOR][http://paste.ubuntu.com/6513295/](http://paste.ubuntu.com/6513295/)[COLOR=#333333][FONT=Ubuntu].[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]I'm scared to take further steps in recovering. For example, when* testdisk *shows that I have 20Gb partition, though I totally can not access it - I have no idea, what is wrong and what should I do. Please, someone, sort it out for me - how to recover another SSD disk? I want my Win8 back.[/FONT][/COLOR]

---

### Post by oldfred on 2013-12-05
Another with similar issues.
       Asus Zenbook Prime UX31A (UEFI)  Blank screen resolved by turning secure boot off, many tests of Boot parameters
[http://ubuntuforums.org/showthread.php?t=2086054](http://ubuntuforums.org/showthread.php?t=2086054)

I did not know these have dual SSDs with RAID.
The desktop installer does not have RAID drivers, the server installer does.

I know very little about RAID as most desktops do not have it and it is even more unusual to have dual SSD. It proably depends on what type of RAID it was. If it was RAID 0 it is broken as part of all data is on each drive. If RAID 1 that is a mirror and each drive should show entire system.

Your sdb looks like a standard Ubuntu UEFI install with efi, / (root) and swap partitions using entire sdb drive.
But you sdc has no semblance to a Windows install. You can only have one efi partition and you are showing 3.

Not sure what testdisk is showing and also not sure if RAID is part of issue.
This is typical Windows gpt partitions for UEFI boot, but vendors may have recovery in different places.

 Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)
Windows technical info on gpt and GUIDs
[http://msdn.microsoft.com/library/windows/desktop/aa365449](http://msdn.microsoft.com/library/windows/desktop/aa365449)
Order on drive is important: msftres
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)
Windows 8 info
[http://technet.microsoft.com/en-us/library/hh824947.aspx](http://technet.microsoft.com/en-us/library/hh824947.aspx)

You should check with your vendor and see if you can get an install image for your drive. That would not be a full install but the recovery partition or image of drive as installed. Some may offer it for just a nominal charge. Otherwise you may need to purchase a new copy of Windows.

---

### Post by dragonfly41 on 2013-12-05
I do recommend posting your problem on testdisk forum .. I found the author to be very helpful.

[http://forum.cgsecurity.org/phpBB3/](http://forum.cgsecurity.org/phpBB3/)

You may be advised to clone your data and then work on recovery from the cloned data.

---

