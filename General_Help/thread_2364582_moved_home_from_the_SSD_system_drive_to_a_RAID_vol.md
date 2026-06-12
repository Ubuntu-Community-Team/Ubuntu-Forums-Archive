---
title: "moved home from the SSD system drive to a RAID volume"
date: 2017-06-25
forum: General Help
---

### Post by claudedjones on 2017-06-25
Following the instructions here: [https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving) I have migrated my /home partition from the SSD system drive to a RAID partition created using MDADM. The disk shows that /home is mounted there and it has files amounting to the right size. However, I am having one problem.
[LIST]
[*]following the instructions in this step
[/LIST]
[B]Moving /home into /old_home
[/B][FONT=Ubuntu]Backing up your old home, just in case things have not gone completely smoothly, is best done right now. Here is how: [/FONT]
[FONT=Ubuntu]As long as you have not rebooted yet, you will still see 2 copies of your /home directory; the new one on the new partition (currently mounted as /media/home) and the old one still in the same partition it was always in (currently mounted as /home). We need to move the contents of the old home directory out of the way and create an empty "place-holder" directory to act as a "mount point" for our new partition.[/FONT][FONT=Ubuntu]Type the following string of commands in to do all this at once:    [B][FONT=UbuntuMono]cd / && sudo mv /home /old_home && sudo mkdir /home
[/FONT][/B][/FONT]

[LIST]
[*]This is supposed to rename the old /home directory /old_home
[*]I edited FSTAB to mount home in my RAID volume and this has appeared to work
[*]The machine is back up and appears to be running just fine - the new drive is populated
[*]However, I can not find the old home directory now supposed to be called /home_old
I can tell that files are still there because my system drive is still populated with the same number/size files that were there before I started but without the ability to see my old /home directory, I can't delete the old files
[*]What am I doing wrong?
[/LIST]

---

### Post by TheFu on 2017-06-25
You've explained it, so it makes sense, but without any proof.  That means there is a disconnect somewhere between what you actually did and what you believe you did. ;)

Working through this usually will make the issue/mistake come to light.

*Prove to us* that you did what you claim, please.  Use the **history** to prove it.  
Exactly what did you type? When?
Exactly what is in the fstab?  
Was the old_home a separate partition on the SSD or just a directory?
**sudo parted -l** would be helpful too.

---

### Post by claudedjones on 2017-06-25
[LIST]
[*]I didn't type the following, I copy/pasted from the article:  cd / && sudo mv /home /old_home && sudo mkdir /home

[/LIST]


[LIST]
[*]Here's my FSTAB

[/LIST]

```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdc2 during installation
UUID=317cf3ba-2c6a-4793-96c0-fe6f18db3f27 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sdc1 during installation
UUID=3C22-D6E1  /boot/efi       vfat    umask=0077      0       1
/swapfile                                 none            swap    sw              0       0
/dev/md0 /home ext4 defaults,nofail,discard 0 0
```


[LIST]
[*]The old home directory on the SSD was whatever is created when you install the OS. I didn't do any custom partitions, just took defaults.
[/LIST]


[LIST]
[*]Here's the output of sudo parted -l
[/LIST]

```
Model: ATA WDC WD6002FFWX-6 (scsi)
Disk /dev/sdb: 6001GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags:  

Number  Start  End  Size  File system  Name  Flags


Model: ATA WDC WD20EADS-00R (scsi)
Disk /dev/sdc: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags:  

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  2000GB  2000GB  primary  ext4


Model: ATA TOSHIBA HDWE150 (scsi)
Disk /dev/sdd: 5001GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags:  

Number  Start   End     Size    File system  Name  Flags
 1      1049kB  5001GB  5001GB  ext4


Model: ATA Samsung SSD 850 (scsi)
Disk /dev/sde: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags:  

Number  Start   End    Size   File system  Name                  Flags
 1      1049kB  538MB  537MB  fat32        EFI System Partition  boot, esp
 2      538MB   500GB  500GB  ext4


Model: Linux Software RAID Array (md)
Disk /dev/md0: 6001GB
Sector size (logical/physical): 512B/4096B
Partition Table: loop
Disk Flags:  

Number  Start  End     Size    File system  Flags
 1      0.00B  6001GB  6001GB  ext4

Thanks for taking the time to try and solve this. 
```

---

### Post by coffeecat on 2017-06-25
@claudedjones, I've removed a motley collection of font formatting BBCode from your post and replaced it with BBCode code tags. I think you were trying to preserve the columnar formatting of your parted output with a monospace font. That doesn't work - unless you use BBCode code tags, the forum software strips out many of the space characters. Unfortunately, your fstab doesn't look much better even with code tags - that's a "feature" of fstab; it always looks a mess whatever you do. 

There's a link in my sig about using code tags if you need it.

Good luck finding a solution.

---

### Post by TheFu on 2017-06-25
Nothing is jumping out.

```
 \ls -alF /old_home
\more /proc/mdstat

```
please. Include the leading \ too. Both the command AND the output, please. That prevents any aliases.  And confusion.  There are separate reasons for those commands.

