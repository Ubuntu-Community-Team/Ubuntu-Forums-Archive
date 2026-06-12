---
title: "Windows partitions are not seen in gparted."
date: 2020-05-10
forum: General Help
---

### Post by praveenthivari on 2020-05-10
I have a hp laptop with 120GB SSD and 1TB hard disk. I have a windows installed on SSD. The hard disk has been partitioned into 3 partitions. I have unallocated some space from one of the partitions in hard disk. I am planning to install ubuntu on this. But when I boot into the live ubuntu usb, during installation, the unallocated space and the partitions of hard disk are not seen. It just appears as a single large space. 

I think I had partitioned my hard disks as GPT partitions table. If that helps.

How to make ubuntu detect the partitions on hard disks.?

My partition table results are follows:

[ATTACH=CONFIG]285812[/ATTACH][ATTACH=CONFIG]285813[/ATTACH]

---

### Post by CelticWarrior on 2020-05-10
Please check the SATA mode or equivalent in UEFI. Likely you'll find it set to RAID or Intel RST, both modes are not compatible, it needs change to AHCI. AHCI support needs to be installed in Windows first or it'll not boot after that change.

[LEFT]

[/LEFT]

---

### Post by VMC on 2020-05-10
> **CelticWarrior said:**
> Please check the SATA mode or equivalent in UEFI. Likely you'll find it set to RAID or Intel RST, both modes are not compatible, it needs change to AHCI. AHCI support needs to be installed in Windows first or it'll not boot after that change.That's most likely the case. Just  yesterday after several Windows installs and not being able to install linux, RST popped up. There is a hack to fix without re-installing, but in the end it was way more work, so I re-installed Windows with AHCI ctive. All's well now.

---

### Post by praveenthivari on 2020-05-10
Thank you for reply.

As I searched through the BIOS settings, I couldn't find RAID or Intel RST options anywhere. 

I did a bit of googling, it happens that the InsydeH20 rev5.0 bios on my laptop has been locked by HP and doesn't show advanced options. To my knowledge, at present there are is no safer way (key combo or flashing a different bios version) to unlock the advanced settings.

I am thinking of wiping both (SSD and hard disk), deleting all partitions and create a new partition table which ubuntu understands. However, that would be too much work for me to as I have to backup all my data. Don't want to have such a drastic step at this stage. Will it help? Is it a solution.

My windows partitions:

[ATTACH=CONFIG]285814[/ATTACH]

---

### Post by oldfred on 2020-05-10
You show LDM.
How did you get that?

LDM is dynamic partitions on a gpt partitioned drive. Somewhat like LVM volumes are in Linux.
It is proprietary to Microsoft. Linux now has a driver so you can see LVM, but it really does not work with Linux.

Microsoft's official policy is a full backup, erase dynamic partitions and create new basic partitions. There is no undo.
Dynamic volume is a Microsoft proprietary format developed together with Veritas/Symantec for logical volumes.
You may be use a third-party tool, such as Partition Wizard MiniTool or EASEUS to convert a convert a dynamic disk to a basic disk without having to delete or format them.
I've never used any of these and so I can't be sure they will work.Be sure to have good backups as any major partition change has risks.
Shown as SFS in fdisk, Dynamic also on gpt as LDM
[http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx](http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx) & 
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)
From Linux view LDM
[http://mika.soup.io/post/304505086/ldmtool-accessing-Microsoft-Windows-dynamic-disks-from](http://mika.soup.io/post/304505086/ldmtool-accessing-Microsoft-Windows-dynamic-disks-from)
[https://askubuntu.com/questions/482768/changing-windows-dynamic-disk-partition-to-basic-partition-and-not-the-full-driv](https://askubuntu.com/questions/482768/changing-windows-dynamic-disk-partition-to-basic-partition-and-not-the-full-driv)
[http://manpages.ubuntu.com/manpages/trusty/man1/ldmtool.1.html](http://manpages.ubuntu.com/manpages/trusty/man1/ldmtool.1.html)

---

### Post by praveenthivari on 2020-05-10
Thank you for replying.

I think when I installed the windows on new SSD, I had wiped data on hard disk also. I had set SSD as the windows installation location. It might have created LDM partitions at that time. All the while I thought it to be a linux recognised partitions. (My bad)


I had not installed linux on this laptop till now, so didn't pick this up early. Now, during this ongoing lockdown situation I had planned to install ubuntu on a partition. But, I think this thing will have to wait for some time.

Anyway, EaseUS partition manager doesn't have the option of converting the partitions back to basic partitions. :-| 
So now I'll have to find a safe way to get around the problem/ or make a full backup of my system:D

What is your opinion on deleting all the partitions on both drives and create new partitions again? Will this solve the problem? What precautions/ modifications to partitions  will I have to make to create linux recognisable partitions with my dual disks setup?

---

### Post by oldfred on 2020-05-10
As long as Windows is not hibernated, fast start up is off, or Windows does not need chkdsk, then the Linux NTFS driver can correctly see the Windows partitions.
Windows cannot see Linux partitions.

Some old threads. Do not see dynamic partitions much with gpt. It more was what Windows used to get around the 4 primary partition limit in MBR partitioning. Windows did not normally use primary, extended & logical partitions. But with gpt there is in effect no real limit on number of partitions. Not sure what other advantage they claim, if any. Not sure if gpt, if then testdisk will still work or not.

Be sure to have good backups.

Posts by oldfred & srs5694
[http://ubuntuforums.org/showthread.php?t=1705481](http://ubuntuforums.org/showthread.php?t=1705481)
SFS converting:
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)
Post 96 using sfdisk - must have only 4 partitions
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk-10.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk-10.html)
Also used testdisk if less than 4 dynamic partitions
[http://ubuntuforums.org/showthread.php?t=1675420](http://ubuntuforums.org/showthread.php?t=1675420)
Used testdisk but see caveats in Post#7:
[http://ubuntuforums.org/showthread.php?t=1669418](http://ubuntuforums.org/showthread.php?t=1669418)

---

