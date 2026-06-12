---
title: "Dual boot Windows 7 and Ubuntu 13.10"
date: 2014-02-09
forum: General Help
---

### Post by ThePie on 2014-02-09
I've need some help with setting up a dual boot for Ubuntu on my HP Pavilion dv6 laptop.

I have Windows 7 installed on my hard drive which is basic not dynamic.

I have 3 partitions and a extended partition.

System is around 200MB
C: (Where Windows 7 is) is around 400GB
Temp is around 1GB
pA, pB, pC, pD are around 50GB
(pC is the Ubuntu partition and pD is the file transfer partition)
HP_TOOLS is around 100MB

Normal Text are primary partitions, Italicized is the extended partition.
[TABLE="class: grid, width: 200"]
[TR]
[TD]SYSTEM
[/TD]
[/TR]
[TR]
[TD]C:
[/TD]
[/TR]
[TR]
[TD]*Temp*
[/TD]
[/TR]
[TR]
[TD]*pA*
[/TD]
[/TR]
[TR]
[TD]*pB*
[/TD]
[/TR]
[TR]
[TD]*pC*
[/TD]
[/TR]
[TR]
[TD]*pD*
[/TD]
[/TR]
[TR]
[TD]&#65279;&#65279;HP_TOOLS
[/TD]
[/TR]
[/TABLE]
(And that's the order in which it shows up in Device Manager in Windows 7 with 2 primary partitions then a extended partition and then the last primary partition)

I already have them set up and the right size and just need to install Ubuntu 13.10. The problem that I'm having is that nether the Ubuntu installer or the GParted program on my Parted Magic CD can see any of my partitions.

[IMG]http://s6.postimg.org/ezz2s6u41/Screenshot_from_2014_02_10_00_04_19.png[/IMG]

So far I've went into Parted Magic, ran "gdisk /dev/sda" in terminal. Choose expert menu (x) and then (z) to destroy the GPT data while not changing the MBR data.

I booted up Ubuntu 13.10 from a 8GB USB drive and ran these two commands and received the following response.
```
[B][COLOR=#000000][FONT=Arial]ubuntu@ubuntu:~$ sudo parted -l
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]Error: Can't have overlapping partitions.                                 [/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Model: SanDisk Cruzer (scsi)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Disk /dev/sdb: 8000MB[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Sector size (logical/physical): 512B/512B[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Partition Table: msdos[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Number  Start   End     Size    Type     File system  Flags[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial] 1      1049kB  8000MB  7999MB  primary  fat32        boot, lba[/FONT][/COLOR]
[/B]
```

```
[B][COLOR=#000000][FONT=Arial]ubuntu@ubuntu:~$ sudo fdisk -l[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Disk /dev/sda: 750.2 GB, 750156374016 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Units = sectors of 1 * 512 = 512 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Sector size (logical/physical): 512 bytes / 4096 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I/O size (minimum/optimal): 4096 bytes / 4096 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Disk identifier: 0x5e633406[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]   Device Boot      Start         End      Blocks   Id  System[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]/dev/sda1   *        2048      409599      203776    7  HPFS/NTFS/exFAT[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]/dev/sda2          409600  1042692095   521141248    7  HPFS/NTFS/exFAT[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]/dev/sda3      1042692033  1464936447   211122207+   f  W95 Ext'd (LBA)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Partition 3 does not start on physical sector boundary.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]/dev/sda4      1464936448  1465147119      105336    c  W95 FAT32 (LBA)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]/dev/sda5      1042692096  1044684799      996352    6  FAT16[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]/dev/sda6      1044686848  1149749247    52531200    7  HPFS/NTFS/exFAT[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]/dev/sda7      1149751296  1254809599    52529152    7  HPFS/NTFS/exFAT[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]/dev/sda8      1254811648  1359874047    52531200    7  HPFS/NTFS/exFAT[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]/dev/sda9      1359876096  1464936447    52530176    7  HPFS/NTFS/exFAT[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Disk /dev/sdb: 8000 MB, 8000110592 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]255 heads, 63 sectors/track, 972 cylinders, total 15625216 sectors[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Units = sectors of 1 * 512 = 512 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Sector size (logical/physical): 512 bytes / 512 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I/O size (minimum/optimal): 512 bytes / 512 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Disk identifier: 0x00000000[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]   Device Boot      Start         End      Blocks   Id  System[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]/dev/sdb1   *        2048    15624191     7811072    c  W95 FAT32 (LBA)[/FONT][/COLOR]

[/B]
```

---

### Post by oldfred on 2014-02-09
Your sda2 ends after the start of sda3, or sda3 starts inside sda2, which cannot overlap.
You need to fix that first.

 /dev/sda2          409600  [COLOR=#ff0000][/COLOR]104269[COLOR=#ff0000]2095 [/COLOR]  521141248    7  HPFS/NTFS/exFAT
/dev/sda3      104269[COLOR=#ff0000]2033[/COLOR]  1464936447   211122207+   f  W95 Ext'd (LBA)

The first partition inside the ext'd, sda5 does start correctly as ...2096

---

### Post by ThePie on 2014-02-09
> **oldfred said:**
> Your sda2 ends after the start of sda3, or sda3 starts inside sda2, which cannot overlap.
 You need to fix that first.

 /dev/sda2          409600  104269[COLOR=#ff0000]2095 [/COLOR]  521141248    7  HPFS/NTFS/exFAT
 /dev/sda3      104269[COLOR=#ff0000]2033[/COLOR]  1464936447   211122207+   f  W95 Ext'd (LBA)

 The first partition inside the ext'd, sda5 does start correctly as ...2096


I've never had this issue before. How would I go about fixing the overlapping? Is it something that needs to be done from Windows 7, Ubuntu Live CD boot, or Parted Magic?

---

### Post by oldfred on 2014-02-09
Most Linux tools do not work when they see an error. Not sure if Windows tools will or not. 

 Fix overlaping partition error srs5694 Post #34
[http://ubuntuforums.org/showthread.php?t=1667614](http://ubuntuforums.org/showthread.php?t=1667614)

      
 First backup partition table, use your drive for sdX or sda, sdb etc.
sudo sfdisk -d /dev/sdX > parts.txt

I also have seen posts from very knowledgeable users on using sfdisk to manually change the partition table. You export file as above backup and manually edit data as it is just text and then restore a corrected version.
      
 Using sfdisk to fix partition table problems - not without risk
[http://ubuntuforums.org/showthread.php?t=1192598](http://ubuntuforums.org/showthread.php?t=1192598)
Equivalent sfdisk values would keep the start point and convert the end point via the formula size = end - start + 1. 
Also fdisk -lu shows start & blocks, blocks * 2 also equals size in sectors

   Caljohnsmith using sfdisk to edit partition table from text file
[http://ubuntuforums.org/showthread.php?t=1036600](http://ubuntuforums.org/showthread.php?t=1036600)
[http://ubuntuforums.org/showthread.php?t=1038943](http://ubuntuforums.org/showthread.php?t=1038943)
caljohnsmith and meierfra use sfdisk links:
Exported partition table & reimported to fix with sfdisk.
[http://ubuntuforums.org/showthread.php?t=1591704](http://ubuntuforums.org/showthread.php?t=1591704)

---

### Post by ThePie on 2014-02-09
So I first went and looked at this link [[COLOR=#dd4814]http://ubuntuforums.org/showthread.php?t=1192598[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1192598")

Made a backup of my partition table using the "sudo sfdisk -d /dev/sda > parts.txt" command

Then I went to [http://www.rodsbooks.com/missing-parts/](http://www.rodsbooks.com/missing-parts/) and its download page [http://sourceforge.net/projects/gptfdisk/files/gptfdisk/0.8.8/fixparts-binaries/](http://sourceforge.net/projects/gptfdisk/files/gptfdisk/0.8.8/fixparts-binaries/) and downloaded [fixparts_0.8.8-1_amd64.deb]("http://sourceforge.net/projects/gptfdisk/files/gptfdisk/0.8.8/fixparts-binaries/fixparts_0.8.8-1_amd64.deb/download") and installed that onto my live boot of Ubuntu.

Then I ran "sudo fixparts /dev/sda" to launch it. Typed "p" to print out my partition table. (I read/noticed that just by running fixparts it auto/silently corrects some of the partition mistakes.) When viewing the partition table I didn't see any overlapping partitions (numbers) so I went ahead and ran the "w" command which writes the table to the disk.

I then went back to terminal and ran the two check commands that I started this post with.
```
[B][COLOR=#000000][FONT=Arial]ubuntu@ubuntu:~$ sudo parted -l[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Model: ATA Hitachi HTS54757 (scsi)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Disk /dev/sda: 750GB[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Sector size (logical/physical): 512B/4096B[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Partition Table: msdos[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Number  Start   End    Size    Type      File system  Flags[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial] 1      1049kB  210MB  209MB   primary   ntfs         boot[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial] 2      210MB   534GB  534GB   primary   ntfs[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial] 3      535GB   750GB  215GB   extended               lba[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial] 5      535GB   589GB  53.8GB  logical   ntfs[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial] 6      589GB   642GB  53.8GB  logical   ntfs[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial] 7      642GB   696GB  53.8GB  logical   ext4[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial] 8      696GB   750GB  53.8GB  logical   ntfs[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial] 4      750GB   750GB  108MB   primary   fat32        lba[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]Model: SanDisk Cruzer (scsi)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Disk /dev/sdb: 8000MB[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Sector size (logical/physical): 512B/512B[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Partition Table: msdos[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Number  Start   End     Size    Type     File system  Flags[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial] 1      1049kB  8000MB  7999MB  primary  fat32        boot, lba[/FONT][/COLOR]
[/B]

```
```
[B][COLOR=#000000][FONT=Arial]ubuntu@ubuntu:~$ sudo fdisk -l[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Disk /dev/sda: 750.2 GB, 750156374016 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Units = sectors of 1 * 512 = 512 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Sector size (logical/physical): 512 bytes / 4096 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I/O size (minimum/optimal): 4096 bytes / 4096 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Disk identifier: 0x5e633406[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]   Device Boot      Start         End      Blocks   Id  System[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]/dev/sda1   *        2048      409599      203776    7  HPFS/NTFS/exFAT[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]/dev/sda2          409600  1042692095   521141248    7  HPFS/NTFS/exFAT[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]/dev/sda3      1044686847  1464936447   210124800+   f  W95 Ext'd (LBA)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Partition 3 does not start on physical sector boundary.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]/dev/sda4      1464936448  1465147119      105336    c  W95 FAT32 (LBA)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]/dev/sda5      1044686848  1149749247    52531200    7  HPFS/NTFS/exFAT[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]/dev/sda6      1149751296  1254809599    52529152    7  HPFS/NTFS/exFAT[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]/dev/sda7      1254811648  1359874047    52531200    7  HPFS/NTFS/exFAT[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]/dev/sda8      1359876096  1464936447    52530176    7  HPFS/NTFS/exFAT[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Disk /dev/sdb: 8000 MB, 8000110592 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]255 heads, 63 sectors/track, 972 cylinders, total 15625216 sectors[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Units = sectors of 1 * 512 = 512 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Sector size (logical/physical): 512 bytes / 512 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I/O size (minimum/optimal): 512 bytes / 512 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Disk identifier: 0x00000000[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]   Device Boot      Start         End      Blocks   Id  System[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]/dev/sdb1   *        2048    15624191     7811072    c  W95 FAT32 (LBA)[/FONT][/COLOR]
[/B]

```

I went to the install Ubuntu package/app/whatever its called, and clicked threw till I got to the step where you can "choose something else" and instead of getting unallocated partition table I saw my partitions!
[IMG]http://s6.postimg.org/i83k58gdt/Screenshot_from_2014_02_10_02_59_32.png[/IMG]

Also here is what my before and after partition table txt files looked like
```
parts.txt

# partition table of /dev/sda
unit: sectors/dev/sda1 : start=     2048, size=   407552, Id= 7, bootable
/dev/sda2 : start=   409600, size=1042282496, Id= 7
/dev/sda3 : start=1042692033, size=422244415, Id= f
/dev/sda4 : start=1464936448, size=   210672, Id= c
/dev/sda5 : start=1042692096, size=  1992704, Id= 6
/dev/sda6 : start=1044686848, size=105062400, Id= 7
/dev/sda7 : start=1149751296, size=105058304, Id= 7
/dev/sda8 : start=1254811648, size=105062400, Id= 7
/dev/sda9 : start=1359876096, size=105060352, Id= 7


```
```
parts2.txt

# partition table of /dev/sda
unit: sectors/dev/sda1 : start=     2048, size=   407552, Id= 7, bootable
/dev/sda2 : start=   409600, size=1042282496, Id= 7
/dev/sda3 : start=1044686847, size=420249601, Id= f
/dev/sda4 : start=1464936448, size=   210672, Id= c
/dev/sda5 : start=1044686848, size=105062400, Id= 7
/dev/sda6 : start=1149751296, size=105058304, Id= 7
/dev/sda7 : start=1254811648, size=105062400, Id= 7
/dev/sda8 : start=1359876096, size=105060352, Id= 7


```

I booted back into Windows 7 and went to the device manager and noticed that my partition table changed. The Temp partition that used to be in the extended partition is now just unallocated space, not free space within the extended partition even though that it used to be within the extended partition which I thought was odd. 

[COLOR=#0000cd]Primary, [/COLOR][COLOR=#008000]Extended,[/COLOR] [COLOR=#808080]Unallocated, [/COLOR][COLOR=#00ff00]Free Space[/COLOR]
[TABLE="class: cms_table_grid, width: 200"]
[TR]
[TD][COLOR=#0000ff]SYSTEM[/COLOR]
[/TD]
[/TR]
[TR]
[TD][COLOR=#0000ff]C:[/COLOR]
[/TD]
[/TR]
[TR]
[TD][COLOR=#808080]Temp[/COLOR]
[/TD]
[/TR]
[TR]
[TD][COLOR=#008000]pA[/COLOR]
[/TD]
[/TR]
[TR]
[TD][COLOR=#008000]pB[/COLOR]
[/TD]
[/TR]
[TR]
[TD][COLOR=#008000]pC[/COLOR]
[/TD]
[/TR]
[TR]
[TD][COLOR=#008000]pD[/COLOR]
[/TD]
[/TR]
[TR]
[TD][COLOR=#0000ff]&#65279;&#65279;HP_TOOLS[/COLOR]
[/TD]
[/TR]
[/TABLE]

Although the only reason why I have this small 'Temp' partition is for using "Partition Manager" (a windows 7 partitioning tool) which made it possible to take space (megabytes) from the C: partition and move it to a temporary location to format it to FAT32 which put it into a logical partition where I was then able to extend the logical partitions pA, pB, pC, pD to the size that I wanted (50GB + 100MB --> 51300MB). P.S. - It bugged me that windows explorer was saying that the partitions pA, pB, pC, and pD where being displayed as 49.99GB instead of the 50.0GB that it should have been showing so by adding that extra 100MB I was able to get windows explorer to show that those 4 logical partitions are 50.0GB.

Anyway I will continue with the dual boot process another day for I am tired and sick of staring at a screen.  :)

---

### Post by oldfred on 2014-02-10
With new SSD & 4K drives, partition tools round to prevent drive issues. Best not to change that.
And you may be into binary vs.decimal as some tools show one and other show the other.

 First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of arrays and some types of new hard disks (those with 4096-byte physical sectors). See article by srs5694:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)
it's 8-sector (4096-byte) alignment
[http://ubuntuforums.org/showthread.php?t=1768635](http://ubuntuforums.org/showthread.php?t=1768635)
Alignment issues on 4K drives
[http://ubuntuforums.org/showthread.php?t=1635018](http://ubuntuforums.org/showthread.php?t=1635018)


 sudo parted -s /dev/sda unit GB print
sudo parted -s /dev/sda unit GiB print

      
 MB vs MiB
[http://en.wikipedia.org/wiki/Binary_prefix](http://en.wikipedia.org/wiki/Binary_prefix)
[http://www.osforge.com/news/001337.html](http://www.osforge.com/news/001337.html)

---

