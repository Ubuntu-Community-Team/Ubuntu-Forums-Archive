---
title: "What will be an easy way to copy a HDD"
date: 2022-04-03
forum: General Help
---

### Post by satimis on 2022-04-03
Hi all,

Can I run **[COLOR="#FF0000"]dd command [/COLOR]**to dump/duplicate all data files from a HDD to another HDD

From:
HDD-1
WD HDD SATA3
Capacity 4TB, about 3.1TB free and without partition
Format - ext4
Only data files and folders, without OS installed

To:
HDD-2 (old HDD)
WD HDD SATA
Capacity 1.5TB, without partition
All data can be deleted

Do I need to run **[COLOR="#FF0000"]fdisk[/COLOR]** to delete its content first?

The HDD-2 will be installed on another PC.

Please advise.  Thanks

Regards

---

### Post by Impavidus on 2022-04-03
How "no partition"? You can create the filesystem directly on the entire drive, but that's very uncommon. Or is there one big partition, covering the entire drive?

You can use dd to clone a filesystem or entire drive, but only if the destination is at least as large as the source. So if the filesystem on the 4TB drive is smaller than 1.5TB, it can be done. Otherwise, it can't. And that's about the size of the filesystem, not what's actually used by the files.

---

### Post by HermanAB on 2022-04-03
You can just copy the whole device with cat or dd or a zoo of other utilities:
# cat /dev/sda > /dev/sdd

However if you put the wrong destination device, then the result could be very disappointing, and if the disk is mostly empty and very big, then it can take a looong tiiime.

Also, if you would then immediately try to boot off the disk, mounting will fail since the UUIDs in fstab will be wrong. So some minor editing of settings are needed in that case.

---

### Post by satimis on 2022-04-03
> **Impavidus said:**
> How "no partition"? You can create the filesystem directly on the entire drive, but that's very uncommon. Or is there one big partition, covering the entire drive?

You can use dd to clone a filesystem or entire drive, but only if the destination is at least as large as the source. So if the filesystem on the 4TB drive is smaller than 1.5TB, it can be done. Otherwise, it can't. And that's about the size of the filesystem, not what's actually used by the files.
Thanks for your advice.

There is no OS running on the storage HDD.  Ubuntu 20.04 is running on a NVMe PCIe 3.0 SSD.  The WD 4TB HDD is solely for storing Linux data files.

I'm going to build a new Dual-boot desktop PC.  I need to copy all files and folders to the old HDD-2 and install it on the new PC.  Newly created data will not be stored on the old HDD-2.

On the new Dual-boot desktop PC there are 2 SSDs
1)
ADATA 2TB XPG GAMMIX S70 BLADE AGAMMIXS70B-2T-CS M.2 2280 PCIe Gen4x4 NVMe SSD
for running Ubuntu 20.04/22.04 (Linux) and virtualization (Oracle VirtualBox)

2)
ADATA 1TB XPG LEGEND 840 PCIe Gen4 x4 M.2 2280 SSD
for running Windows11 64bit

There will be sufficient space for storing newly created data

I can run drag & drop to copy all Linux data from HDD-1 to HDD-2.  But I need to run "fdisk" to delete all data on the old HDD-2.  I'm searching for an easy way to clone/dump all data direct from HDD-1 to HDD-2 without the step of "fdisk".  Besides drag & drop is too slow in operation

Regards

---

### Post by satimis on 2022-04-03
> **HermanAB said:**
> You can just copy the whole device with cat or dd or a zoo of other utilities:
# cat /dev/sda > /dev/sdd

However if you put the wrong destination device, then the result could be very disappointing, and if the disk is mostly empty and very big, then it can take a looong tiiime.

Also, if you would then immediately try to boot off the disk, mounting will fail since the UUIDs in fstab will be wrong. So some minor editing of settings are needed in that case.
Thanks for your advice.

