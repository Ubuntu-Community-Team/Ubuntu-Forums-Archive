---
title: "GParted Error: Error informing the kernel about modifications to partition"
date: 2013-09-07
forum: General Help
---

### Post by ktz84 on 2013-09-07
I'm using Ubuntu 13.04.

On sdd4 I'm getting the following error when I load up GParted:

> Error informing the kernel about modifications to partition /dev/sdd4 -- Device or resource busy.  This means Linux won't know about any changes you made to /dev/sdd4 until you reboot -- so you shouldn't mount it or use it in any way before rebooting.

SDD4 is my extended partition container according to GParted:

[IMG]https://dl.dropboxusercontent.com/u/3136192/Partition%20Info.png[/IMG]

All my Partitions work and sdd5 autmounts without issue.

To go back a little. Yesterday I had changed the partitions on this disk using GParted as I converted the sdd3 partition from an ntfs file system to ext4 as I'm gradually move all my main data that I will never need in a dual boot as I will only be dual booting on the very rare occasion that I can't do something natively in Ubuntu or in a Windows 7 VM. I have yet to decide the partitioning of the unallocated space in the Extended partition.

After doing the repartitioning yesterday GParted started showing the whole disk as unallocated and had a big exclamation mark in it and throughout all this I could still access all my partitions and copy to and from them. I went looking for a fix so that the GParted would correctly show my partitions again. I used fixparts on that disk. I hadn't a clue what it was telling me but noted that it said that sometimes invisible changes take place during the initial running of it so seeing no errors or anything and having backed up my partition as advised I decided to write that to the disk and rebooted. GParted now shows the disk, as shown above, however I keep getting this message so I'm guessing I may have caused a few more problems or I haven't completely sorted the original issue.

Not really sure where to go from here. Can anyone advise please?

---

### Post by ktz84 on 2013-09-07
I was just in disks there as I was looking to mount something else and I thought I'd take a look there and this is what SDD looks like:

[IMG]https://dl.dropboxusercontent.com/u/3136192/Disks%20SDD%20Partition%20View.png[/IMG]

This shows no partition in the Extended Area even though there is the 800GB ext4 logical partition with only ~300GB actually unallocated.

---

### Post by oldfred on 2013-09-07
Did you have it mounted when you made changes?

Post this to see if it shows extended partition with sdd4
       sudo parted /dev/sdd unit s print

---

### Post by ktz84 on 2013-09-07
I couldn't honestly swear that I definitely did have it unmounted when I made the changes (the changes were that sdd3 was converted from ntfs to ext4 and all logical partitions deleted and then the sdd5 created and the rest left unallocated) however I've made loads of changes to partitions over the last week as I have gradually migrated most of my data over to ext4 and moved what is left on ntfs to newly created partitions.

Some of the changes were made in Windows using the inbuilt disk management tool in Windows 7 and other with GParted so I suppose that didn't help but I just used the tool that was relevant in the OS that I was using at that time. Thankfully the that whole process of migration is almost complete assuming I get over this prob without big issues.

The output as requested is:

```
Model: ATA ST2000DL003-9VT1 (scsi)Disk /dev/sdd: 3907020911s
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start        End          Size         Type      File system  Flags
 1      2048s        81922047s    81920000s    primary   ntfs
 2      81922048s    696322047s   614400000s   primary   ntfs
 3      696322048s   1720322047s  1024000000s  primary   ext4
 4      1720324095s  3358724095s  1638400001s  extended               lba
 5      1720324096s  3358724095s  1638400000s  logical   ext4

```

So looks like it sees the extended and logical partitions ok. Hopefully that's a good start.

---

### Post by ktz84 on 2013-09-07
How very odd I just went into disks as I wanted to set up an automount on the VM partition which is on the same the disk and Disks was showing correctly the Extended Partition with Logical Partition under it correctly sized and named and the free space beside it. I then decided to see what would happen if I fired up GParted and sure enough as soon as the error message came up on the screen the Disks screen immediately changed to reflect exactly what was posted in my second post ie the extended partition disappeared at that whole part of the disk is showing as free space.

---

### Post by Quackers on 2013-09-07
It may be that the extended partition is not correctly represented in the partition table. This can happen sometimes.
It may be worth downloading and running [Fixparts]("http://sourceforge.net/projects/gptfdisk/files/gptfdisk/0.8.7/fixparts-binaries/")
after reading more about it here
[http://www.rodsbooks.com/fixparts/]("http://www.rodsbooks.com/fixparts/")

---

### Post by oldfred on 2013-09-07
Again was it mounted when you used gparted? 

And maybe Disks is interfering with gparted as both cannot open partition table at same time? I know that is an issue with updates not sure about gparted as I do use gparted on my install drive to edit partitions on another drive, but never have had issues. But I make sure nothing is mounted, or if inside an extended partition with mounted partitions, then I use live Flash drive.

---

### Post by ktz84 on 2013-09-07
Thanks oldfred. It was because I had the partition mounted. I thought when you were asking earlier about the mounted partitions it was in relation to the repartitioning only and not when I was subsequently trying to run it. The sdd5 was mounted throughout as it is set to automount. It never occurred to me that this could be issue as all my other partitions, which are primary partitions, show in GParted whether mounted or not and it's only the Extended partitions which fail to show when mounted in GParted.

The reason why I was always using GParted was that I was using it to find the UUID and to copy and paste it for partitions for autostart programs and auto mounts however I've since discovered Disks which is much handier for setting up my mounts.

---

### Post by oldfred on 2013-09-08
Disks is supposedly improved over my 12.04 Disk Utility, but I have seen issues with gpt drives. I do use Disk Utility to change labels if I forget with gparted when repartitioning or a new install.

If you want UUIDs
 # To clear cache and get new view:
sudo blkid -c /dev/null -o list

---

