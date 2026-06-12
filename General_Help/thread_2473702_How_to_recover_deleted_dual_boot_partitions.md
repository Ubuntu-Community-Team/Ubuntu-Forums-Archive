---
title: "How to recover deleted dual boot partitions?"
date: 2022-04-11
forum: General Help
---

### Post by csete on 2022-04-11
OK.  I'm an idiot.  I wasn't paying attention to which drive was selected in GParted and just deleted all of my partitions with the exception of my primary Ubuntu partition that I'm currently running on top of.  That includes, the UEFI, Dell Restore, Windows (dual boot), etc.  While I have data backups and can rebuild from scratch, I'm wondering if there is any "easy" way to rebuild the partition table?  I've just created a databackup again for my primary Ubuntu partition, but I'm holding off any sort of reboot until I can figure out my best next steps.

Thanks for any insights for someone that clearly wasn't paying enough attention.
Craig

---

### Post by #&amp;thj^% on 2022-04-11
I've done this once myself, and I was Lucky using: [https://www.simplified.guide/linux/disk-recover-partition-table](https://www.simplified.guide/linux/disk-recover-partition-table)
Good Luck

---

### Post by oldfred on 2022-04-11
Have you rebooted?
If not it could be easier.
If not rebooted recover partition:
[http://ubuntuforums.org/showpost.php?p=10364557&postcount=34](http://ubuntuforums.org/showpost.php?p=10364557&postcount=34)

Otherwise Testdisk, but it may show multiple sets of partitions as if you changed several times, it finds all of them. You have to select correct set that matches what you have/had. 
You can also use parted rescue if you know partitions approx start & end.
[https://www.cgsecurity.org/wiki/TestDisk](https://www.cgsecurity.org/wiki/TestDisk)
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

Used parted rescue
[https://ubuntuforums.org/showthread.php?t=2362656](https://ubuntuforums.org/showthread.php?t=2362656)
[http://ubuntuforums.org/showthread.php?t=2315405](http://ubuntuforums.org/showthread.php?t=2315405)
backup partition table before any changes, so you can get back to current if changes not correct
sudo sfdisk -d /dev/sda > PT_sda.txt
So you know sectors:
sudo parted /dev/sda unit s print

---

### Post by psychohermit on 2022-04-11
Bummer.  You can't reboot until you have recovered the EFI partition.

Best of luck recovering!
--glenn

---

### Post by csete on 2022-04-11
> **psychohermit said:**
> Bummer.  You can't reboot until you have recovered the EFI partition.

Best of luck recovering!
--glenn

Is that true even if I want to boot from an Ubuntu USB stick?  I just want to make sure I understand my situation which is why I've waited to reboot.  Reading about "testdisk", it seems like the safer option, even if it gives me some extra entries I need to clean up.

---

### Post by csete on 2022-04-11
> 

Otherwise Testdisk, but it may show multiple sets of partitions as if you changed several times, it finds all of them. You have to select correct set that matches what you have/had. 
You can also use parted rescue if you know partitions approx start & end.
[https://www.cgsecurity.org/wiki/TestDisk](https://www.cgsecurity.org/wiki/TestDisk)
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)


Given that I haven't rebooted yet is there any way to gather this information to successfully drive Testdisk?  The reality is that I don't believe I've changed partitioning since I did the original dualboot installation, but if there is a way to handle then I'd like to set myself up for "hopeful" success.

---

### Post by #&amp;thj^% on 2022-04-11
> **csete said:**
> Is that true even if I want to boot from an Ubuntu USB stick?  I just want to make sure I understand my situation which is why I've waited to reboot.  Reading about "testdisk", it seems like the safer option, even if it gives me some extra entries I need to clean up.
Just install testdisk on your current running OS.

---

### Post by csete on 2022-04-11
> **oldfred said:**
> 
Otherwise Testdisk, but it may show multiple sets of partitions as if you changed several times, it finds all of them. You have to select correct set that matches what you have/had. 
You can also use parted rescue if you know partitions approx start & end.
[https://www.cgsecurity.org/wiki/TestDisk](https://www.cgsecurity.org/wiki/TestDisk)
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)


I think I may be seeing what you mentioned here:
```

TestDisk 7.1, Data Recovery Utility, July 2019
Christophe GRENIER <grenier@cgsecurity.org>
https://www.cgsecurity.org

Disk /dev/nvme0n1 - 1024 GB / 953 GiB - CHS 976762 64 32
     Partition               Start        End    Size in sectors
>P EFI System                  2048     391167     389120 [EFI System Partition] [ESP]
 D MS Data                   653312  732344319  731691008 [OS]
 D MS Data                   653312 1997068287 1996414976 [OS]
 D Linux filesys. data    732344320 1961144319 1228800000
 D MS Data               1929277441 1963171840   33894400
 D MS Data               1959116801 1961144320    2027520
 D MS Data               1961144320 1963171839    2027520 [WINRETOOLS]
 D MS Data               1963171840 1997066239   33894400 [Image]
 D MS Data               1993758721 1997068288    3309568
 D MS Data               1997068288 2000377855    3309568 [DELLSUPPORT]

```

I haven't made any changes yet because I'm not sure what is safe here.  Suggestions appreciated.

Thanks,
Craig

---

### Post by csete on 2022-04-11
Looking a little closer, it seems like this is the key:
```
NTFS found using backup sector, blocksize=4096, 1022 GB / 951 GiB
```

---

### Post by csete on 2022-04-11
Some progress to report.  I was able to restore at least the basics of Ubuntu booting (UEFI partition, Grub, etc). Unfortunately, getting an error when trying to boot into Windows.  Given that Windows is not something I use regularly, I have time to figure that out.  I tried boot-repair, but that did not resolve it.  If anyone has any other pointers, I would appreciate them.   I get a bright blue Windows (11) screen and it is complaining about not being able to find winload.exe.  I will do a bit more Googling as well.

Thanks for the pointers thus far!

---

### Post by #&amp;thj^% on 2022-04-11
If worse comes to worse, try their rescue cd (windows) [https://www.groovypost.com/howto/create-a-windows-11-usb-recovery-drive/](https://www.groovypost.com/howto/create-a-windows-11-usb-recovery-drive/)
in a nutshell 
Step 1: You need to prepare an empty USB having a minimum of 8GB space. The more space your USB contains, the better. Go to Microsoft&#8217;s official website to download Windows 11 ISO.

Step 2: Click on "Download Tool Now" and launch it on your computer. Accept the terms and conditions. 

restore Windows 11 from the recovery USB

When you are done creating the recovery disk, follow the steps given below to recover Windows 11 using the recovery device. 

Step 1: Start your computer and connect your recovery disk to it.

Step 2: Select "Troubleshoot" and select the recovery option.

---

### Post by oldfred on 2022-04-11
Windows has a Microsoft reserved partition unformatted just in front of first NTFS. Since not formatted, it is not found by testdisk.
Often recovery includes that space and in effect corrupts the NTFS Windows partition.
Not sure how to then repair the Windows install.
Potentially you could just allocate the 128MB partition.

My older Dell showed this in sectors.  But unless you have some backup of partition table, it will be difficult to know your exact configuration.
Restore partitions you know, it looks like first NTFS partition was shrunk to make room for the Linux partition. And backup that configuration.

```
GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1           2,048     1,026,047     1,024,000 EFI System partition
/dev/sda2       1,026,048     1,107,967        81,920 -
/dev/sda3       1,107,968     1,370,111       262,144 Microsoft Reserved Partition (Windows)
/dev/sda4       1,370,112     2,906,111     1,536,000 Windows Recovery Environment (Windows)

```

Microsoft suggested partitions including reserved partition for gpt & UEFI:
[https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions](https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions)
Order on drive is important: msftres
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

---

### Post by csete on 2022-04-11
Thanks again for all of the help.  At this point, I have a working Ubuntu system, so I may just wait until I have a bit more time to repair my Windows installation.  At this point, I'm thinking I may be better off to do a factory recovery and then restore Ubuntu.  Unfortunately, Windows 11 troubleshooting didn't appear to work, so this may end up being my easiest option.

---

### Post by dragonfly41 on 2022-04-11
Possibly rEFInd installation might get you out of a hole. It installs into the EFI directory (I have it dual booting up Windows and Ubuntu) and rEFInd has its own identity.

---

### Post by csete on 2022-04-11
> **dragonfly41 said:**
> Possibly rEFInd installation might get you out of a hole. It installs into the EFI directory (I have it dual booting up Windows and Ubuntu) and rEFInd has its own identity.

So, in theory, this would replace both Windows Boot loader and GRUB?

---

### Post by oldfred on 2022-04-11
Grub is both a boot manager (menu) & a boot loader.
REFInd is a boot manager, it does not actually boot other systems, but has some additional capabilities over the grub menu.
I like rEFInd for emergeny boot as it fits on an old too small for anything else flash drive that I had laying around.

Alternative efi boot manager for UEFI limited systems:
[http://www.rodsbooks.com/refind/](http://www.rodsbooks.com/refind/) &
[https://askubuntu.com/questions/908677/want-to-view-contents-of-boot-efi-in-xubuntu-dont-have-permissions](https://askubuntu.com/questions/908677/want-to-view-contents-of-boot-efi-in-xubuntu-dont-have-permissions)
Setting up a multi-boot of 5 Linux distributionsm boot with rEFInd
[https://medium.com/@manujarvinen/setting-up-a-multi-boot-of-5-linux-distributions-ca1fcf8d502](https://medium.com/@manujarvinen/setting-up-a-multi-boot-of-5-linux-distributions-ca1fcf8d502)

If you really want to try to recover Window you may need to view the details at the beginning of the partition.
It should have a partition boot sector, not blank data like the system recovery partition would be.
You can use dd or hexdump to view data on NTFS partition. I expect first 256 or so sectors will be blank.
Actual Windows partition should start with certain codes.
[URL="http://ntfs.com/ntfs-partition-boot-sector.htm"]http://ntfs.com/ntfs-partition-boot-sector.htm
[http://www.c-jump.com/bcc/t256t/Week04NtfsReview/W01_0140_ntfs_boot_sector_byte.htm](http://www.c-jump.com/bcc/t256t/Week04NtfsReview/W01_0140_ntfs_boot_sector_byte.htm)
[/URL]

---

### Post by csete on 2022-04-11
> **oldfred said:**
> If you really want to try to recover Window you may need to view the details at the beginning of the partition.

Thinking about this some more.... if I don't care about the contents of my Windows installation, can I just reinstall Windows and fix up dualboot (if necessary)?  In the end, I only keep my Windows installation around for very rare cases and there is nothing in that installation I really care about.  If reinstall is OK are there any things I should be aware of before jumping in?

Thanks again,
Craig

---

### Post by oldfred on 2022-04-11
I have not used virtual installs, but may soon.
But many post that better to install Windows in Virtual Box, if not used for gaming where you need direct access to system for speed. It is only slightly slower in VB.

You do need Windows & Ubuntu in same boot mode, or both UEFI or both BIOS.
And Windows only installs in UEFI boot mode to gpt partitioned drives.
How you boot install media, UEFI or BIOS is then how it installs.

---

### Post by csete on 2022-04-12
I was able to just reinstall Windows and repair dual-boot/Grub without issues.  Thanks to everyone for their help along the way.

---