For any lurkers, copy/pasting directly from any HTML is a dangerous thing.  Always go through an editor, so you can see any hidden stuff.  Trust me on this.  Not everyone is nice and it is very easy to put other commands into HTML that won't be seen until it is too late. It is possible to run other commands, clear the line, then run what is expected too.

I like to make notes in a file as I work through stuff like this. That way I have a record of what I did, in what order. Plus copy/paste from my editor is safe.

I'm afraid that you ran those commands more than once. If so, it is possible to wipe the old directory, though I hope an error would be displayed. In my testing here, no error was shown.

---

### Post by claudedjones on 2017-06-25
I'm missing something. Do you mean me to run 
\too \ls -alF /old_home
and
\too [COLOR=#000000][FONT=&amp]\more /proc/mdstat[/FONT][/COLOR]

---

### Post by claudedjones on 2017-06-25
This is what I get if I simply run the commands you asked for
```

$ \ls -alF /old_home
ls: cannot access '/old_home': No such file or directory


$ \more /proc/mdstat
Personalities : [raid1] [linear] [multipath] [raid0] [raid6] [raid5] [raid4] [raid10]  
md0 : active raid1 sdb[1] sda[0]
      5860391488 blocks super 1.2 [2/2] [UU]
      bitmap: 3/44 pages [12KB], 65536KB chunk

```

---

### Post by TheFu on 2017-06-25
Things aren't adding up with the md0 array. The parted cmd isn't showing any sda.

The ls command just proves to me that /old_home is gone. Don't know what happened to it, but it is gone and any data inside it is also gone.  That doesn't mean it isn't named differently, but only you would know that.

If you know of a specific filename that was only in the prior /home directory, you can search for it using 'find', just be certain it is unique. Give it some time. It will take awhile. It will only work if the location with the file is currently mounted (and not encrypted). If it isn't, then 'find' won't see it.

Thanks to coffeecat for fixing the formatting, **repeatedly**.

---

### Post by claudedjones on 2017-06-25
[COLOR=#000000]OK - I think I figured out this code box bit. Let's see if this works. Here's the parted -l command run again. It's showing the /dev/sda now. But, it's also reporting that my primary GPT table is corrupt, but the backup is OK and is being used. What have I wrought? 

[/COLOR]```
[FONT=monospace][COLOR=#54FF54]**cjones@CJUbuntuStudio**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454FF]**~**[/COLOR][COLOR=#000000]$ sudo parted -l[/COLOR]
[sudo] password for cjones:  
Error: The primary GPT table is corrupt, but the backup appears OK, so that will
be used.
OK/Cancel? OK                                                              
Model: ATA WDC WD6002FFWX-6 (scsi)
Disk /dev/sda: 6001GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags:  

Number  Start  End  Size  File system  Name  Flags


Error: The primary GPT table is corrupt, but the backup appears OK, so that will be used.
OK/Cancel? OK                                                              
Model: ATA WDC WD6002FFWX-6 (scsi)
Disk /dev/sdb: 6001GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags:  

Number  Start  End  Size  File system  Name  Flags


Model: ATA WDC WD20EADS-00R (scsi)
Disk /dev/sdc: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags:  

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  2000GB  2000GB  primary  ext4


Model: ATA TOSHIBA HDWE150 (scsi)
Disk /dev/sdd: 5001GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags:  

Number  Start   End     Size    File system  Name  Flags
 1      1049kB  5001GB  5001GB  ext4


Model: ATA Samsung SSD 850 (scsi)
Disk /dev/sde: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags:  

Number  Start   End    Size   File system  Name                  Flags
 1      1049kB  538MB  537MB  fat32        EFI System Partition  boot, esp
 2      538MB   500GB  500GB  ext4


Model: Linux Software RAID Array (md)
Disk /dev/md0: 6001GB
Sector size (logical/physical): 512B/4096B
Partition Table: loop
Disk Flags:  

Number  Start  End     Size    File system  Flags
 1      0.00B  6001GB  6001GB  ext4



[/FONT]
```

[COLOR=#000000]

[/COLOR]

---

### Post by TheFu on 2017-06-25
A corrupt GPT is always a concern.  This is especially important to fix since the 2 copies are at opposite ends of the drive.  Better redundancy than with an MBR partition scheme.

There are a few best practices for using RAID.  1 is to create a partition to hold the RAID, which is not the situation with your sda and sdb.  Old-school was to skip making a partition table plus partitions for RAID, making the entire disk the storage for RAID.  Doing so means there aren't partition tables for normal OS tools to see and inexperienced people looking at the disks could easily assume them to be empty or corrupted.

That doesn't help much and I probably wouldn't go back and attempt to redo the RAID just to add a partition table and 1 partition to hold everything.  I'd guess it is a 50/50 "best practice", not a 90/10 one.

Since you didn't mention the other suggestions, I suppose you aren't interested, so I'll bow out now. Hopefully someone else will be able to help.

---