Ubuntu 20.04 is running on a 1TB NVMe PCIe SSD.  I'll unplug all other drives on the PC before testing, leaving only the NVMe PCIe SSD, HDD-1 and HDD-2 connected.

I don't need all old data on HDD-2.  I expect to over-write them on copying the Linux data from HDD-1 to HDD-2

I'll run "fdisk" to find out /dev/sdx and /dev/sdy for HDD-1 and HDD-2 ?  
**[COLOR="#FF0000"]$ sudo fdisk -l | grep /dev/sd[/COLOR]**

I don't think I can copy data from "1TB NVMe PCIe SSD" to itself ?

Regards

---

### Post by tea for one on 2022-04-03
Prepare an ext4 partition on your destination disk HDD-2.
This new partition must be the same size or slightly larger than your source partition on HDD-1

Create a live Clonezilla USB [https://clonezilla.org/](https://clonezilla.org/)
Clone the data using Device to Device option with sub-menu Partition to Partition.

---

### Post by TheFu on 2022-04-03
**dd** is a block-level copy tool.  Probably want to use **ddrescue** instead if dd is the choice. Many reasons.

If you want to copy files above the file system layer, then use **rsync**.  Much faster. Can pick up in the middle easier, and can be used to re-sync over and over and over again while keeping or losing ownership, group, and permissions, as you like.

[LIST=1]
[*]HDDs/SSDs have 5 basic logical layers.
[*]Partition table - MSDOS or GPT
[*]Partitions - at least 4 primary or 128 primary if GPT
[*]File systems - each partition can have a different file system
[*]Files and directories
[/LIST]
rsync works at the highest layer.
dd/ddrescue can work at the whole disk or partition or file layer.  The source and target devices/files determine which layer is used.
[LIST]
[*]/dev/sda == whole disk
[*]/dev/sda1 == 1st partition on sda
[*]/home/bob/some-file == 1 file to be copied
[/LIST]
dd/ddrescue are cumbersome to use for copying 1 file.   Though on Unix-like systems, almost everything is a file and can be accessed. That's why the whole disk file (/dev/sda) can be accessed and copied/cloned.

**fsarchiver** is typically used at the partition layer ... but it gets the file system and all data inside it, not the partition size, location, etc. For certain file systems, it is smart and supports restoring to smaller partitions.  Dumber tools like dd/ddrescue don't like to be copied to smaller partitions. That's because they work at the block level and don't know anything about the data contained in those blocks.

Of course, there are a few caveats about accessing any device files, but depending on the goal, even if it is slow, it doesn't care about the file system or partition table. To block tools, those are just data.

---

### Post by TheFu on 2022-04-03
> I don't think I can copy data from "1TB NVMe PCIe SSD" to itself ?

You can but it is a really bad idea.  Unix doesn't ask if a command is stupid or not. If the input and the output are the expected types (a file), then it can be done.  I highly doubt you'll end up with what you hope to achieve.  **_No way would I do this on purpose._**

---

### Post by satimis on 2022-04-03
Hi all,

Lot of thanks for your advice.  On summing up your advice I think the reliable solution is;

1. Run fdisk to create a single partion on HDD-2 and format the whole drive as ext4
2. Run "drag & drop' copying all folders and files from HDD-1 to HDD-2

This is the traditional method, taking more time to finish. But it is a safe way.

---

### Post by satimis on 2022-04-03
> **TheFu said:**
> **dd** is a block-level copy tool.  Probably want to use **ddrescue** instead if dd is the choice. Many reasons.

If you want to copy files above the file system layer, then use **rsync**.  Much faster. Can pick up in the middle easier, and can be used to re-sync over and over and over again while keeping or losing ownership, group, and permissions, as you like.
....... 

Could you please advise how to do it running **[COLOR="#FF0000"]rsync[/COLOR]**.

I only need copying all data from HDD-1 to HDD-2, retaining their properties.  Nothing else

Regards

---

### Post by oldfred on 2022-04-03
I think rsync is the most traditional.
rsync has many parameters but simple copy only needs a few.

[https://ubuntuforums.org/showthread.php?t=2471454&p=14078689#post14078689](https://ubuntuforums.org/showthread.php?t=2471454&p=14078689#post14078689)

I copy folders to a flash drive so I can then copy them to another system. Since I do not want to readd the deleted files I add a deleted flag. 
rsync -aruvP --delete /mnt/data/Documents /media/fred/data256a
Mount point for /mnt/data exists and has many folders. The mount for media/fred is created by plugging in flash drive.

---

### Post by TheFu on 2022-04-03
> **satimis said:**
> Could you please advise how to do it running **[COLOR="#FF0000"]rsync[/COLOR]**.

I only need copying all data from HDD-1 to HDD-2, retaining their properties.  Nothing else

Regards

Rsync doesn't work at the HDD level. It works at the directory level.

If you don't care about permissions, ownership, groups, ACLs ... and just want the data ... which is almost always safe for HOME directories, but never safe for the OS or programs, then 
```
SOURCE=/home/bob
TARGET=/mnt/backup/home/bob
rsync -avz "$SOURCE" "$TARGET"

```
Simple. This will make all the files owned by the userid running the rsync program.

If there are sparse files, you'll want to add a sparse file option (--sparse) so those don't get expanded.  The manpage has more details and is extremely expansive.  It is worth looking for web pages with _10 rsync examples_ too. Some people learn better through examples.

Also, the target file system needs to support the same permissions model as the source, if you want those to be retained.  Generally, it is a bad idea to try a system backup from EXT4  to NTFS. It won't work.  Sure, you'll get the data, but all the permissions, group, ownership and ACLs will be lost.  **File systems matter.**

Let's say you want to backup all the data for 10 users on the computer and retain the permissions, ownership, groups with the data.  Then
```
SOURCE=/home
TARGET=/mnt/backup/home
sudo rsync -avz "$SOURCE" "$TARGET"

```
is the command I'd use.  Be 100% certain that the target file system supports Unix permissions.

If the TARGET is on a different machine and ssh connectivity is setup, then you can use 
```
TARGET="1.2.3.4:/mnt/backup/home/bob"
```
instead to have bob's (assuming you are bob and bob is running the rsync command) files copied.  rsync can pull or push data between different systems and will retain permissions/ACLs, ownership/group as much as allowed by the userid running the rsync command. It is slightly complex when a remote copy of OS files or files owned by multiple users are included. Basically, remote root access is required, which leads to all sorts of security implications and decisions.  I just saw the *--fake-super* option, which might be a way do not use root, but get backups. I've not used it myself.  Interesting.

Almost all Unix backup tools use librsync underneath, so learning how rsync works is very useful.  I use rsync a few times most days. Mainly to ensure 2 copies of media files are stored on different physical media.

BTW, rsync has a --dry-run  option.  Add that and it will show what it would do, without doing anything.  Also, rsync doesn't delete anything in the TARGET without an explicit option to do that.  If you want clear progress, use *--progress --stats *options.

The -x option (--one-file-system) is handy too, to prevent getting more stuff than you want.

---

### Post by SeijiSensei on 2022-04-03
There are subtle differences depending on syntax. That's why I almost always do a dry-run first.

For instance
```
rsync -av source:/path/to/directory /path/to/target
```
will include the directory along with the files within it.
```
rsync -av source:/path/to/directory/ /path/to/target
```
will copy only the files in the source directory but not the parent directory itself.

---

### Post by TheFu on 2022-04-03
@SeijiSensei is correct as usual.  

The main reasoning is to make it easy to get .dotfiles when /home/bob/* wouldn't.
/hom/ebob/ and /home/bob would.  At least that's my sense for why the trailing / is handled in a special way.  When I backup stuff, getting my personal settings (.dotfiles) is one of the most important things that I definitely want.

---

