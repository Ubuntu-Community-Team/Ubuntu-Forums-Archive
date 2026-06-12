---
title: "GParted sees NO DATA after boot-repair (PC still works)"
date: 2014-04-08
forum: General Help
---

### Post by Ace..... on 2014-04-08
**[http://paste.ubuntu.com/7221436](http://paste.ubuntu.com/7221436)**

Check out this number of 512byte sectors: 3,018,063,139  b2 QNX Neutrino Power-Safe (wow!!!!)
(I had previously never even heard of a QNX o/s........ it looks like a case of 'mis-identification'.)
Gparted sees 149 GiB with partitions and files system, both unallocated.
The PC boots to Win XP ..... we've lost the GRUB and access to Xubuntu.

**Here's what happened**:
During initial setup, a win partition was created for AVG, with the intention of separating the mammoth daily updates.
This was a fail..... AVG simply bypassed this to load on C drive.
So there was some spare capacity right next to the winxp partition.

A partition had been created to install programs, but the user forgot when installing a very big gaming package - crossfire.
(We'd tried to get this to work on xubuntu, but it was always laggy)
With updates, and all, C: ran out of space (I noticed when trying to shut the damned thing down this Monday).

I figured.... shrink the useless AVG partition, and move it to the right, to create space to the left, allowing me to expand the win xp partition.
I guessed that messing with the partitions might rupture GRUB...... but we did have 'BOOT-REPAIR' :)

**Using Xubuntu & GParted:**
The first operation was to create free space to the left of the AVG partition.
I clicked through all the warnings (I had boot-repair ready).

The operation failed.
I re-booted to witness the consequences, and had no 'bead of sweat' when I got 'GRUB ERROR'.
I immediately booted to boot-repair, accepting the std config.

**Boot-Repair Ditched GRUB and Xubuntu:**
On re-boot, instead of a multi-boot menu.... the PC booted directly to win xp.

I figured that I would be able to fix this using the advanced setting, however, when I examined the disk (using boot-repair gparted) the disk was shown as effectively empty.
I then ran the xubuntu install disk (choosing something else) to load GParted....... same result.
I then downloaded GParted Live....... same result.

Bizarrely enough.... the WinXP embedded disk manager sees all partitions, though, as normal, it doesn't understand the xubuntu/swap partitions (even if it sees them)

**So For the Moment I'm stuck**:
I can't do anything with GParted cos it thinks the disk is blank.
I can't risk, (without support) trying boot-repair's advanced option, in order to try to re-build the GRUB and re-gain xubuntu (and and then subsequently enlarge C: to absorb the (now formatted) ex-AVG partitition).

Thank goodness we have the 'boot-repair output text'.

:)

---

### Post by oldfred on 2014-04-08
Boot-Repair & gparted cannot see any Linux partitions. As long as you have this you have major issues.
Do you know partition layout before?

> 
 Extended partition linking to another extended partition.

 /dev/sda9 ends after the last sector of /dev/sda
the logical partition /dev/sda9 is not contained in the extended partition /dev/sda3
/dev/sda9 overlaps with /dev/sda10
/dev/sda10 ends after the last sector of /dev/sda
the logical partition /dev/sda10 is not contained in the extended partition /dev/sda3


I am not sure if fixparts or testdisk is the better alternative or you may have to try both. I might try both without writing from each first to see what they say.

