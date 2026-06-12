---
title: "Wiping a removable hard disk formatted MSDOS"
date: 2014-03-27
forum: General Help
---

### Post by movrshakr on 2014-03-27
I have a tower machine running ubuntu 12.04.  It has an insertable second hard disk mounted in a removable, sliding tray.  I need to fully wipe this disk (data deletion); however it is formatted MSDOS, and I don't think the technique 
```
sudo dd if=/dev/zero of=/dev/sda2 bs=1M
```
will work if the target is formatted MSDOS.  Is that right?  If so, how can I wipe it?

---

### Post by Bashing-om on 2014-03-27
movrshakr; Oh movrshakr;

dd has earned the nickname Disk Destroyer for reason. Be very sure, look three times and KNOW exactly what dd is going to do - it is a very versatile utility and with great power. It will do what you tell it to do, even when it is not what you intended to happen !
OK, 1st lesson ->
linux drive designation:
1st hard drive is sda - that is the whole entire hard drive -
2nd hard drive will be sdb
3rd hard drive -> sdc
and so on -> d e f g ect.
Now on this physical hard drive are the individual partitions, as in
sda1 equals 1st drive 1st partition
sda2 equals 1st drive 2nd partition
sda3 1st drive, 3rd Partition
sdb3 2nd drive, 3rd partition
sde8 5th drive, 8th partition.

"msdos" is the term applied to the booting scheme for the partition table format, in linux that is the ext family of file systems.
So you want to zero out a hard disk, Be careful.. know exactly what the system assigns as to the drive disgnatation:
```

sudo fdisk -lu ## for the msdos partitioning. GPT disk ->  gdisk ##

```

You can bet your socks that "sda" is  where your operating system is installed onto. maybe sda2 is your entire operating system - invoke that dd command as you have it and your operating system is history. I would almost bet not even high dollar forensics can reclaim that data.

Be sure ! be sure !
Now if it is your intent to totally wipe a drive with dd ( hey I use it, works great, real happy with the results of this utility !) thoroughly
then:
```

sudo dd if=/dev/zero of=/dev/sdX bs=1M

```
where 'X' is the position designator that the system has assigned (a=1, b=2, c-3)
That command will write zero's on the entire hard drive.
Slowly, at the rate of about an hour per gig of size.
There is a means to get a status :
see:
```

man dd

``` for the instruction of how to ( reading the man page is a good thing to do anyway)

Be careful and sure and be aware, triple check before committing, there is no forgiveness of a mistake !

Take care and there
[INDENT][INDENT]will be happy trails for you
[/INDENT][/INDENT]

---

### Post by movrshakr on 2014-03-27
Thanks.  I am aware of the power of dd, and the sda2 I wrote was just an example that came out of my head.  i know that I must specify the right 'of'.

I gather from all that you wrote that  dd'ing a partition/drive that is MSDOS formatted is no problem.   Yes?
Will it still be partitioned after I do it?  
IOW, does that write zeros to the content of the partition which remains afterward with zeroes in it-
-or does it wipe out the partition as well?

Lastly, do I specify sd(drive) or sd(partition) in the dd command.?

Lastly#2..is there a faster way?  It is about a 100GB drive; 1gb/hour = 100 hours!!

---

### Post by Bashing-om on 2014-03-27
movrshakr; Well,

Again "dd" is versatile, if you know what you are doing, can do most any file manipulation with "dd".
In the realm of zeroing out a disk or any portion of it - any portion or all - it all depends on what you tell "dd" to do.
In this invocation it will wipe the disk of everything // oh, I was hasty .. the speed is about 1 hour to the 100 gigs ( 500GigaBytes = 5 hours)//
Inclusive of the partition tables. If one want to work at the partition level then by all means pass to "dd" as 'of =/dev/sdXY'.

> 
I gather from all that you wrote that dd'ing a partition/drive that is MSDOS formatted is no problem. Yes?

In this context, MSDOS = MicroSoft Disk Operating System ???
OR as the partitioning scheme that linux uses for the ext4 family of filesystems ?
I'll say this, Windows tools for Window's systems, ubuntu for linux file systems.
If you were to activate GParted and look at the partition options, one is 'msdos' - the partitioning scheme for a linux file system that is not related to the MicroSoft application.

