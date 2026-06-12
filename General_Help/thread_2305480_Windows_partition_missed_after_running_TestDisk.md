---
title: "Windows partition missed after running TestDisk"
date: 2015-12-06
forum: General Help
---

### Post by LecJackS on 2015-12-06
I have my computer with Ubuntu in one partition and Windows 10 (yeah, I know) in another (two ntfs, one for windows, one bigger for data).

A few days ago, I updated Windows, and it seems to be a BIG update because it downloaded tons of data, and seems to be a complete update of the system. I didn't know that until it started installing it as it was an entire new version of windows.

I know that I'll have problems with my boot after that, but it was too late to go back.

First part of the installation finished, restarted, no grub, no nothing. Classic.

So I used [Boot Repair Disk]("https://help.ubuntu.com/community/Boot-Repair") to solve it. Didn't work.

I choose the windows partition to boot from there (in the advanced options), and it worked, but I cannot make it to work with the ubuntu partition ("NTLDR missing" message at booting).

So I used TestDisk (booted from the Boot Repair Disk) and improvised from there. I find my ubuntu partition and tag it as bootable (before that, the one as tagged as boot was the windows one).

Then I use the Recommended Repair (again) on Boot Repair Disk, and it freaking worked.

Obviously, my Windows partition was now missing and showed as Free F*cking Space.

Now, I tried running Boot Repair with the "Repair File System" option checked, then CHKDSK but there is no partition to check, and also used another tool from the windows boot cd to recover missing partitions, but it just detected like a dozen of 1MB partitions.

I'm not sure what to do now. I can format that partition and start again, but I would prefer to repair it, not because the data on that partition, but just to learn how to do it and understand better how it works.

BootInfo sumary from Boot Repair: [http://paste.ubuntu.com/13750121/]("http://paste.ubuntu.com/13750121/")

My partitions right now:
[IMG]http://i.imgur.com/ngrwK2L.png[/IMG]

---

### Post by oldfred on 2015-12-06
You are showing Windows boot files in sdb? What is that? And was that how you booted Windows?

The small unallocated at end of drive is just because of the new larger block sizes or 4K sectors for compatiblity with new drives & SSD. You always had some unused sectors, some required just for separation, but now the spaces are large enough gparted shows them.
 Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)
it's 8-sector (4096-byte) alignment
[http://ubuntuforums.org/showthread.php?t=1768635](http://ubuntuforums.org/showthread.php?t=1768635)

---

### Post by LecJackS on 2015-12-07
> **oldfred said:**
> You are showing Windows boot files in sdb? What is that? And was that how you booted Windows?
sdb1 is a bootable windows usb, with which I tried to repair the partition using chkdsk.

In this computer, I installed windows first, and then ubuntu. So it used to boot from the ubuntu grub, and select OS from there.

> **oldfred said:**
> The small unallocated at end of drive is just because of the new larger block sizes or 4K sectors for compatiblity with new drives & SSD. You always had some unused sectors, some required just for separation, but now the spaces are large enough gparted shows them.
 Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)
it's 8-sector (4096-byte) alignment
[http://ubuntuforums.org/showthread.php?t=1768635](http://ubuntuforums.org/showthread.php?t=1768635)
Thank you for this information!

---

### Post by oldfred on 2015-12-07
For chkdsk to work, you partition has to be NTFS. And Windows does not use partition table as much as the partition boot sector (BS or PBR). While Boot-Repair's summary report says it is ok and is Windows it still can have issues.

You can try using bootsect.exe to replace the PBR.
       How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
Use bootsect.exe to repair XP & older or Vista/7 bootsectors - Use diskpart, then list volumes to see which drive to use 
bootsect.exe /nt52 c:  *compatible* with operating systems older (XP) than Windows Vista.
bootsect.exe /nt60 c:  *compatible* with Windows Vista, Windows Server 2008 or later

---

