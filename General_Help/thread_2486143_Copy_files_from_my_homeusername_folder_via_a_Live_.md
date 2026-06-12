---
title: "Copy files from my /home/username folder via a Live USB Boot Session"
date: 2023-04-21
forum: General Help
---

### Post by DeadlyOats on 2023-04-21
I'm in the process of trying to recover my system.  However, in the event that I can't, I want to try Plan B.  That is to copy files that are on my desktop folder and save them on another folder.  I saw this:

[PHP]Method 2. Transfer files you want to save

1. Boot from a Live Session
2. Open the partition where the files are located
3. Create a new folder somewhere on the partition such as the Desktop on the partition
4. Right-click on each file or folder you want to save
5. Click on "Copy to..." or "Move to..."
6. Navigate to and open the folder you just created
7. Click Select at the top right
8. After moving all items to that folder, "Copy to..." or "Move to..." a flashdrive, external, or "secondary" HDD or SSD[/PHP]

I found that, here:

[https://ubuntuforums.org/showthread.php?t=2472549&highlight=copy+files+desktop+boot+install](https://ubuntuforums.org/showthread.php?t=2472549&highlight=copy+files+desktop+boot+install)

I tried it, but my /home/username folder is locked, and I can't get to my desktop folder.

How can I get this to work?  Or will this not work?  Is there another way?

---

### Post by TheFu on 2023-04-21
Learn about Unix permissions.  Until you do, you will have hours, days, weeks, months of frustration over trivial things. There are many tutorials.  It isn't worth trying to explain them here, since they are well-covered all over the internet.
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions) is one, but any Unix tutorial is just as valid.  Every popular OS in the world today, except 1, uses the same Unix permission model.

I've posted very simple backup, versioned, backup commands in these forums many times.  In general, backups need to be run as root, which on Ubuntu means using the **sudo** command. Put the script below into a file, change the permissions so it is executable and can be read.  Edit the TGT and how many days of versioned backups you want to retain.  The TGT should be on different storage, with a native Linux file system. ext4 would be a good choice.  DO NOT USE NTFS, FAT32 or exFAT.  They won't work.

```

#!/bin/bash
TGT=/Backups
DAYS=120

# Local Backups; **all backups need to run as root**, to capture file metadata
/usr/bin/rdiff-backup \
        --exclude-sockets --exclude-device-files --exclude-fifos \
        --exclude '**/.cache'  --exclude "$TGT" \
        --include /usr/local   --include /etc  \
        --include /root        --include /home \
        --exclude '**'   /       "$TGT"

# Trim old backups from long ago
/usr/bin/rdiff-backup  --remove-older-than "$DAYS"  --force "$TGT"
```

If you named the file **bak-test** and put it into ~/bin/bak-test, then you'd run it with 
```
sudo ~/bin/bak-test
```
After it is tested and works, you can place the script into /etc/cron.daily/ and it will be run daily, automatically.  If it backs up 10G, then 90 days will take about 13G of storage.  Of course, YMMV. The size is just an estimate based on my use here.  The first run (in the test) will take as long as a normal rsync takes, but every run after that will only take as long as the changed data requires. It is very storage and speed efficient.

If you look in the $TGT directory, you'll see that the last backup is a mirror of the source files. Older versions are efficiently stored as gzipped diff files.  This works fine for most types of files with the exception of huge binary files ... like videos or virtual machines stored inside 1 file.  Those need a different backup method.

---

### Post by ne29914 on 2023-04-21
This is the way I do it:
1: do a live boot.
2: open Terminal
3: run: sudo mount /dev/sdxy /home (where /dev/sdxy is /dev/sda2 or wherever your /home partition is

Now you can access your data partition and copy your data to a thumb drive or whatever. If you only have one / partition and nothing alse, I don't know how to help.

---

### Post by DeadlyOats on 2023-04-26
So, I actually gave up on saving the files and did a complete re-install.  However, I wanted to try out your method as an experiment.  So, I created a dummy file and set it on my desktop.

Because of a line that you said, > If you only have one / partition and nothing alse, I don't know how to help.  I decided to create separate partitions for / and /home.

I typed in the command: [PHP]sudo /dev/sda3/home[/PHP] 

I got back the answer: [PHP]/dev/sda3/home: can't find in /etc/fstab[/PHP]

So, I'd like to get this ironed out, so that in the future, if I have to try this method of recovering files, I'll get it to work.

Thanks

---

### Post by TheFu on 2023-04-26
> **DeadlyOats said:**
>  
I typed in the command: ```
sudo /dev/sda3/home
``` 

This isn't correct.
a) there's no command specified
b) /dev/sda3/home doesn't make sense