And lastly- yeah there are faster ways, by varying the invocation parameters .
One such:
```

sudo dd if=/dev/zero of=/dev/sda bs=512 count=1

```
which will write 0's [s]to the whole of sda[/s], a sector at a time (bs=512) - many invocations exist - none as thorough as the one that you had originally posted ( I think).

Edit: the specifier "count=1" This command will wipe only the MBR and partition table (only the first 512 bytes of the drive) .
dd is fastest with "bs=4096" (sudodus)
[INDENT][INDENT]Hope This Helps
[/INDENT][/INDENT]

---

### Post by Mark Phelps on 2014-03-27
> however it is formatted MSDOS

Windows uses filesystems like FAT, FAT32, NTFS -- not "MSDOS".

To let us see what is really on the drive, after you have connected it, open a terminal, enter "sudo fdisk -lu" (lowercase L, not a one), and post the results.  That will list out the partitions and filesystems.

---

### Post by sudodus on 2014-03-28
You can use ***dd*** to wipe a disk or partition (overwrite with zeros) according to the good description by *Bashing-om*. It is also possible to use the shell-script ***mkusb*** according to this link to help ***dd*** finding the correct drive (and avoid destroying important data)
[URL="http://ubuntuforums.org/showthread.php?t=1958073"]
Ubuntu Forums tutorial "Howto make USB boot drives"[/URL]


But there are more efficient ways to wipe a disk (at least if it is reasonably modern). You can use ***hdparm*** according to this link
[URL="http://ubuntuforums.org/showthread.php?t=2124829"]
best way to wipe a drive[/URL]

In both cases it is very important that you know which is the intended target drive. One way to avoid mistakes is to ***remove the internal drive*** and boot from a live CD/DVD/USB drive and connect the drive you want to wipe. Then you cannot destroy the internal drive.

-o-

Finally, do you want to get a 'clean disk' for your own usage in the future, or do you want to erase confidential information?

- for a clean disk it is enough to wipe the first megabyte of the drive which erases traces from previous partition tables and certain meta-data. This can be done rather safely using ***mkusb***.

- to erase confidential information you must wipe the whole disk using ***hdparm*** (or if you prefer ***dd*** directly or via ***mkusb***).

---

### Post by movrshakr on 2014-03-28
I think I have enough to go on now.  Thanks everybody.

Mark, some linux command I used several days ago, showed that disk or the single partition that is on itas "msdos."  I confess that it was in lowercase rather than uppercase as I wrote it.

---

### Post by Bashing-om on 2014-03-28
movrshakr; Good deal.

Please see my edit to my post #4. If the need be to continue this discussion, Hey we will, we will !
Else if the matter is concluded to your satisfaction, please mark this thread solved; - 1st post -> thread tools -
Aids others seeking the information, and as well promotes the tidiness of the forum.

[INDENT][INDENT]good regards
[/INDENT][/INDENT]

---

### Post by movrshakr on 2014-03-28
OK I do have one other question just for education before we go..

previous post said
"If you were to activate GParted and look at the partition options, one is 'msdos' - the partitioning scheme for a linux file system that is not related to the MicroSoft application."

Can you elaborate on a linux fs called "msdos"?  Why would they name a linux fs with such a name?  I thought it was a FAT (i.e.msdos) partition and that linux had built in capability to read/write FAT partitions, otherwise known as msdos since that is where FAT originated.

Just trying to learn.

---

### Post by sudodus on 2014-03-28
The partition table can be 'MSDOS' - that is the classic partition table with MBR, primary, extended and logical partitions.

I think the best thing would be that you run the following command and post the output in a reply:

```
sudo parted -l
```

at the end there should be 'space' 'minus' 'ell'.

Looking at the output, we can discuss the partition table and each partition and file system.

---

### Post by movrshakr on 2014-03-28
Here is the data from two info commands

