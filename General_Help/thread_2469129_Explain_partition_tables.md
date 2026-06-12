---
title: "Explain partition tables"
date: 2021-11-20
forum: General Help
---

### Post by sofasurfer on 2021-11-20
I have never touched a partition table as far as I know. Yet on partitioning tools I see "create new partition table". Why and when would I need to do this?

---

### Post by rsteinmetz70112 on 2021-11-20
I'm not sure how you managed to get to 2021 from 2008 without needing to know about partition tables. 

But let me try to help. A partition table divides up storage into areas to be used for various purposes. Ubuntu will do it for you if you install on a new or unformated drive.The Ubuntu installer can wipe out the existing partition table and create a new one. 

There are two types main of partition tables commonly in use
[LIST=1]
[*]MBR (The old MSDOS type) and 
[*]GPT a newer more flexible type.
[/LIST]
 WHy do you want to know after all this time?

---

### Post by sofasurfer on 2021-11-21
I have always used Gparted to create partitions and also and also created partitions using live dvds when installing Ubuntu. However, everything is automatic. I assumed that part tables were created during installations and when creating new partitions but I have never needed to click on the "create new partition table" button. I stumbled on a reference to creating partition tables in a post yesterday and it got my curiosity up. I have always though messing with partition tables was a no-no if you didn't know what you were doing.  And since my installation disk always took care of it I never had a reason to risk it.
If partitioning IS creating a partition table then how is creating a part table a process used outside of installing?

---

### Post by yancek on 2021-11-21
The first link below is to the GParted Manual which you indicate some familiarity with.  Most of us are at least somewhat familiar with it.  I keep that page bookmarked, never know when you might need it and it is very useful to have available before trouble.

[https://gparted.org/display-doc.php%3Fname%3Dhelp-manual](https://gparted.org/display-doc.php%3Fname%3Dhelp-manual)

The link below is the manual for the software 'Parted', GParted is basically the graphical version of Parted.

[https://www.gnu.org/software/parted/manual/parted.html](https://www.gnu.org/software/parted/manual/parted.html)

> However, everything is automatic. I 

It may seem so and even be so in many cases but it isn't always.  Have you never used the 'manal' Something Else option in Ubuntu?  You can create partitions which will modify your partition table or you can let the installer do whatever it does automatically.  Create a / (root filesystem) partition, create a separate /home partition, or create a separate data partition for personal data or to share between users.  All kinds of options.

I would agree that 'messing' with partition tables can be very risky if you don't know what you are doing and I would not advise anyone to do so until AT LEAST becoming familiar with software such as GParted.

> I have never needed to click on the "create new partition table" button.  

You may never have to but if you do, the message you will see will be to the effect that making that selection will destroy all data on the device!  Guess what, they're not joking.  I believe you actually get 2 warnings.  One instance where this is often necessary is after writing an iso to a usb stick with dd and being unable to use the usb again until creating a new partition table.

> If partitioning IS creating a partition table then how is creating a part table a process used outside of installing? 		 

You 'seem' to be confusing modifying a partition table with creating a new partition table.  You can do both.  Create a new partition table is very different than modifying a partition table during install.  The creating new part as explained above destroys all data, stay away unless you know exactly what you want and are doing.

If you are a basic home computer user, you will know that historically, almost all computers for home use are sold with an operating system (and hence partitions and a partition table) already existing.  THis of course has usually been some form/version of windows.  If you have a blank drive, you can use GParted or similar software to 'create a new partition table' and to create any number of partitions n that drive (I believe the limit with GPT drives is 128).  You can create filesystems on these partitions also but don't need to, they will still exist.  Without a filesystem though they will be useless.  You don't need to be installing anything, you can create the partition table along with as many partitions as you wish and not use them for either the OS or data so installing an OS isn't necessary after creating a partition table but you do need to create or have a partition table to install any OS.  If you really want to understand you need to read the GParted Manual from the link above.

---

### Post by The Cog on 2021-11-21
> If partitioning IS creating a partition table then how is creating a part table a process used outside of installing?
Creating a new partition table is something you would do either to a brand new disk, or to a used disk where you want to completely start afresh by wiping away the old content and making a new install. Making a new partition table will overwrite any existing partition table, wiping any record of what partitions used to be there and where they were located on the disk. Note that writing a new partition table will not overwrite the actual partitions, just the record of their location and type. This means that if you were to write a new partition table in error, and not write anything else, a data recovery specialist may be able to examine the disk and work out where the partitions were and re-make the old partition table. 

Note that Windows likes to portray different partitions of the same disk as different "drives", so that often the Windows system C: and user data D: are just different partitions on the same drive. 

Partition tables can also be edited for various reasons. For example, I tend to leave some unused space on large disks, to expand into later. I might then choose to add a new partition in that space, or enlarge an existing partition into that space. I also like to keep my last Ubuntu installation there when I install the next version, just in case the next version has some problem I can still boot the previous version. This means I now always use the "something else" option when installing Ubuntu, and tell it to install onto the partition that contains the older version, leaving the newer version unused (but there in case I want to revert to it).

The partition table specifies the location and type of the partition, that's all. In general, you will wnat to place a file system on a partition after it has been created. There are many different file system types, such as NTFS (Windows), ext4 (Linux). The file system's primary task is to maintain an index to keep track of the location of different files it contains. Putting a file system on a partition is called **formatting** it, and much like the partition table, overwriting the index with an empty one (or different type) loses all index information about previous contents.

Modern machines always have an EFI partition that contains the bootloader (I think - I'm hazy about the relationship between gpt partition tables end efi partitions).

Installing an OS involves:
* Ensuring there is a partition table, either creating a new one or re-using an existing one
* Ensuring one (or more) partitions are formatted ready to have the OS installed on them
* Writing the OS files to the file system(s)
* Configuring the machine to boot from the correct partition.

Anyway, hope this helps.

---

### Post by sofasurfer on 2021-11-21
Thanks for all your answers. It does open my eyes a little. I will start reading the links offered above.
At this point I think that partition table is a index or table of contents of a hard drive. A part table is created when a disk is partitioned but is not the whole disk itself. If partitioned are changed, moved or modified the table must be changed to reflect these changes. If partitions are created on a blank disk a table must be created to tell where everything is.
Sounds good to me anyway. I will start learning. 
Thanks.

---