sudo to what?  
sudo {COMMAND} {inputfile}

Device files don't directly get accessed as directories.  /dev/sda points at the first SCSI/SATA/eSATA disk discovered by the kernel, this boot.  If you have more than 1 of those disks connected, the order can change, so the same disk could be /dev/sda or /dev/sdb ... it comes down to the timing of the kernel's discovery efforts.  Sometimes that is tied to how long a drive takes to spin up too.

/dev/sda1 would be the first partition on drive "sda".
/dev/sda2 would be the second partition on drive "sda".
/dev/sda3 would be the third partition on drive "sda".
Partition numbers aren't positional on the drive. They are strictly by the order created. That doesn't usually matter. Just some trivia.

Typically, if no volume manager is used, then a file system will be placed onto a partition. It is possible to have partitions without any file system or used for other purposes, but in a simplistic drive setup, the ext4 file system would be placed onto the partition and can be referenced in that way for mounting.  

Until the file system is mounted, using the correct file system type, it isn't accessible as directories.  There must be 50 file systems with 20 of them commonly seen on Linux. Windows basically has 1 file system, NTFS, though it has many versions since 1990s when it was first introduced.  MSFT has done a good job if hiding the different versions of NTFS from the world by ensuring backwards compatibility.  In the Linux world, we'd typically see ext4 today or xfs, though btrfs and ZFS are becoming more popular for people who want/need more advanced volume management + file systems.

Anyway, if you want to mount a file system on sda3, then a possible solution would be
```
sudo mkdir /mnt/3
sudo mount -t ext4 /dev/sda3 /mnt/3
```
If some other file system was used, then that would need to be specified. Also, if the file system were corrupted, it is possible that the mount would be refused and corrective action would be suggested, like running an **fsck**.

And as always, there's no getting around normal Unix file and directory permissions. Those will need to be addressed to provide access. In Unix/Linux, the owner, group, and permissions are very important.  If those aren't set correctly, then some programs may refuse to work.

---

### Post by ajgreeny on 2023-04-27
As TheFu said, you can not use /dev/sda# in a **cp** command but must use the mountpoint of that device -see below.

The mountpoint can be anywhere you wish but if a USB flash drive is automounted when attached it should be seen in /media/username/USBid and that USBid will be either the UUID of the USB's partition or its label.

Always label partitions and you will reduce your frustration when dealing with this in future

---

### Post by DeadlyOats on 2023-04-27
Ack!  Sorry!  That's a mistake!  I typed the command:

[PHP]sudo mount /dev/sda3/home[/PHP]

I got this as a reply from the system:

[PHP]/dev/sda3/home: can't find in /etc/fstab[/PHP]

---

### Post by yancek on 2023-04-28
>  [COLOR=#000000][COLOR=#0000BB]sudo mount [/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000BB]dev[/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000BB]sda3[/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000BB]home[/COLOR][/COLOR]

That won't work.  See post 5 above which explained it and showed the proper command.  You need to use or create a mount point (mount means to make accessible) and you can use the /mnt directory to do that so you do not need to create a separate, new directory.  I'm not sure what the point is unless you are just practicing the cp command.  Copying a directory or files to another location on the same partition and same drive is not a backup.  You need to use a separate drive as shown in the initial post so why not just do that directly?

---

### Post by TheFu on 2023-04-28
> **DeadlyOats said:**
> Ack!  Sorry!  That's a mistake!  I typed the command:

[PHP]sudo mount /dev/sda3/home[/PHP]

I got this as a reply from the system:

[PHP]/dev/sda3/home: can't find in /etc/fstab[/PHP]

That **DOES NOT** look correct - I mean it is an error.  /dev/sda3/home doesn't make sense. It never will, no matter how many times you try.  You need to "mount" the file system, before you can access any files or directories inside it.  I don't know how to say it any clearer.

A file system cannot be accessed in the most useful way (files and directories), until it is mounted. 
If /dev/sda3 is still the correct device (that changes from boot to boot), then the correct mount commands are in post #5 above.  Did you try those commands?

Spaces matter in those commands.

---

### Post by zebra2 on 2023-04-29
I keep a bootable Puppy Linux USB handy and have no problem doing what you are trying to do.  I can even edit my 40_custom file in the root directory with no issues.  "Focal Puppy" is the version you will want to use.  You don't need to bother to setup wifi or anything since you are just moving files from one partition to another.  Its free so nothing to lose.  I use Rufus on my Windows machine and a puppy ISO to make the boot disk. FYI

---

### Post by ne29914 on 2023-04-29
You have a typo in your command.
It should read:
```
sudo mount /dev/sda3 /home
```
/dev/sda3 is the partition, /home is the mount point.

---