```
:~$ sudo fdisk -lu

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8f424c10

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   228380039   114189988+  83  Linux
/dev/sda2       228380040   234436544     3028252+   5  Extended
/dev/sda5       228380103   234436544     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 13.6 GB, 13613064192 bytes
255 heads, 63 sectors/track, 1655 cylinders, total 26588016 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xce59f839

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63    26587574    13293756    c  **W95 FAT32 (LBA)**
================================================
~$ sudo parted -l
Model: ATA WDC WD1200BB-16D (scsi)
Disk /dev/sda: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: **msdos**

Number  Start   End    Size    Type      File system     Flags
 1      32.3kB  117GB  117GB   primary   ext3            boot
 2      117GB   120GB  3101MB  extended
 5      117GB   120GB  3101MB  logical   linux-swap(v1)

Model: ATA Maxtor 91360U4 (scsi)

Disk /dev/sdb: 13.6GB
Sector size (logical/physical): 512B/512B
Partition Table: **msdos**

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  13.6GB  13.6GB  primary               lba

```

I was way wrong on the sdb size.  I ran the dd command to zero sdb1, and it did not take long at all.

---

### Post by sudodus on 2014-03-28
Both drives have MSDOS partition tables. Are you talking about the second drive **/dev/sdb** with size 13.6 GB? It had a FAT32 file system (found by fdisk, but not by parted). Did you wipe the whole partition **/dev/sdb1** or only part of it?

Which command did you use for wiping?

---

### Post by Bashing-om on 2014-03-28
movrshakr; Hello;

Never having had to so so; I can not from my own experience say, BUT ->
IF the disk assignments remained as your outputs denote:
> 
Disk /dev/sdb: 13.6 GB, 13613064192 bytes
<snip>
/dev/sdb1              63    26587574    13293756    c  [color=blue]W95 FAT32 (LBA)[/color]
<snip>


Then you have applied a linux tool to a Window's type file system.
> 
 I ran the dd command to zero sdb1, and it did not take long at all.


SO, OK, what is the result ? Is that usb drive still usable ?
[INDENT]inquiring minds want to know
[/INDENT]

---

### Post by movrshakr on 2014-03-28
> **sudodus said:**
> Both drives have MSDOS partition tables. Are you talking about the second drive **/dev/sdb** with size 13.6 GB? It had a FAT32 file system (found by fdisk, but not by parted). Did you wipe the whole partition **/dev/sdb1** or only part of it? Which command did you use for wiping?
wiped sdb1

used sudo dd if=/dev/zero of=/dev/sdb1 bs=1M

---

### Post by sudodus on 2014-03-29
Good, without the count specifier, it will wipe the whole target, in this case the partition **/dev/sdb1** :-)

---

### Post by movrshakr on 2014-03-29
> **Bashing-om said:**
> ...SO, OK, what is the result ? Is that usb drive still usable ?
[INDENT]inquiring minds want to know
[/INDENT]

Yes, still usable.  I had to use gparted and make a partition on the drive however.  It seems that even though I wiped sdb1, not sdb, there was no partition left on the drive.

---

### Post by SuperFreak on 2014-03-29
I wonder what the advantage of using dd over gparted to delete and format the partition which I thought would be safer? Or is this a question of a secure deletion vs a deletion that can be undone forensically through photorec or testdisk?

---

### Post by sudodus on 2014-03-30
> **SuperFreak said:**
> I wonder what the advantage of using dd over gparted to delete and format the partition which I thought would be safer? Or is this a question of a secure deletion vs a deletion that can be undone forensically through photorec or testdisk?

Yes, the latter. dd overwrites the disk space with zeros. This is not done with gparted.

If I understand correctly, wiping with hdparm is done at an even lower level, changing the allocation table of physical memory cells to logical memory cells.

---

### Post by movrshakr on 2014-03-30
> **SuperFreak said:**
> I wonder what the advantage of using dd over gparted to delete and format the partition which I thought would be safer? Or is this a question of a secure deletion vs a deletion that can be undone forensically through photorec or testdisk?I wanted to overwrite all of the data area as it had contained some files with financially sensitive data.  But I am not paranoid enough (in this case; in others, yes) to want to do an NSA level multipattern, multipass type of secure wipe.

In other words, I wanted data area sweeped, not just indexes.

---

### Post by movrshakr on 2014-03-30
> **Bashing-om said:**
> ...SO, OK, what is the result ? Is that usb drive still usable ?
[INDENT]inquiring minds want to know
[/INDENT]

OH, didn't see you said usb drive; it is not--it's a regular HD installed in a removable tray.  The tray 'receiver' installed inside the tower attached to a drive cable, but I don't remember the bus in that machine.

---