You cannot have overlapping partitions and all logical partitions must be inside the extended partition.
Also now partition table is corrupted so it does not show a Linux format for any partitions, so no data inside them can be read.
Also many of your NTFS partitions all start internally from sector 63. These must be copies and you never ran chkdsk to repair them.

       To convert a partition from primary to logical, at least one free (unallocated) sector must exist between the partition and the one that precedes it.
Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1667614&p=10367957#post10367957](http://ubuntuforums.org/showthread.php?t=1667614&p=10367957#post10367957)
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
First backup partition table, use your drive for sdX or sda, sdb etc.
sudo sfdisk -d /dev/sdX > parts.txt

 [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
      
 Testdisk Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

 [http://www.rodsbooks.com/missing-parts/index.html](http://www.rodsbooks.com/missing-parts/index.html)

---

### Post by Ace..... on 2014-04-09
[B]Here is the partition layout as displayed by WinXP disk manager (see attached image).
[/B]
From left to right:

```

Dell ............................. 63Mb
WinXP............................. 29Gb
Formatted drive (was AVG drive)... 9.7Gb
Programs ......................... 30Gb
Data.............................. 30Gb
Win Swap.......................... 2.9Gb
Internet temp .................... 10Gb
```
The above look correct.
'Internet temp' seems a bit large, but the order will be correct.

**The last 4 (as shown) are not to be trusted**, as the entire disk holds only around 150Gb, so sizes are way off.
Three of these were linux file system: 

```

free space ........... 851Gb (!)
Xubuntu ............... 3.0Gb
Data ................. 1439Gb (!)
Swap .................. 6.3Gb
```
**Boot-repair anaysis:** [http://paste.ubuntu.com/7221436/](http://paste.ubuntu.com/7221436/)

I'll proceed to attempt to back up the partition table.

---

### Post by Ace..... on 2014-04-09
sudo sfdisk -d /dev/sdX > parts.txt
produces:

```
# partition table of /dev/sda
unit: sectors


/dev/sda1 : start=       63, size=   128457, Id=de
/dev/sda2 : start=   128520, size= 61432560, Id= 7, bootable
/dev/sda3 : start= 61561141, size=244635339, Id= f
/dev/sda4 : start=306198900, size=  6297480, Id=db
/dev/sda5 : start= 82044018, size= 63472752, Id= 7
/dev/sda6 : start=145516833, size= 63472752, Id= 7
/dev/sda7 : start=208989648, size=  6136767, Id= 7
/dev/sda8 : start=215126478, size= 21494907, Id= 7
/dev/sda9 : start=2022437005, size=3018063139, Id=b2
/dev/sda10: start=4520496369, size= 13204961, Id=7c

```

---

### Post by Ace..... on 2014-04-09
**In the end, I took a different route.**
I studied Rod smith's documents, but I found that he himself was not advising using the fixparts on the primary boot drive 0.
In addition there were complications running linux from a cd.

What I had gleaned from my researches, was that windows disk tools can see the partitions, whereas linux tools cannot.
As a consequence I downloaded **EaseUS Partition Master**.

attached are the pre & post modification screenshots.

My strategy was to make changes to the partitions, in the hope that Partition Master would re-write the partition table correctly.

[B]I have just loaded GParted Live:
[/B]The good news is that GParted can now see the hard drive, the same as Partition Master.

This looks like a big win :)

I shall try uploading a screen shot, and also running yannbuntu's analysis tool.

---

### Post by Ace..... on 2014-04-09
**Here is the Boot-Repair analysis:**

[http://paste.ubuntu.com/7226206/](http://paste.ubuntu.com/7226206/)

I failed to figure a way of uploading the screenshot taken in GParted Live.
They provide a screenshot prog, plus a very neat and fast browser 'net surf'.
However they didn't provide a simple file manager.
I'm sure there must be a way but......

However, the analysis is more important.

I note that sda 5-8 drives are shown as starting at 63 ie. where the 1st Dell partition is located.
However.... just below in the next section - the start points of each drive are listed perfectly???

Does this look okay?

There is still the cylinder boundary issue that has always been present.... I don't know whether anything can be done about that, or even whether it has been the root cause of the problems.

One thing is clear.... partition master has proved to be a very useful utility. 

:)

---

### Post by oldfred on 2014-04-09
Cylinder boundry is an old error message and should not be an issue. Hard drives have not used cylinders since they went over 8GB. Often better to have drive set for AHCI, but that does not work with XP. When I had to change to AHCI for trim to work on my then new SSD, I had to finally stop using XP as it did not have those drivers. It would have been a new install to incorporate AHCI. Windows 7 has those drivers but have to be turned on before change in BIOS.

It looks like all EaseUS did was delete the LInux partitions (or partition entries) and resize your NTFS to then be the entire drive. You may have been able to just delete them anyway. But glad that worked.

Partitions have partition table entries which are where they are on drive. But NTFS partition have internal data in PBR or partition boot sector that also has the same start & size info as partition table. If  that info does not match Windows will not boot. But if a data partition it may not matter. Normally a chkdsk resets that data.

---

### Post by Ace..... on 2014-04-09
> **oldfred said:**
> Cylinder boundry is an old error message and should not be an issue.

Thanks for clearing up that area of doubt.

> **oldfred said:**
> 
It looks like all EaseUS did was delete the LInux partitions (or partition entries) and resize your NTFS to then be the entire drive. You may have been able to just delete them anyway. 

Yes, I specifically directed Partition Master to reconfigure each partition, and area considered as free space, changing the start, and end locations - to force a re-write.
It then scanned each partition for partition errors, surface errors, and then booked a boot-time chkdsk (which found no errors).

Success!

:)

---

