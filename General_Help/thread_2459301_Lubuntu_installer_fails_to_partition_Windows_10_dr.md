---
title: "Lubuntu installer fails to partition Windows 10 drive"
date: 2021-03-15
forum: General Help
---

### Post by Brent_Santin on 2021-03-15
I'm trying to install Lubuntu 20.04LTS onto a computer that already has Windows 10 installed on it.  I'd like it to be a dual boot system.  I've done this many times on old Windows XP machines, but it's failing on this Win10 machine. 

It fails is when it attempts to shrink the Windows 10 partition and create a new partition to for Lubuntu. The drive is a 500GB Seagate drive. Currently Windows 10 takes up 33GB of the drive. I'd like to reduce this partition to about 100GB (as I barely use Windows) and have the rest of the drive available for Lubuntu.

From the Lubuntu installer, I choose to "Install alongside..."
Then I choose sda3 and use the GUI to graphically adjust the NTFS Win10 partition to be about 100GB, leaving the rest for Lubuntu. SDA1 and SDA2 are very small partitions on the drive. I'm assuming recovery partitions or something for Win10.

Once I've set the parameters, it says at the bottom of the install screen:
[INDENT][B][FONT=courier new]"/dev/sda3 will be shrunk to <size I've set>MiB and a new <size I've set>MiB partition will be created for Lubuntu"
"The EFI sytem partition at /dev/sda1 will be used for starting Lubuntu"[/FONT][/B]
[/INDENT]

I then click the NEXT button at the bottom of the screen.

When the installer tries to resize the Windows partition, and error window pops up saying:
[INDENT][B][FONT=courier new]The installer failed to resize partition /dev/sda3 on disk 'ST5900DM002-1BD142'.
===================================================
Shrink partition '/dev/sda3' from 465.16GiB to 117.73GiB
===================================================
===================================================
Job: Check file system on partition 'dev/sda3'
===================================================
===================================================
Command: ntfsresize -no-progress-bar --info --force --verbose /dev/sda3
===================================================
Checking partition 'dev/sda3/ before resize/move failed.[/FONT][/B]
[/INDENT]

I tried entering the command recommended above (after the word Command: ntfsresize...etc.) in a shell but get this error message:

[FONT=courier new][B]Error opening '/dev/sda3': Permission denied
ERROR(13): Opening '/dev/sda3' as NTFS failed: Permission denied[/B][/FONT]

Any help anyone can offer help it would be appreciated.
A little reading online advised me to shut of "fast startup" in Windows 10, which I did. It did not help.

Thanks

---

### Post by grahammechanical on 2021-03-15
It is best to use Windows tools to manage Windows partitions. Use a Windows tool to defragment the drive and a Windows tool to shrink the Windows partition. May be defragment again. Test Windows will boot at each stage.

Then Ubuntu Gparted to create partitions in the unallocated space.

Regards

---

### Post by HermanAB on 2021-03-16
+10: "It is best to use Windows tools to manage Windows partitions."

---

### Post by guiverc on 2021-03-16
I have no experience with windows 10, and I'll assume any *fastboot/hibernate* has been de-activated (*it would be unwise if not impossible to shrink a partition unless that was done*)

I'd opt to shrink before I attempted install (ie. *create the blank space in which you install Lubuntu then start the installer, or better create a partition in that blank sp*ace and just select that within `calamares`), with the  "*Manual Partitioning*" options by preference  anyway.

  I test *install alongside* with Lubuntu at least weekly, but it's with *native* (to GNU/Linux) file-systems.

I too think it's wise to let the OS where the *file-system* is native do any re-sizes (ie. NTFS is a microsoft windows file-system; so I'd *tend* to trust their tools for the job).

 I know I've used `gparted` to do it *many *times (*supporting XP computers years ago*) but I was selective in what tool I'd use and it was often an appropriate tool. Sorry I don't know if there are any differences with windows 10.

If you wish to do it Lubuntu yourself, I'd restart the *live* ISO (ie. *reboot*) and use *KDE Partition Manager* to setup the partitions as you want (ie. *let it do the re-size*), then when you've got what you want, start `calamares` and select the prepared partitions and let the install happen.

FYI:  `calamares` is the name of the installer used by Lubuntu.

---

### Post by Brent_Santin on 2021-03-16
Can anyone recommend a simple and free Windows disk partitioning utility?  I am totally out of the scene on Windows 10

Thanks

---

### Post by yancek on 2021-03-16
> Can anyone recommend a simple and free Windows disk partitioning utility?  I am totally out of the scene on Windows 10


The Disk Management tool is part of any windows installation and is available from the windows menu.  It should be under Computer Management.  Several other methods explained at the link below.

 [https://www.isunshare.com/windows-10/7-ways-to-open-disk-management-in-windows-10.html](https://www.isunshare.com/windows-10/7-ways-to-open-disk-management-in-windows-10.html)

You might run Disk Defragmenter first but definitely test reboot windows after shrinking any partition.  Might also be a good ides to run chkdsk.

---

### Post by ActionParsnip on 2021-03-16
Shrink NTFS in Windows. It's a Windows file system and only Microsoft know how it works fully.

---

### Post by dragonfly41 on 2021-03-16
My suggestion would be to leave the internal drive untouched (no attempt to install Ubuntu on a shrunken partitions) and go out to purchase an external USB SSD with its own power supply. In fact I have two SSD's in a dual bay docking system (USB 3.0 port is better) attached to Dell tower. Just to clarify I have Ubuntu 20.04 on the external SSD's. All UEFI.

---

### Post by Autodave on 2021-03-16
Back up EVERYTHING before doing any of the above mentioned!!!!!

---

### Post by Brent_Santin on 2021-03-16
Okay, I've run chkdsk and defragmented the Win10 drive.  I've also found the Win10 utility that will let me shrink the partition.

The reason I don't want to purchase a dedicated drive for Lubuntu is that I really almost never use Windows. I only keep it around for those few Windows applications I need to run that won't run under Linux/WINE. In fact, if this dual booting thing doesn't work I am a little tempted to just delete Win10 and make the computer 100% Lubuntu. For that past 7 years or so I've run a Lubuntu/WinXP machine this way. The new (used) computer has Win10 instead.

Will back up the drive first, then will attempt the installation afterward.

---

### Post by Brent_Santin on 2021-03-19
chkdsk and de-fragmenting fixed the problem. I was able to do a dual Lubuntu/Windows installation.  Thanks.

---

