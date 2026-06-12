---
title: "Flashdrive Recovery"
date: 2023-05-30
forum: General Help
---

### Post by wyattwhiteeagle on 2023-05-30
```
Error mounting /dev/sdb at /media/wyatt/New Volume:
Unknown error when mounting /dev/sdb
```

From lsusb
```
Bus 002 Device 003: ID 0781:5575 SanDisk Corp. Cruzer Glide
```

KDE Partition Manager - Partition Table Export
```
##|v1|## partition table of /dev/sdb# on Tuesday, 30 May 2023 05:13:14 EDT
type: "msdos"
align: "sector"


# number start end type roles label flags
1;1936269394;3772285809;unknown;primary;"";""
2;1917848077;2462285169;unknown;primary;"";""
3;1818575915;2362751050;unknown;primary;"";""
4;2844524554;2844579527;unknown;primary;"";""
```

i don't understand why I hit this error.
KDE Part Manager had the "mount" grayed out

Where do I go from here?

I don't even know where to start.
Data recovery?
Troubleshoot the error in hopes of correcting?
How would I even accomplish that?

I got this error when I performed a fresh clean install of Lubuntu about a month ago.
It seems the "new install" doesn't recognize the flashdrive.
It contains important files I don't need to be losing.

It's a new flashdrive from Walmart...I know, not the best place for electronics.

The machine is a Dell Latitude E5400 CKNVVK1
The flashdrive is a 64gb Sandisk Cruzer Glide

I need a better alternative for storing my files.
I started a thread for that...
[https://ubuntuforums.org/showthread.php?t=2487305](https://ubuntuforums.org/showthread.php?t=2487305)

---

### Post by yancek on 2023-05-30
How did you try to mount it, from a terminal or GUI file manager?  Try using the filesystem option.  If you have several partitions, use whatever filesystem you have to try to mount as in the example below:

```
sudo mount -t ext4 /dev/sdb1 /media/wyatt/New-Volume
```

Don't use spaces in the directory names.

---

### Post by ActionParsnip on 2023-05-30
sdb is the disk, /dev/sdb1 will be the first file system which you can mount. You won't be able to mount /dev/sdb

---

### Post by wyattwhiteeagle on 2023-05-30
> **ActionParsnip said:**
> sdb is the disk, /dev/sdb1 will be the first file system which you can mount. You won't be able to mount /dev/sdb
Uh oh...does that mean the flashdrive is unrecoverable?

> **yancek said:**
> How did you try to mount it, from a terminal or GUI file manager?  Try using the filesystem option.  If you have several partitions, use whatever filesystem you have to try to mount as in the example below:

```
sudo mount -t ext4 /dev/sdb1 /media/wyatt/New-Volume
```

Don't use spaces in the directory names.


I ran it...
```
sudo mount -t ext4 /dev/sdb1 /media/wyatt/New-Volume
```


Here's what I got...
```
mount: /media/wyatt/New-Volume: mount point does not exist.
```


I usually just plug in the flashdrive and it mounts to media automatically.


The /media that things are being mounted to is default installed and it looks and acts like a directory.
I'm not sure how the system mounts things to /media.

---

### Post by ajgreeny on 2023-05-30
More detail needed.

Have you used that flash drive as an install medium with which you installed Ubuntu or other distro?
Have you used it in a Windows computer and not properly removed it, ie, after unmounting or ejecting it?

Insert it and then run```
sudo parted -l
``` and ```
sudo fdisk -l
```which might give us some clues about the flash drive.

---

### Post by wyattwhiteeagle on 2023-05-30
Would gdisk, testdisk, or any info at this link help my situation?
[https://www.r-studio.com/free-linux-recovery/](https://www.r-studio.com/free-linux-recovery/)

> **ajgreeny said:**
> More detail needed.


Have you used that flash drive as an install medium with which you installed Ubuntu or other distro?
Have you used it in a Windows computer and not properly removed it, ie, after unmounting or ejecting it?


Insert it and then run


```
sudo parted -l
```


and 


```
sudo fdisk -l
```


which might give us some clues about the flash drive.


Have you used that flash drive as an install medium with which you installed Ubuntu or other distro?
No, I haven't.


Have you used it in a Windows computer and not properly removed it, ie, after unmounting or ejecting it?
I have used it in a Windows computer but have always properly removed it.


```
sudo parted -l
```
```
Model: ATA WDC WD800BEVT-75 (scsi)
Disk /dev/sda: 80.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 


Number  Start   End     Size    Type     File system  Flags
 1      1049kB  80.0GB  80.0GB  primary  ext4         boot




Model: SanDisk Cruzer Glide (scsi)
Disk /dev/sdb: 63.5GB
Sector size (logical/physical): 512B/512B
Partition Table: loop
Disk Flags: 


Number  Start  End     Size    File system  Flags
 1      0.00B  63.5GB  63.5GB  ntfs
```


and 


```
sudo fdisk -l
```
```
Disk /dev/sda: 74.53 GiB, 80026361856 bytes, 156301488 sectors
Disk model: WDC WD800BEVT-75
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x4196e8af


Device     Boot Start       End   Sectors  Size Id Type
/dev/sda1  *     2048 156296384 156294337 74.5G 83 Linux




Disk /dev/sdb: 59.16 GiB, 63518539776 bytes, 124059648 sectors
Disk model: Cruzer Glide    
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x6e697373


Device     Boot      Start        End    Sectors   Size Id Type
/dev/sdb1       1936269394 3772285809 1836016416 875.5G 4f QNX4.x 3rd part
/dev/sdb2       1917848077 2462285169  544437093 259.6G 73 unknown
/dev/sdb3       1818575915 2362751050  544175136 259.5G 2b unknown
/dev/sdb4       2844524554 2844579527      54974  26.8M 61 SpeedStor


Partition table entries are not in disk order.
```

---

### Post by ajgreeny on 2023-05-30
```
Device     Boot      Start        End    Sectors   Size Id Type
/dev/sdb1       1936269394 3772285809 1836016416 875.5G 4f QNX4.x 3rd part
/dev/sdb2       1917848077 2462285169  544437093 259.6G 73 unknown
/dev/sdb3       1818575915 2362751050  544175136 259.5G 2b unknown
/dev/sdb4       2844524554 2844579527      54974  26.8M 61 SpeedStor
```
These partition types found on the disk mean nothing to me and a search of the forum and other sites such as AskUbuntu has got me nowhere useful for your problem.

I do hope that any files you have on the disk are available on some other storage device as that may be the best way to ensure they can still be used again!

---

### Post by wyattwhiteeagle on 2023-05-30
> **ajgreeny said:**
> ```
Device     Boot      Start        End    Sectors   Size Id Type
/dev/sdb1       1936269394 3772285809 1836016416 875.5G 4f QNX4.x 3rd part
/dev/sdb2       1917848077 2462285169  544437093 259.6G 73 unknown
/dev/sdb3       1818575915 2362751050  544175136 259.5G 2b unknown
/dev/sdb4       2844524554 2844579527      54974  26.8M 61 SpeedStor
```
These partition types found on the disk mean nothing to me and a search of the forum and other sites such as AskUbuntu has got me nowhere useful for your problem.

I do hope that any files you have on the disk are available on some other storage device as that may be the best way to ensure they can still be used again!

I don't recall if I transferred the files to alternative storage, I'll need to check but it would be an extensive search.

---

### Post by ajgreeny on 2023-05-30
Sorry but my continued searches have found nothing hopeful and I am still completely baffled though I hope someone else may be able to give you better help than I have so far.

---

### Post by oldfred on 2023-05-30
What you are showing is garbage data in the MBR partition table, that it then is trying to convert to a partition table.
Typical of writing to a drive, not to a partition.

Old floppy drives did not have partitions, but now just about every thing expects to see partitions.
If you know format, you can try manually mounting.

sudo mkdir /media/temp
If ext4
mount -t ext4 /dev/sdb /media/temp

If FAT32
mount -t vfat /dev/sdb /media/temp

---

### Post by wyattwhiteeagle on 2023-05-30
> **oldfred said:**
> What you are showing is garbage data in the MBR partition table, that it then is trying to convert to a partition table.
Typical of writing to a drive, not to a partition.

Old floppy drives did not have partitions, but now just about every thing expects to see partitions.
If you know format, you can try manually mounting.

sudo mkdir /media/temp
If ext4
mount -t ext4 /dev/sdb /media/temp

If FAT32
mount -t vfat /dev/sdb /media/temp

Is there a terminal command to check the format of the flashdrive?

```
sudo fdisk -l
```
At the end of the report, it says...
> Partition table entries are not in disk order.
Could that be part of the problem?

When I look in Partition Manager, it shows /dev/sdb3 as the first partition.

---

### Post by ajgreeny on 2023-05-30
That's interesting oldfred; I had never come across that before.

Does that mean wyattwhiteeagle needs to simply create a new partition table, and then partitions, using gparted, for example, or is there more to it than that? And how can he get to and recover whatever files were on that disk (if they are still there, of course)?

---

### Post by wyattwhiteeagle on 2023-05-30
> **ajgreeny said:**
> That's interesting oldfred; I had never come across that before.

Does that mean wyattwhiteeagle needs to simply create a new partition table, and then partitions, using gparted, for example, or is there more to it than that? And how can he get to and recover whatever files were on that disk (if they are still there, of course)?

Good questions.
I was getting around to asking that but you were on the same train of thought.
Thank you for asking

---

### Post by oldfred on 2023-05-30
If written to the entire drive, you cannot create a partition table now.
The data starts at the MBR, not leaving room for the MBR, the space after the MBR and the PBR - partition boot record.
So no place for partition table structures.

If not worried about data recovery, you need to dd the first sector to clear the MBR of the garbage data, so partition tools can create partition(s). 

Do not know of photorec will then work. It may not need to see partition(s) as it scans a drive.
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec) & 
[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)

Photorec is slow, has to have another drive at least as large as data to be recovered and does not recovery full file names, just extensions.

---

### Post by wyattwhiteeagle on 2023-05-31
If I must accept the loss, I can use Windows reformat and KDE Partition Manager until it's usable again.

A bit of info...

All the other flashdrive's can still be used, why hit only this one flashdrive?
That's the main thing that don't make sense.

The flashdrive still works on a windows system.
Apparently, Windows and Linux uses two seperate partitions on that flashdrive.

The partition read by Windows shows only one file.

Before this happened, I had put at least 7 files onto the flashdrive.
Then I plugged it into a windows system to make sure the files saved to the flashdrive...the files were there...but they're gone now.
That's another thing that don't make sense.

The files included the one file that Windows can still see.
I then began the fresh clean Lubuntu install on my system.

After update && full-upgrade, I plugged the flashdrive into the Lubuntu system and got the error message I mentioned in the first post.

The only thing I've knowingly done since the error message is see if the drive is still usable on the Windows system.

The only way anything would've been written to the drive is if the system writes to the drive when it is plugged in.

The files I put on the drive were important custom *.sh script's, text files compiling info important to me, Web-browser bookmarks and passwords, and maybe a few photos and *.zip files.

My most concern about which files I'm trying to get back are the Scripts and text files.
Took me a long time to get those scripts put together and working properly.
The text files are weeks of useful info for me and her to utilize in the near future.
It just took me a long time to get those put together.
I'm not worried about the other files as they are on another flashdrive fully readable by both systems.

---

### Post by MAFoElffen on 2023-05-31
> **wyattwhiteeagle said:**
> I ran it...
```
sudo mount -t ext4 /dev/sdb1 /media/wyatt/New-Volume
```
Here's what I got...
```
mount: /media/wyatt/New-Volume: mount point does not exist.
```

What that returned error said was that you tried to mount the first partition of device sda to an existing mountpoint of /media/wyatt/New-Volume, (like you asked) but that there was no folder under /media/wyatt/ called "New_Volume". That had no bearing that it couldn't read the filesystem on that flash drive. It hadn't gotten that far yet.

Let's back up a step. Your command assumed that the path an dfloder existed. Did you create a folder under /media/wyatt/ named "New_Volume" manually?

By default, removable media will automount to the /media/$USER/ directory and create a folder under that named after the device. You are doing that manually, so you would have to create a folder manually. You understand the logic of that right? 

Once you get the format of that 'fixed' logically, lets do this
```

sudo lsblk -o name,mointpoint.size,fstype,UUID /dev/sdb

```
So you can see the file system type that is recognized within that partition... Your thread title says "Flash Drive", so nothig yet siad what filesystem was on that Flash Drive, which is most often as "FAT32" (or some other type of FAT filesystem), not "ext4", unless you did that specifically.

So feedback from that output, if fat32, 'might' evolve into something like:
```

sudo mkdir /mnt/temp/
sudo dosfsck -w -r -l -a -v -t /dev/sdb1
sudo mount -t fat32 /dev/sdb1 /mnt/temp
sudo chmod -R $USER:$USER /mnt/temp

```

---

### Post by wyattwhiteeagle on 2023-05-31
> **MAFoElffen said:**
> What that returned error said was that you tried to mount the first partition of device sda to an existing mountpoint of /media/wyatt/New-Volume, (like you asked) but that there was no folder under /media/wyatt/ called "New_Volume". That had no bearing that it couldn't read the filesystem on that flash drive. It hadn't gotten that far yet.

Let's back up a step. Your command assumed that the path an dfloder existed. Did you create a folder under /media/wyatt/ named "New_Volume" manually?

By default, removable media will automount to the /media/$USER/ directory and create a folder under that named after the device. You are doing that manually, so you would have to create a folder manually. You understand the logic of that right? 

Once you get the format of that 'fixed' logically, lets do this
```

sudo lsblk -o name,mointpoint.size,fstype,UUID /dev/sdb

```
So you can see the file system type that is recognized within that partition... Your thread title says "Flash Drive", so nothig yet siad what filesystem was on that Flash Drive, which is most often as "FAT32" (or some other type of FAT filesystem), not "ext4", unless you did that specifically.

So feedback from that output, if fat32, 'might' evolve into something like:
```

sudo mkdir /mnt/temp/
sudo dosfsck -w -r -l -a -v -t /dev/sdb1
sudo mount -t fat32 /dev/sdb1 /mnt/temp
sudo chmod -R $USER:$USER /mnt/temp

```
I didn't create "New_Volume" manually.
That's the name of the flashdrive.

I understand the logic you mention.

Reading what you typed, it's thought provoking.
It seems I've missed specific details about one or more commands I've ran so far.

I'm gonna re-run the info gathering commands and move forward.

I believe all of us are missing bits of info about the flashdrive.

---

### Post by MAFoElffen on 2023-05-31
+1 -- 
*** You are doing a data rescue, which will try to change things. If you  value that data, then first do a dd copy of the disk, to a file, so you  have a backup to fall back on. (Before starting anything on it)

I dug deeper, into reading through all the output in your posts here, and found this tidbit pointing out what we were missing:
[quote="wyattwhiteeagle"]
```

Model: SanDisk Cruzer Glide (scsi)
Disk /dev/sdb: 63.5GB
Sector size (logical/physical): 512B/512B
Partition Table: loop
Disk Flags: 


Number  Start  End     Size    File system  Flags
 1      0.00B  63.5GB  63.5GB  [COLOR=#ff0000]ntfs[/COLOR]

```
[/quote]
The filesystem type there is "ntfs", instead of the default fat32, or the assumed ext4. So...

What I would do based on that output...
It is an NTFS filesystem. Linux does not have tools to repair an NTFS filessytem installed as a default, so install them:
```

sudo apt install ntfs-3g
sudo ntfsfix /dev/sdb1

```
Then the commands to mount it manually would evolve to:
```

sudo mkdir /mnt/temp/
sudo mount -t ntfs /dev/sdb1 /mnt/temp
sudo chmod -R $USER:$USER /mnt/temp

```
*** The one troubling other thing to note in that specific output that I quoted... Look at the Partition Table type that is found there in those fdisk results(?). On a SanDisk Flash Drive, the default partition table type is 'msdos'. It has it as 'loop'. See that? It may fail on just that, as an invalid partition table type.

So, if doing these things, if you can access the data, then copy off all that you can to rescue the data. Then after that-- then reformat the Flash Drive, starting  with a new partition table and partition.

---

### Post by yancek on 2023-05-31
> Error mounting /dev/sdb at /media/wyatt/New Volume:

The above is the error you reported in your initial post.  I suggested you mount it manually and change New Volume to "New_Volume" as spaces in a terminal command will return an error.  You would have to create the directory "New_Volume" under /media/wyatt before running the command which you did not do as seen by subsequent posts.  As oldfred posted earlier and is seen by your output from parted, there are problems with the filesystem on the flash drive which is ntfs.  I doubt ntfs-fix will do much to repair as it is very limited.  If you are using windows filesystems, you should try to repair it with windows.

---

### Post by MAFoElffen on 2023-05-31
> **yancek said:**
> The above is the error you reported in your initial post.  I suggested you mount it manually and change New Volume to "New_Volume" as spaces in a terminal command will return an error.  You would have to create the directory "New_Volume" under /media/wyatt before running the command which you did not do as seen by subsequent posts.  As oldfred posted earlier and is seen by your output from parted, there are problems with the filesystem on the flash drive which is ntfs.  I doubt ntfs-fix will do much to repair as it is very limited.  If you are using windows filesystems, you should try to repair it with windows.
True. Nice catch on the filename having a space in it... And Windows does a better job at fixing their native NTFS filesystems.

There are two ways around the space there by writing them out as:
```

/media/wyatt/"New Volume"
/media/wyatt/New%20Volume

```
But notice the tidbit I noticed at the last minute in the edit of my last post (on invalid partition table type.) Windows may not recognize the Flash Drive because of that...

---

### Post by wyattwhiteeagle on 2023-05-31
Considering the current state of the flashdrive, the ntfs, msdos, and loop...
should running these new commands fail...

Will it render the files I aim to recover as unreadable or unusable?

How would I do a dd copy of everything to a file before starting anything?

---

### Post by #&amp;thj^% on 2023-05-31
> **wyattwhiteeagle said:**
> 

How would I do a dd copy of everything to a file before starting anything?
Everything you need for info here: [https://www.baeldung.com/linux/dd-command](https://www.baeldung.com/linux/dd-command)
take your time, stop and ask first if your unclear.... dd has a nick-name Disk Destroyer, (use with caution)

---

### Post by wyattwhiteeagle on 2023-05-31
Is there a way to do all this as a simulation...a "Dry-Run"?

---

### Post by #&amp;thj^% on 2023-05-31
> **wyattwhiteeagle said:**
> Is there a way to do all this as a simulation...a "Dry-Run"?
Not that I'm aware of, but rsync can help there:
Also please check your systems case use with:
```
info dd
```
Your may have differences than what I show from Arch:
```
File: coreutils.info,  Node: dd invocation,  Next: install invocation,  Prev: cp invocation,  Up: Basic operations

11.2 ‘dd’: Convert and copy a file
==================================

‘dd’ copies input to output with a changeable I/O block size, while
optionally performing conversions on the data.  Synopses:

     dd [OPERAND]...
     dd OPTION

   The only options are ‘--help’ and ‘--version’.  *Note Common
options::.

   By default, ‘dd’ copies standard input to standard output.  To copy,
‘dd’ repeatedly does the following steps in order:

  1. Read an input block.

  2. If converting via ‘sync’, pad as needed to meet the input block
     size.  Pad with spaces if converting via ‘block’ or ‘unblock’, NUL
     bytes otherwise.

  3. If ‘bs=’ is given and no conversion mentioned in steps (4) or (5)
     is given, output the data as a single block and skip all remaining
     steps.

  4. If the ‘swab’ conversion is given, swap each pair of input bytes.
     If the input data length is odd, preserve the last input byte
     (since there is nothing to swap it with).

  5. If any of the conversions ‘swab’, ‘block’, ‘unblock’, ‘lcase’,
     ‘ucase’, ‘ascii’, ‘ebcdic’ and ‘ibm’ are given, do these
     conversions.  These conversions operate independently of input
     blocking, and might deal with records that span block boundaries.

  6. Aggregate the resulting data into output blocks of the specified
     size, and output each output block in turn.  Do not pad the last
     output block; it can be shorter than usual.

   ‘dd’ accepts the following operands, whose syntax was inspired by the
DD (data definition) statement of OS/360 JCL.

‘if=FILE’
     Read from FILE instead of standard input.

‘of=FILE’
     Write to FILE instead of standard output.  Unless ‘conv=notrunc’ is
     given, truncate FILE before writing it.

‘ibs=BYTES’
     Set the input block size to BYTES.  This makes ‘dd’ read BYTES per
     block.  The default is 512 bytes.

‘obs=BYTES’
     Set the output block size to BYTES.  This makes ‘dd’ write BYTES
     per block.  The default is 512 bytes.

‘bs=BYTES’
     Set both input and output block sizes to BYTES.  This makes ‘dd’
     read and write BYTES per block, overriding any ‘ibs’ and ‘obs’
     settings.  In addition, if no data-transforming ‘conv’ operand is
     specified, input is copied to the output as soon as it’s read, even
     if it is smaller than the block size.

‘cbs=BYTES’
     Set the conversion block size to BYTES.  When converting
     variable-length records to fixed-length ones (‘conv=block’) or the
     reverse (‘conv=unblock’), use BYTES as the fixed record length.

‘skip=N’
‘iseek=N’
     Skip N ‘ibs’-byte blocks in the input file before copying.  If N
     ends in the letter ‘B’, interpret N as a byte count rather than a
     block count.  (‘B’ and the ‘iseek=’ spelling are GNU extensions to
     POSIX.)

‘seek=N’
‘oseek=N’
     Skip N ‘obs’-byte blocks in the output file before truncating or
     copying.  If N ends in the letter ‘B’, interpret N as a byte count
     rather than a block count.  (‘B’ and the ‘oseek=’ spelling are GNU
     extensions to POSIX.)

‘count=N’
     Copy N ‘ibs’-byte blocks from the input file, instead of everything
     until the end of the file.  If N ends in the letter ‘B’, interpret
     N as a byte count rather than a block count; this is a GNU
     extension to POSIX. If short reads occur, as could be the case when
     reading from a pipe for example, ‘iflag=fullblock’ ensures that
     ‘count=’ counts complete input blocks rather than input read
     operations.  As an extension to POSIX, ‘count=0’ copies zero blocks
     instead of copying all blocks.

‘status=LEVEL’
     Specify the amount of information printed.  If this operand is
     given multiple times, the last one takes precedence.  The LEVEL
     value can be one of the following:

     ‘none’
          Do not print any informational or warning messages to standard
          error.  Error messages are output as normal.

     ‘noxfer’
          Do not print the final transfer rate and volume statistics
          that normally make up the last status line.

     ‘progress’
          Print the transfer rate and volume statistics on standard
          error, when processing each input block.  Statistics are
          output on a single line at most once every second, but updates
          can be delayed when waiting on I/O.

     Transfer information is normally output to standard error upon
     receipt of the ‘INFO’ signal or when ‘dd’ exits, and defaults to
     the following form in the C locale:

          7287+1 records in
          116608+0 records out
          59703296 bytes (60 MB, 57 MiB) copied, 0.0427974 s, 1.4 GB/s

     The notation ‘W+P’ stands for W whole blocks and P partial blocks.
     A partial block occurs when a read or write operation succeeds but
     transfers less data than the block size.  An additional line like
     ‘1 truncated record’ or ‘10 truncated records’ is output after the
     ‘records out’ line if ‘conv=block’ processing truncated one or more
     input records.

     The ‘status=’ operand is a GNU extension to POSIX.

‘conv=CONVERSION[,CONVERSION]...’
     Convert the file as specified by the CONVERSION argument(s).  (No
     spaces around any comma(s).)

     Conversions:

     ‘ascii’
          Convert EBCDIC to ASCII, using the conversion table specified
          by POSIX.  This provides a 1:1 translation for all 256 bytes.
          This implies ‘conv=unblock’; input is converted to ASCII
          before trailing spaces are deleted.

     ‘ebcdic’
          Convert ASCII to EBCDIC.  This is the inverse of the ‘ascii’
          conversion.  This implies ‘conv=block’; trailing spaces are
          added before being converted to EBCDIC.

     ‘ibm’
          This acts like ‘conv=ebcdic’, except it uses the alternate
          conversion table specified by POSIX.  This is not a 1:1
          translation, but reflects common historical practice for ‘~’,
          ‘[’, and ‘]’.

          The ‘ascii’, ‘ebcdic’, and ‘ibm’ conversions are mutually
          exclusive.  If you use any of these conversions, you should
          also use the ‘cbs=’ operand.

     ‘block’
          For each line in the input, output ‘cbs’ bytes, replacing the
          input newline with a space and truncating or padding input
          lines with spaces as necessary.

     ‘unblock’
          Remove any trailing spaces in each ‘cbs’-sized input block,
          and append a newline.

          The ‘block’ and ‘unblock’ conversions are mutually exclusive.
          If you use either of these conversions, you should also use
          the ‘cbs=’ operand.

     ‘lcase’
          Change uppercase letters to lowercase.

     ‘ucase’
          Change lowercase letters to uppercase.

          The ‘lcase’ and ‘ucase’ conversions are mutually exclusive.

     ‘sparse’
          Try to seek rather than write NUL output blocks.  On a file
          system that supports sparse files, this will create sparse
          output when extending the output file.  Be careful when using
          this conversion in conjunction with ‘conv=notrunc’ or
          ‘oflag=append’.  With ‘conv=notrunc’, existing data in the
          output file corresponding to NUL blocks from the input, will
          be untouched.  With ‘oflag=append’ the seeks performed will be
          ineffective.  Similarly, when the output is a device rather
          than a file, NUL input blocks are not copied, and therefore
          this conversion is most useful with virtual or pre zeroed
          devices.

          The ‘sparse’ conversion is a GNU extension to POSIX.

     ‘swab’
          Swap every pair of input bytes.

     ‘sync’
          Pad every input block to size of ‘ibs’ with trailing zero
          bytes.  When used with ‘block’ or ‘unblock’, pad with spaces
          instead of zero bytes.

     The following “conversions” are really file flags and don’t affect
     internal processing:

     ‘excl’
          Fail if the output file already exists; ‘dd’ must create the
          output file itself.

     ‘nocreat’
          Do not create the output file; the output file must already
          exist.

          The ‘excl’ and ‘nocreat’ conversions are mutually exclusive,
          and are GNU extensions to POSIX.

     ‘notrunc’
          Do not truncate the output file.

     ‘noerror’
          Continue after read errors.

     ‘fdatasync’
          Synchronize output data just before finishing, even if there
          were write errors.  This forces a physical write of output
          data, so that even if power is lost the output data will be
          preserved.  If neither this nor ‘fsync’ are specified, output
          is treated as usual with file systems, i.e., output data and
          metadata may be cached in primary memory for some time before
          the operating system physically writes it, and thus output
          data and metadata may be lost if power is lost.  *Note sync
          invocation::.  This conversion is a GNU extension to POSIX.

     ‘fsync’
          Synchronize output data and metadata just before finishing,
          even if there were write errors.  This acts like ‘fdatasync’
          except it also preserves output metadata, such as the
          last-modified time of the output file; for this reason it may
          be a bit slower than ‘fdatasync’ although the performance
          difference is typically insignificant for ‘dd’.  This
          conversion is a GNU extension to POSIX.

‘iflag=FLAG[,FLAG]...’
     Access the input file using the flags specified by the FLAG
     argument(s).  (No spaces around any comma(s).)

‘oflag=FLAG[,FLAG]...’
     Access the output file using the flags specified by the FLAG
     argument(s).  (No spaces around any comma(s).)

     Here are the flags.

     ‘append’
          Write in append mode, so that even if some other process is
          writing to this file, every ‘dd’ write will append to the
          current contents of the file.  This flag makes sense only for
          output.  If you combine this flag with the ‘of=FILE’ operand,
          you should also specify ‘conv=notrunc’ unless you want the
          output file to be truncated before being appended to.

     ‘cio’
          Use concurrent I/O mode for data.  This mode performs direct
          I/O and drops the POSIX requirement to serialize all I/O to
          the same file.  A file cannot be opened in CIO mode and with a
          standard open at the same time.

     ‘direct’
          Use direct I/O for data, avoiding the buffer cache.  Note that
          the kernel may impose restrictions on read or write buffer
          sizes.  For example, with an ext4 destination file system and
          a Linux-based kernel, using ‘oflag=direct’ will cause writes
          to fail with ‘EINVAL’ if the output buffer size is not a
          multiple of 512.

     ‘directory’

          Fail unless the file is a directory.  Most operating systems
          do not allow I/O to a directory, so this flag has limited
          utility.

     ‘dsync’
          Use synchronized I/O for data.  For the output file, this
          forces a physical write of output data on each write.  For the
          input file, this flag can matter when reading from a remote
          file that has been written to synchronously by some other
          process.  Metadata (e.g., last-access and last-modified time)
          is not necessarily synchronized.

     ‘sync’
          Use synchronized I/O for both data and metadata.

     ‘nocache’
          Request to discard the system data cache for a file.  When
          count=0 all cached data for the file is specified, otherwise
          the cache is dropped for the processed portion of the file.
          Also when count=0, failure to discard the cache is diagnosed
          and reflected in the exit status.

          Note data that is not already persisted to storage will not be
          discarded from cache, so note the use of the ‘sync’
          conversions in the examples below, which are used to maximize
          the effectiveness of the ‘nocache’ flag.

          Here are some usage examples:

               # Advise to drop cache for whole file
               dd if=ifile iflag=nocache count=0

               # Ensure drop cache for the whole file
               dd of=ofile oflag=nocache conv=notrunc,fdatasync count=0

               # Advise to drop cache for part of file
               # Note the kernel will only consider complete and
               # already persisted pages.
               dd if=ifile iflag=nocache skip=10 count=10 of=/dev/null

               # Stream data using just the read-ahead cache.
               # See also the ‘direct’ flag.
               dd if=ifile of=ofile iflag=nocache oflag=nocache,sync

     ‘nonblock’
          Use non-blocking I/O.

     ‘noatime’
          Do not update the file’s access timestamp.  *Note File
          timestamps::.  Some older file systems silently ignore this
          flag, so it is a good idea to test it on your files before
          relying on it.

     ‘noctty’
          Do not assign the file to be a controlling terminal for ‘dd’.
          This has no effect when the file is not a terminal.  On many
          hosts (e.g., GNU/Linux hosts), this flag has no effect at all.

     ‘nofollow’
          Do not follow symbolic links.

     ‘nolinks’
          Fail if the file has multiple hard links.

     ‘binary’
          Use binary I/O.  This flag has an effect only on nonstandard
          platforms that distinguish binary from text I/O.

     ‘text’
          Use text I/O.  Like ‘binary’, this flag has no effect on
          standard platforms.

     ‘fullblock’
          Accumulate full blocks from input.  The ‘read’ system call may
          return early if a full block is not available.  When that
          happens, continue calling ‘read’ to fill the remainder of the
          block.  This flag can be used only with ‘iflag’.  This flag is
          useful with pipes for example as they may return short reads.
          In that case, this flag is needed to ensure that a ‘count=’
          argument is interpreted as a block count rather than a count
          of read operations.

     These flags are all GNU extensions to POSIX. They are not supported
     on all systems, and ‘dd’ rejects attempts to use them when they are
     not supported.  When reading from standard input or writing to
     standard output, the ‘nofollow’ and ‘noctty’ flags should not be
     specified, and the other flags (e.g., ‘nonblock’) can affect how
     other processes behave with the affected file descriptors, even
     after ‘dd’ exits.

   The behavior of ‘dd’ is unspecified if operands other than ‘conv=’,
‘iflag=’, ‘oflag=’, and ‘status=’ are specified more than once.

   The numeric-valued strings above (N and BYTES) are unsigned decimal
integers that can be followed by a multiplier: ‘b’=512, ‘c’=1, ‘w’=2,
‘xM’=M, or any of the standard block size suffixes like ‘k’=1024 (*note
Block size::).  These multipliers are GNU extensions to POSIX, except
that POSIX allows BYTES to be followed by ‘k’, ‘b’, and ‘xM’.  Block
sizes (i.e., specified by BYTES strings) must be nonzero.

   Any block size you specify via ‘bs=’, ‘ibs=’, ‘obs=’, ‘cbs=’ should
not be too large – values larger than a few megabytes are generally
wasteful or (as in the gigabyte..exabyte case) downright
counterproductive or error-inducing.

   To process data with offset or size that is not a multiple of the I/O
block size, you can use a numeric string N that ends in the letter ‘B’.
For example, the following shell commands copy data in 1 MiB blocks
between a flash drive and a tape, but do not save or restore a 512-byte
area at the start of the flash drive:

     flash=/dev/sda
     tape=/dev/st0

     # Copy all but the initial 512 bytes from flash to tape.
     dd if=$flash iseek=512B bs=1MiB of=$tape

     # Copy from tape back to flash, leaving initial 512 bytes alone.
     dd if=$tape bs=1MiB of=$flash oseek=512B

   For failing storage devices, other tools come with a great variety of
extra functionality to ease the saving of as much data as possible
before the device finally dies, e.g.  GNU ‘ddrescue’
(https://www.gnu.org/software/ddrescue/).  However, in some cases such a
tool is not available or the administrator feels more comfortable with
the handling of ‘dd’.  As a simple rescue method, call ‘dd’ as shown in
the following example: the operand ‘conv=noerror,sync’ is used to
continue after read errors and to pad out bad reads with NULs, while
‘iflag=fullblock’ caters for short reads (which traditionally never
occur on flash or similar devices):

     # Rescue data from an (unmounted!) partition of a failing device.
     dd conv=noerror,sync iflag=fullblock </dev/sda1 > /mnt/rescue.img

   Sending an ‘INFO’ signal (or ‘USR1’ signal where that is unavailable)
to a running ‘dd’ process makes it print I/O statistics to standard
error and then resume copying.  In the example below, ‘dd’ is run in the
background to copy 5GB of data.  The ‘kill’ command makes it output
intermediate I/O statistics, and when ‘dd’ completes normally or is
killed by the ‘SIGINT’ signal, it outputs the final statistics.

     # Ignore the signal so we never inadvertently terminate the dd child.
     # Note this is not needed when SIGINFO is available.
     trap '' USR1

     # Run dd with the fullblock iflag to avoid short reads
     # which can be triggered by reception of signals.
     dd iflag=fullblock if=/dev/zero of=/dev/null count=5000000 bs=1000 & pid=$!

     # Output stats every second.
     while kill -s USR1 $pid 2>/dev/null; do sleep 1; done

   The above script will output in the following format:

     3441325+0 records in
     3441325+0 records out
     3441325000 bytes (3.4 GB, 3.2 GiB) copied, 1.00036 s, 3.4 GB/s
     5000000+0 records in
     5000000+0 records out
     5000000000 bytes (5.0 GB, 4.7 GiB) copied, 1.44433 s, 3.5 GB/s

   The ‘status=progress’ operand periodically updates the last line of
the transfer statistics above.

   On systems lacking the ‘INFO’ signal ‘dd’ responds to the ‘USR1’
signal instead, unless the ‘POSIXLY_CORRECT’ environment variable is
set.

   An exit status of zero indicates success, and a nonzero value
indicates failure.

```

---

### Post by MAFoElffen on 2023-05-31
I would use either of these commands:
```

sudo dd if=/dev/sdb of=~/Downloads/SanDiskCruiser.img bs=1k conv=sync,noerror
sudo dd if=/dev/sdb conv=sync,noerror bs=1k | gzip -c > ~/Downloads/SanDiskCruiser.gz

```
Change the destination to wherever you wanted to put it...

---

### Post by wyattwhiteeagle on 2023-06-01
Did your suggestion help at all?
If I did it incorrectly, then please guide in the correct way.
Please see below...
> **yancek said:**
> The above is the error you reported in your initial post.  I suggested you mount it manually and change New Volume to "New_Volume" as spaces in a terminal command will return an error.  You would have to create the directory "New_Volume" under /media/wyatt before running the command which you did not do as seen by subsequent posts.  As oldfred posted earlier and is seen by your output from parted, there are problems with the filesystem on the flash drive which is ntfs.  I doubt ntfs-fix will do much to repair as it is very limited.  If you are using windows filesystems, you should try to repair it with windows.

> **yancek said:**
> How did you try to mount it, from a terminal or GUI file manager? Try using the filesystem option. If you have several partitions, use whatever filesystem you have to try to mount as in the example below:


```
sudo mount -t ext4 /dev/sdb1 /media/wyatt/New-Volume
```


Don't use spaces in the directory names.
> KDE Partition Manager - Partition Table Export
```
##|v1|## partition table of /dev/sdb# on Tuesday, 30 May 2023 05:13:14 EDT
type: "msdos"
align: "sector"


# number start end type roles label flags
1;1936269394;3772285809;unknown;primary;"";""
2;1917848077;2462285169;unknown;primary;"";""
3;1818575915;2362751050;unknown;primary;"";""
4;2844524554;2844579527;unknown;primary;"";""
```
The numbers under the '#' are the partition numbers, ie sdb1, sdb2, sdb3, sdb4

I ran...
```
sudo mkdir /media/wyatt/New-Volume
```
Then I attached the flashdrive
Then I ran...
```
sudo mount -t ntfs /dev/sdb1 /media/wyatt/New-Volume
```

The Label Name of the flashdrive is New Volume.
What are the commands to actually change the label name of the flashdrive?
I suspect that would involve reformatting, thus losing the files.

Creating a directory with one name then running a command to mount something with a different name will give an error as well.

Note: I haven't ran any ntfs-3g commands yet

The below says...[COLOR=#000000][I]Failed to access volume '/dev/sdb1': No such file or directory
[/I][/COLOR]The reason it says that is because in /media/wyatt/New-Volume...the newly created directory...there is nothing...no such file or directory "/dev/sdb1"

And terminal says...
> ntfs-3g: Failed to access volume '/dev/sdb1': No such file or directory


ntfs-3g 2021.8.22 integrated FUSE 28 - Third Generation NTFS Driver
                Configuration type 7, XATTRS are on, POSIX ACLS are on


Copyright (C) 2005-2007 Yura Pakhuchiy
Copyright (C) 2006-2009 Szabolcs Szakacsits
Copyright (C) 2007-2021 Jean-Pierre Andre
Copyright (C) 2009-2020 Erik Larsson


Usage:    ntfs-3g [-o option[,...]] <device|image_file> <mount_point>


Options:  ro (read-only mount), windows_names, uid=, gid=,
          umask=, fmask=, dmask=, streams_interface=.
          Please see the details in the manual (type: man ntfs-3g).


Example: ntfs-3g /dev/sda1 /mnt/windows


Plugin path: /usr/lib/x86_64-linux-gnu/ntfs-3g


News, support and information:  [https://github.com/tuxera/ntfs-3g/](https://github.com/tuxera/ntfs-3g/)


---

### Post by MAFoElffen on 2023-06-01
It cannot find the partition...

Have you thought about trying this?: [https://www.cgsecurity.org/wiki/TestDisk](https://www.cgsecurity.org/wiki/TestDisk)

---

### Post by wyattwhiteeagle on 2023-06-01
> **MAFoElffen said:**
> It cannot find the partition...

Have you thought about trying this?: [https://www.cgsecurity.org/wiki/TestDisk](https://www.cgsecurity.org/wiki/TestDisk)
I haven't even tried what you suggested yet.
I want to make sure I don't mess this up for myself

I believe I will try TestDisk later today.
I asked about TestDisk here...but got no response about it
> **wyattwhiteeagle said:**
> Would...testdisk...help my situation?...


And my previous post was a rebuttal to yancek's complaint at me.
In the post, I typed about midways down...> **wyattwhiteeagle said:**
> The Label Name of the flashdrive is New Volume.
What are the commands to actually change the label name of the flashdrive?
I suspect that would involve reformatting, thus losing the files.


Creating a directory with one name then running a command to mount something with a different name will give an error as well.


Note: I haven't ran any ntfs-3g commands yet


The below says...Failed to access volume '/dev/sdb1': No such file or directory
The reason it says that is because in /media/wyatt/New-Volume...the newly created directory...there is nothing...no such file or directory "/dev/sdb1"

---

### Post by yancek on 2023-06-01
If your flash drive shows under:  /media/wyatt/New Volume (with a space between New and Volume) you need to either create a new mount point (New-Volume) and try to mount it there or put quotes around the name such as:  sudo mount /dev/sdb1 /media/wyatt/"New Volume"  Try that.  The drive filesystem is apparently corrupted and since it is an ntfs filesystem is not likely to be repaired by ntfsfix or any other Linux tool but by using windows. 

> no such file or directory "/dev/sdb1 

You won't see /dev/sdb1 even if it is successfully mounted.  /dev/sdb1 is the device upon which the data is stored and the mount point /media/wyatt/New-Volume is the mount point where that data will be accessible.

Test Disk and Photorec are excellent at their job.  Problem is that what is saved will not show the correct file names in the same manner as you created them so it takes a lot of time to figure all this out.  If you decide to try it, I would definitely recommend reading through the documentation before beginning.

>  And my previous post was a rebuttal to yancek's complaint at me.

Not a complain, an explanation.

---

### Post by wyattwhiteeagle on 2023-06-01
> **yancek said:**
> If your flash drive shows under: /media/wyatt/New Volume (with a space between New and Volume) you need to either create a new mount point (New-Volume) and try to mount it there or put quotes around the name such as: sudo mount /dev/sdb1 /media/wyatt/"New Volume" Try that. The drive filesystem is apparently corrupted and since it is an ntfs filesystem is not likely to be repaired by ntfsfix or any other Linux tool but by using windows.

You won't see /dev/sdb1 even if it is successfully mounted. /dev/sdb1 is the device upon which the data is stored and the mount point /media/wyatt/New-Volume is the mount point where that data will be accessible.

Test Disk and Photorec are excellent at their job. Problem is that what is saved will not show the correct file names in the same manner as you created them so it takes a lot of time to figure all this out. If you decide to try it, I would definitely recommend reading through the documentation before beginning.

Thank you, I'll be sure and do that.

> **yancek said:**
> Not a complain, an explanation.
> **yancek said:**
> ...You would have to create the directory "New_Volume" under /media/wyatt before running the command which you did not do [COLOR=#000000] as seen by subsequent posts[/COLOR]...

The part that gave me the impression of being a complain was the "which you did not do as seen by subsequent posts."
Had it said, "which you didn't do" and not mention "subsequent posts", I would've read an explanation in that sentence.

If the above was not a complain, but an explanation...
I apologize, please forgive me.

---

### Post by The Cog on 2023-06-01
Oops, misread post 6. Deleted.

---

### Post by wyattwhiteeagle on 2023-06-03
Well Folks, TestDisk worked awesome.

*Spoiler Hint* - Not the desired results.

When I first ran TestDisk, I...
...Scanned for all partitions
...Copied all files on each partition to the Destination folder.
...Checked each recovered file

None of the files recovered were my files.

I haven't yet deleted any of the files that TestDisk recovered.

Should I keep trying or should I accept the loss, reformat and start putting the info together again and storing them to a storage alternative...Not only on a flashdrive?

---

### Post by dragonfly41 on 2023-06-03
Now you might try photorec .. companion to testdisk .. but study advice from OldFred and others on difficulty in getting Humpty Dumpty together again using photorec. File names and paths are lost so very intensive detective work is required on contents of files. I posted somewhere some days ago ideas on scanning for keywords (concordance tools and ripgrep) within corpus of recoveed files.Needless to point out ... save recovered files in another device. Keep the TestDisk recovered files.

---

### Post by oldfred on 2023-06-03
If testdisk did not give you the expected files, what did it give you?
Did at some point you overwrite drive or even wrong drive.
I have a lot of similar flash drives and have to keep a list of which is which and have labels on them.

---

### Post by wyattwhiteeagle on 2023-06-03
> **oldfred said:**
> If testdisk did not give you the expected files, what did it give you?
Did at some point you overwrite drive or even wrong drive.
I have a lot of similar flash drives and have to keep a list of which is which and have labels on them.

> **dragonfly41 said:**
> Now you might try photorec .. companion to testdisk .. but study advice from OldFred and others on difficulty in getting Humpty Dumpty together again using photorec. File names and paths are lost so very intensive detective work is required on contents of files. I posted somewhere some days ago ideas on scanning for keywords (concordance tools and ripgrep) within corpus of recoveed files.Needless to point out ... save recovered files in another device. Keep the TestDisk recovered files.

These are the files TestDisk recovered for me...

```
/home/wyatt/Desktop/Files-Recovered/New-IL-Route.txt
```
This file is copied in 2 other locations.
Recovering isn't actually needed.

```
/home/wyatt/Desktop/Files-Recovered/testdisk.log
```
TestDisk log file

```
/home/wyatt/Desktop/Files-Recovered/EFI/BOOT/BOOTX64.EFI
/home/wyatt/Desktop/Files-Recovered/EFI/BOOT/GRUBX64.EFI
/home/wyatt/Desktop/Files-Recovered/EFI/BOOT/MMX64.EFI
```
These files were recovered from the boot partition of the flashdrive.

The lost files were put onto the flashdrive 10 or 15 minutes and checked on a Windows machine before doing the fresh clean Lubuntu install.
There is no way I knowingly over-wrote or deleted the files.

It seems like the new Lubuntu install deleted the files before giving me the error.

---

### Post by dragonfly41 on 2023-06-04
Is it possible that you had your files previously installed in your device then installed Lubunto over these?
Installing Lubuntu erases all previous files held in the device unless you pre-partitioned the device using gparted on Live USB then later applying option "use something else" in LiveUSB where you install into prepared partitions at front end of device.
It is safer to have backups in separate n+1 media. Search "principles of n+1 redundancy" for the future.

---

### Post by wyattwhiteeagle on 2023-06-04
> **dragonfly41 said:**
> Is it possible that you had your files previously installed in your device then installed Lubunto over these?
Installing Lubuntu erases all previous files held in the device unless you pre-partitioned the device using gparted on Live USB then later applying option "use something else" in LiveUSB where you install into prepared partitions at front end of device.
It is safer to have backups in separate n+1 media. Search "principles of n+1 redundancy" for the future.
Nope, It isn't possible.
I put the files on the flashdrive, then checked the flashdrive on a Windows machine to make sure they were there, then started the new install process.
The flashdrive which contained those files was clear across the room while i used the LiveUSB to install normal on the internal HDD.

In fact, the one file that I specified there were copies in 2 other places...that file was there before I put the other files there with that file.
```
sudo gdisk -l /dev/sdb
```


Could this be why my files disappeared?
Why is the LiveUSB setting things to where recent things seems like they are being reversed?
Yet again, why this flashdrive only and not my other flashdrives as well?
Is there something within the LiveUSB specifying a day or hour limit?


What caught my attention in the output is...
```
Partition table scan:
  MBR: MBR only
  BSD: not present
  APM: not present
  GPT: not present
```
```
***************************************************************
Found invalid GPT and valid MBR; converting MBR to GPT format
in memory. 
***************************************************************
```
```
Warning! Secondary partition table overlaps the last partition by
3648226195 blocks!
You will need to delete this partition or resize it in another utility.
```


> GPT fdisk (gdisk) version 1.0.8


Partition table scan:
  MBR: MBR only
  BSD: not present
  APM: not present
  GPT: not present




***************************************************************
Found invalid GPT and valid MBR; converting MBR to GPT format
in memory. 
***************************************************************


Exact type match not found for type code 4F00; assigning type code for
'Linux filesystem'
Exact type match not found for type code 7300; assigning type code for
'Linux filesystem'
Exact type match not found for type code 2B00; assigning type code for
'Linux filesystem'
Exact type match not found for type code 6100; assigning type code for
'Linux filesystem'


Warning! Secondary partition table overlaps the last partition by
3648226195 blocks!
You will need to delete this partition or resize it in another utility.
Disk /dev/sdb: 124059648 sectors, 59.2 GiB
Model: Cruzer Glide    
Sector size (logical/physical): 512/512 bytes
Disk identifier (GUID): FB7F8A1F-B608-4857-9292-125CAD522E4C
Partition table holds up to 128 entries
Main partition table begins at sector 2 and ends at sector 33
First usable sector is 34, last usable sector is 124059614
Partitions will be aligned on 1-sector boundaries
Total free space is 124059581 sectors (59.2 GiB)


Number  Start (sector)    End (sector)  Size       Code  Name
   1      1936269394      3772285809   875.5 GiB   8300  Linux filesystem
   2      1917848077      2462285169   259.6 GiB   8300  Linux filesystem
   3      1818575915      2362751050   259.5 GiB   8300  Linux filesystem
   4      2844524554      2844579527   26.8 MiB    8300  Linux filesystem

---

### Post by wyattwhiteeagle on 2023-06-04
Could the info in my previous post be possible?
> **wyattwhiteeagle said:**
> ...

---

### Post by oldfred on 2023-06-04
Gdisk is giving similar results as you very first post. Or a totally corrupted partition table that partition tools are trying to use, but then partitions make no sense.

Or you wrote data into MBR partition table area.

---

### Post by wyattwhiteeagle on 2023-06-04
Well folks,

Photorec worked phenomenally.
It recovered every file that's ever been on the flashdrive.
Including the files I lost.

What should I do next with these files?
Go through deleting the files I don't need, or what?

---

### Post by wyattwhiteeagle on 2023-06-04
What are '*.elf' object code type files?
I've never seen these files before.

---

### Post by oldfred on 2023-06-04
I had to look up what .efi files are:
>  ELF is the *abbreviation for Executable and Linkable Format* and defines the structure for binaries, libraries, and core files. 

If recovered files are photos you can easily bulk rename them.
If you saved any files more than once, you have multiple copies and have to compare to see if you can tell which is newest. I had saved some text files many times and had to sort to find a file, then compare all the same versions of that file with an old backup. Long process. I now by default include the filename as a # comment as first line of any text file I create. My python & scripts also have file names. 

Some links show old python2 scripts. They would have to be updated to python3.
Use scripts to help sort and rename files:
[http://www.cgsecurity.org/wiki/After_Using_PhotoRec](http://www.cgsecurity.org/wiki/After_Using_PhotoRec)
use flac tags to rename files 
[http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html](http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html)
Best GUI Indexing/Search Tool for Local text type Files? 
[http://ubuntuforums.org/showthread.php?t=1739701](http://ubuntuforums.org/showthread.php?t=1739701)

---

### Post by wyattwhiteeagle on 2023-06-04
> **oldfred said:**
> I had to look up what .efi files are:


If recovered files are photos you can easily bulk rename them.
If you saved any files more than once, you have multiple copies and have to compare to see if you can tell which is newest. I had saved some text files many times and had to sort to find a file, then compare all the same versions of that file with an old backup. Long process. I now by default include the filename as a # comment as first line of any text file I create. My python & scripts also have file names. 

Some links show old python2 scripts. They would have to be updated to python3.
Use scripts to help sort and rename files:
[http://www.cgsecurity.org/wiki/After_Using_PhotoRec](http://www.cgsecurity.org/wiki/After_Using_PhotoRec)
use flac tags to rename files 
[http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html](http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html)
Best GUI Indexing/Search Tool for Local text type Files? 
[http://ubuntuforums.org/showthread.php?t=1739701](http://ubuntuforums.org/showthread.php?t=1739701)
Thank you, I'll look into that in the near future. However...

When I ran photorec, I told it to recover the files to the Desktop, but it defaulted to recovering to the /home/$user directory creating subdirectories assigning root permissions.
I've already moved some of the files to a folder on the desktop, but that left some of the "recup_dir" folders empty.
The name of these folders are "recup_dir.21" and "recup_dir.31", etc.
These folders have root permissions.

How may I use rmdir specifying these "recup_dir.*" to remove only those which are empty?

---

### Post by oldfred on 2023-06-05
When I ran photorec, I copied everything to another drive.
Do not remember permissions issue, but if in your /home you should change to you as owner & give yourself permissions.
Sometimes I use sudo when I should not and a file is created in /home with / or I download something.
So I may run these. I think now my default is the old settings for /home as now they are a bit more restrictive.
Ubuntu Home directories were created with 755 permissions but will be dropped to 750 with 21.04,  now to prevent new home directories from being readable by other users on the system. 

Do not run any of these on / or any / folder, just /home or a data only partition.
sudo chown -R $USER:$USER /home/$USER
sudo chmod -R a+rwX,o-w /home/$USER
-R is recursive, so all directories also changed. If run on root, only recourse is new install & restore from backup.

---

### Post by wyattwhiteeagle on 2023-06-25
Is there anything I'm missing here...

Currently, I'm having to manually rename files and delete duplicates from the recovered data.

Sometime in the near future, I plan to perform a test on a flash drive to see if it is the new install's that is doing this to my flashdrives or if it is something I'm doing or not doing.

Following the guidance in the quoted post gives me a starting point.

My test steps...
(After backing up all files, of course)
```
1. Format a flash drive to NTFS filesystem
2. Create a test file and put it on the newly formatted flash drive.
3. Do a new fresh clean install of Lubuntu.
4. Attach the newly formatted flash drive and see if it's still readable without TestDisk or Photorec.
```

[https://ubuntuforums.org/showthread.php?t=2487305&p=14145211#post14145211](https://ubuntuforums.org/showthread.php?t=2487305&p=14145211#post14145211)
> **sudodus said:**
> ...NTFS is a good alternative for files that must be available from Linux and Windows...

---

### Post by oldfred on 2023-06-25
If using NTFS, you cannot chmod nor chown files.
The only setting is the defaults you set with the mount command or fstab.

And if Windows fast start up is on, you will lose data. Fast startup sets hibernation flag. Normally Ubuntu should not write into a hibernated partition and Windows will just restore the hibernated file to the way it was when put into hibernation.
Windows turns fast startup back on with many updates, you if issues, you often have to boot Windows and turn it off again.

---

### Post by wyattwhiteeagle on 2023-06-26
I want at least one flashdrive readable in both Windows and Linux.
This is to be for any file that either Windows or Linux can read. Not dual booting though.
I'm using Lubuntu and my fiance is using Windows.
We have separate laptops.
Some files we wish to share with each other.

So maybe FAT32 instead of NTFS?

Your most recent post seems to suggest that the underlying issue may be in fstab or the mount command.

Am I understanding correctly?

---

### Post by oldfred on 2023-06-26
Usually the default settings with the automount of a flash drive work.
But Windows must have fast start up off, or the hibernation flag is set and then default mounts will not work.

Best not to use FAT32 unless small drive. You cannot store files over 4GB on FAT32 and FAT32 does not have a journal, so repairs are more difficult or impossible. Suggest NTFS.

---

### Post by wyattwhiteeagle on 2023-06-30
> **oldfred said:**
> I now by default include the filename as a # comment as first line of any text file I create. My python & scripts also have file names.
Some links show old python2 scripts. They would have to be updated to python3.

How would I do exactly just those?

---

### Post by oldfred on 2023-06-30
Just those? Text files? Or all files. 
And it has to be done before you lose files, so you can find file name in file if recovered with photorec.

I make first line:
# filename.txt

It was at least 6 years ago I wrote a little script to loop thru all .txt files in /home and use sed to insert a line. But I really do not understand sed and now cannot understand old script.

---

### Post by MAFoElffen on 2023-07-01
@olfred ---

Piping  "ls" output through xargs to use the command 'sed' to add a line where?

You can use sed's command "i" to insert a line before the match or pointer... and command "a" to add a line after the match or pointer...

Examples as a command:
```

# Insert line before line #1
ls 'full/path/to/*.txt | xargs -i sh -c 'filename="{}"; sed -i "1 i\ ${filename}" "$filename" '
[s]# Append line after line #3
ls /full/path/to/*.txt | xargs sed '3 a\  ' {};[/s]
# Append line at end of file
ls /full/path/to/*.txt | xargs -i sh -c 'filename="{}"; echo "$filename" >> "$filename" '

```
*** Tested. Now works.


Or in Bash:
```

#!/bin/bash

target=$(/media/$USER/usb_drive_label) # /path/to <-- this could be changed to the path the folder where he copied the files to
filelist=$(ls $target/*.txt)  # use path/to var along with file pattern match

for file in ${filelist} # set a filename from the listed files to a var
do
    sed '1 i\ ${file} ' $target/$file  # Use 'sed' to insert a line at the start of each file.
done

```

Is that what you are looking to do, or a variant thereof? LOL

Which would you like to do? Just assisting. 

If you posted your script, I could translate your script for you with comments added to it saying what each line does... Would that help?

---

### Post by wyattwhiteeagle on 2023-07-01
What oldfred mentions seems to be very wise.

Those Python2 scripts...I can't make heads or tails of them at all
They need to be updated

I'm just now getting a good idea of a minor scratch into understanding bash and bash scripting
I still have a lot to learn though

For me, Bash is a lot easier to understand than Python
I'm just a tad bit past the point where bash begins to introduce Perl

I've been needing to put something within my files so they are easily found and such should I lose those files.

I need to do this with all my files (at least those files which I can do this with)

I also would like to add in a progress line command with verbosity.
I would like for any problems (such like 'file already exist' and 'cannot overwrite already created' etc) encountered during the commands being ran to be exported to a *.txt file on the Desktop
Also would like a command line at the end to have terminal tell me when the commands are all performed and completed.

 I can post my "sort-recovered-files.sh" script and hopefully ya'll can help with adding and/or editing what I'm missing.
Busy weekend...here's the script though...(probably wouldn't hurt for me to tidy it up a bit, lol)

```
#!/bin/bash

# Change Permissions
# chmod a+x /home/wyatt/Desktop/Sort-Recovered-Files.sh

# Run The Script
# /home/wyatt/Desktop/Sort-Recovered-Files.sh

mkdir /home/wyatt/Desktop/recup_dir/Image
mkdir /home/wyatt/Desktop/recup_dir/Image/PNG
mkdir /home/wyatt/Desktop/recup_dir/Image/JPG
mkdir /home/wyatt/Desktop/recup_dir/Image/BMP
mkdir /home/wyatt/Desktop/recup_dir/Image/GIF
find /home/wyatt/Desktop/recup_dir/* -type f -name "*.png" -print0 | xargs -0 mv -t /home/wyatt/Desktop/recup_dir/Image/PNG
find /home/wyatt/Desktop/recup_dir/* -type f -name "*.jpg" -print0 | xargs -0 mv -t /home/wyatt/Desktop/recup_dir/Image/JPG
find /home/wyatt/Desktop/recup_dir/* -type f -name "*.JPG" -print0 | xargs -0 mv -t /home/wyatt/Desktop/recup_dir/Image/JPG
find /home/wyatt/Desktop/recup_dir/* -type f -name "*.jpeg" -print0 | xargs -0 mv -t /home/wyatt/Desktop/recup_dir/Image/JPG
find /home/wyatt/Desktop/recup_dir/* -type f -name "*.JPEG" -print0 | xargs -0 mv -t /home/wyatt/Desktop/recup_dir/Image/JPG
find /home/wyatt/Desktop/recup_dir/* -type f -name "*.bmp" -print0 | xargs -0 mv -t /home/wyatt/Desktop/recup_dir/Image/BMP
find /home/wyatt/Desktop/recup_dir/* -type f -name "*.gif" -print0 | xargs -0 mv -t /home/wyatt/Desktop/recup_dir/Image/GIF

mkdir /home/wyatt/Desktop/recup_dir/Text
find /home/wyatt/Desktop/recup_dir/* -type f -name "*.txt" -print0 | xargs -0 mv -t /home/wyatt/Desktop/recup_dir/Text
find /home/wyatt/Desktop/recup_dir/* -type f -name "*.TXT" -print0 | xargs -0 mv -t /home/wyatt/Desktop/recup_dir/Text

mkdir /home/wyatt/Desktop/recup_dir/Document
find /home/wyatt/Desktop/recup_dir/* -type f -name "*.doc" -print0 | xargs -0 mv -t /home/wyatt/Desktop/recup_dir/Document

mkdir /home/wyatt/Desktop/recup_dir/Application
find /home/wyatt/Desktop/recup_dir/* -type f -name "*.exe" -print0 | xargs -0 mv -t /home/wyatt/Desktop/recup_dir/Application

mkdir /home/wyatt/Desktop/recup_dir/Wyatts-Scripts
find /home/wyatt/Desktop/recup_dir/* -type f -name "*.sh" -print0 | xargs -0 mv -t /home/wyatt/Desktop/recup_dir/Wyatts-Scripts

mkdir /home/wyatt/Desktop/recup_dir/Compressed
find /home/wyatt/Desktop/recup_dir/* -type f -name "*.zip" -print0 | xargs -0 mv -t /home/wyatt/Desktop/recup_dir/Compressed

mkdir /home/wyatt/Desktop/recup_dir/Unspecified
mkdir /home/wyatt/Desktop/recup_dir/Unspecified/ISO
mkdir /home/wyatt/Desktop/recup_dir/Unspecified/PDF
find /home/wyatt/Desktop/recup_dir/* -type f -name "*.iso" -print0 | xargs -0 mv -t /home/wyatt/Desktop/recup_dir/Unspecified/ISO
find /home/wyatt/Desktop/recup_dir/* -type f -name "*.pdf" -print0 | xargs -0 mv -t /home/wyatt/Desktop/recup_dir/Unspecified/PDF

mkdir /home/wyatt/Desktop/recup_dir/Bkmrks-Pswrds
find /home/wyatt/Desktop/recup_dir/* -type f -name "*.html" -print0 | xargs -0 mv -t /home/wyatt/Desktop/recup_dir/Bkmrks-Pswrds
find /home/wyatt/Desktop/recup_dir/* -type f -name "*.csv" -print0 | xargs -0 mv -t /home/wyatt/Desktop/recup_dir/Bkmrks-Pswrds

mkdir /home/wyatt/Desktop/recup_dir/Audio
mkdir /home/wyatt/Desktop/recup_dir/Audio/MP3
mkdir /home/wyatt/Desktop/recup_dir/Audio/WMA
mkdir /home/wyatt/Desktop/recup_dir/Audio/WAV
find /home/wyatt/Desktop/recup_dir/* -type f -name "*.mp3" -print0 | xargs -0 mv -t /home/wyatt/Desktop/recup_dir/Audio/MP3
find /home/wyatt/Desktop/recup_dir/* -type f -name "*.wma" -print0 | xargs -0 mv -t /home/wyatt/Desktop/recup_dir/Audio/WMA
find /home/wyatt/Desktop/recup_dir/* -type f -name "*.wav" -print0 | xargs -0 mv -t /home/wyatt/Desktop/recup_dir/Audio/WAV

find /home/wyatt/Desktop/recup_dir/* -type f -name "*.ini" -delete
find /home/wyatt/Desktop/recup_dir/* -type f -name "*.mov" -delete
find /home/wyatt/Desktop/recup_dir/* -type f -name "*.py" -delete
find /home/wyatt/Desktop/recup_dir/* -type f -name "*.a" -delete
find /home/wyatt/Desktop/recup_dir/* -type f -name "*.c" -delete
find /home/wyatt/Desktop/recup_dir/* -type f -name "*.f" -delete
find /home/wyatt/Desktop/recup_dir/* -type f -name "*.h" -delete
find /home/wyatt/Desktop/recup_dir/* -type f -name "*.java" -delete
find /home/wyatt/Desktop/recup_dir/* -type f -name "*.elf" -delete
find /home/wyatt/Desktop/recup_dir/* -type f -name "*.xml" -delete
find /home/wyatt/Desktop/recup_dir/* -type f -name "*.webp" -delete
find /home/wyatt/Desktop/recup_dir/* -type f -name "*.icc" -delete
find /home/wyatt/Desktop/recup_dir/* -type f -name "*.bz2" -delete
find /home/wyatt/Desktop/recup_dir/* -type f -name "*.gz" -delete
find /home/wyatt/Desktop/recup_dir/* -type f -name "*.svg" -delete
find /home/wyatt/Desktop/recup_dir/* -type f -name "*.xz" -delete
find /home/wyatt/Desktop/recup_dir/* -type f -name "*.deb" -delete
find /home/wyatt/Desktop/recup_dir/* -type f -name "*.mbox" -delete
find /home/wyatt/Desktop/recup_dir/* -type f -name "*.pcx" -delete
find /home/wyatt/Desktop/recup_dir/* -type f -name "*.xlsx" -delete

find /home/wyatt/Desktop/recup_dir/* -type d -empty -delete

```

---

### Post by oldfred on 2023-07-01
I had this command inside a bash loop for all .txt files.
cp $filenm $filenm.bak &&
sed "1i\# ${filenm}" $filenm.bak >$filenm

What surprised me at the time was that photorec found many copies of same file, since I had saved some of the many times. I had old backup and it took a long time to sort as not all same size & compare with old backup.

I found for my own python scripts that were not more than a couple of pages, the py2to3.py worked for at least 90% of required update.
Use scripts to help sort and rename files:
[http://www.cgsecurity.org/wiki/After_Using_PhotoRec](http://www.cgsecurity.org/wiki/After_Using_PhotoRec)
use flac tags to rename files 
[http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html](http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html)

---

### Post by wyattwhiteeagle on 2023-07-01
> **oldfred said:**
> I had this command inside a bash loop for all .txt files.
cp $filenm $filenm.bak &&
sed "1i\# ${filenm}" $filenm.bak >$filenm

I know what a bash script is.
Isn't that what I've been using...my own creations using bash commands, options, arguments, etc?

I haven't the slightest clue what a bash loop is.

> **oldfred said:**
> What surprised me at the time was that photorec found many copies of same file, since I had saved some of the many times. I had old backup and it took a long time to sort as not all same size & compare with old backup.

In my case, this is only a scenario, let's say I have a file named 'bash-scripting-001.txt that is 374kb and another file named 'bash-scripting-002.txt' that is 534kb. Obviously, the second file has more info than the first one. Also, the info within the second file may have some different info than what the first file contains.

That's one reason I need to begin putting something in files that specifies the filename.
Apperently, there seems to be a difference between a specification of a filename within the file and the detected filename of the file.

> **oldfred said:**
> I found for my own python scripts that were not more than a couple of pages, the py2to3.py worked for at least 90% of required update.

It would seem to be more complex than that.
I just can't run that command thinking that I have old python2 scripts that I knowingly use that need to be updated.
I haven't created any of my own python scripts at all.
I have no clue how to run a python script, much less create one, even copying and pasting.
In my mind, just running that command isn't gonna do anything.
Is it the same concept as creating and running a bash script?

For the Python2 scripts below...I don't even know where to begin with those.

> **oldfred said:**
> Use scripts to help sort and rename files:
[http://www.cgsecurity.org/wiki/After_Using_PhotoRec](http://www.cgsecurity.org/wiki/After_Using_PhotoRec)
use flac tags to rename files
[http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html](http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html)
Those links are to seemingly Dutch speaking people.
It sucks that people would do something good such as this while updating the program whatever it is without updating the scripts and other info for that program...

In this case...I'm not a super-geek person.
Does the python creator and it's users intend to target only those people who already have the required knowledge and the required experience?

I'm one that needs it and am having to learn about it before I'm able to anything about what my problem is.

I know nothing about Python except that it exists, my system may use it...at which times I have no idea when or how.
And I just got lucky running photorec and testdisk.

Other than that, I'm completely clueless about python.

---

### Post by wyattwhiteeagle on 2023-07-03
I just re-read my last post.
I'm not happy with how I seem to rant on about python.
That wasn't my intention.
I apologize.

My thoughts are going in different directions and it has me going places leaving that path to recovery.

Let me pull myself together here and post back with what I'm looking for.

Again, I apologize for the rant.

---

### Post by oldfred on 2023-07-03
Just glanced at python script. Not sure if it would run under python3 or not as not much to it.
But link has bash & perl scripts as well as some Windows tools.

---

### Post by wyattwhiteeagle on 2023-07-04
A variant of MAFoElffen's bash example seems to be close to what I'm looking for
> **MAFoElffen said:**
> ```

#!/bin/bash

target=$(/media/$USER/usb_drive_label) # /path/to <-- this could be changed to the path the folder where he copied the files to
filelist=$(ls $target/*.txt)  # use path/to var along with file pattern match

for file in ${filelist} # set a filename from the listed files to a var
do
    sed '1 i\ ${file} ' $target/$file  # Use 'sed' to insert a line at the start of each file.
done

```

I would like...

To change only a few line's within the script to be able to use it outside of photorec, Testdisk, and with any directory under /home.

to insert something within all my files so they are easily identified amd renamed should I lose those files.
at least those files which I can do this with.
Doesn't seem possible with files like *.mp3 and *.jpg.

to see what's going on, i.e. verbosity.
to see a progress line in percents.
Much like what is seen when running 'sudo apt full-upgrade'

for any problem messages (such like 'file already exist' and 'cannot overwrite already created' etc) to be exported to a *.txt file on the Desktop.
Idk if this is even possible.

a command line at the end to have terminal tell me when all the commands have been completed.
Idk, maybe just a simple 'done' at the end of a script does what I'm wanting here.

---

### Post by oldfred on 2023-07-04
Did you stop reading after seeing python scripts in the link on after Photorec?

It also has scripts on using internal file data, EXIF information, from photos and some other files.
I have seen posted and used a few of many examples of renaming photo files using info from inside the photo. 
Photos typically save date, time, and now even gps unless you turn that off.

---

### Post by wyattwhiteeagle on 2023-07-04
> **oldfred said:**
> Did you stop reading after seeing python scripts in the link on after Photorec?

It also has scripts on using internal file data, EXIF information, from photos and some other files.
I have seen posted and used a few of many examples of renaming photo files using info from inside the photo. 
Photos typically save date, time, and now even gps unless you turn that off.

Um...when I looked through the photorec links, I skimmed over it looking for a sort of "do the trick quick" bash-scripting example's.
You asking that, let's me know I need to pay closer attention to what I'm looking at.

Most of the photo's I have aren't photo's taken by any kind of camera or video recorder.
Some are my own creations using kolourpaint or mspaint.
Most are images created by a image creation utility from within Blender and other such application programs.

---

### Post by wyattwhiteeagle on 2023-07-05
> **oldfred said:**
> ...I make first line:
# filename.txt...

Does that mean it goes on line 1 in the text editor and '#!/bin/bash' or whatever is used goes on a later line?

Like this...
```
# filename.sh
#!/bin/bash
```

---

### Post by oldfred on 2023-07-05
I was just editing text files, so it could be first line.
If a script then it should be a after required lines like #!/bin/bash. I had always added that to bash & python files, so did not need a version of script to add name to second line.

Insert after match
[https://stackoverflow.com/questions/70270763/sed-pattern-match-then-append-to-line](https://stackoverflow.com/questions/70270763/sed-pattern-match-then-append-to-line)

---

### Post by wyattwhiteeagle on 2023-07-08
I need to take a step back.
How would I do a file pattern match?

---

### Post by wyattwhiteeagle on 2023-07-17
What would happen to the LiveUSB if I used testdisk and photorec to recover old files and data from the LiveUSB?

Would I need to reformat and recreate the LiveUSB?

---

### Post by wyattwhiteeagle on 2023-09-08
Why isn't PhotoRec working?

```
wyatt@wyatt-aspiree1532:~$ photorec --version
PhotoRec 7.1, Data Recovery Utility, July 2019
Christophe GRENIER <grenier@cgsecurity.org>
https://www.cgsecurity.org

Version: 7.1
Compiler: GCC 11.2
ext2fs lib: 1.46.5, ntfs lib: libntfs-3g, ewf lib: none, libjpeg: libjpeg-turbo-2.1.1, curses lib: ncurses 6.3, zlib: 1.2.11
OS: Linux, kernel 5.15.0-83-generic (#92-Ubuntu SMP Mon Aug 14 09:30:42 UTC 2023) x86_64
```
```
wyatt@wyatt-aspiree1532:~$ sudo photorec-7.1
sudo: photorec-7.1: command not found
wyatt@wyatt-aspiree1532:~$ sudo testdisk-7.1/photorec_static
sudo: testdisk-7.1/photorec_static: command not found
wyatt@wyatt-aspiree1532:~$ sudo photorec_static
sudo: photorec_static: command not found

```

---

### Post by wyattwhiteeagle on 2023-09-08
I had to tell it where photorec is...

```
sudo /usr/bin/photorec
```

Only then it worked.

---

### Post by MAFoElffen on 2023-09-09
LMAO!!!! Wyatt-- You are still working on this? You are like a pitbull when you get something going.

I have to say, if nothing else, you are truly persistent. I think I would have given up long ago.

I'm rooting for you. Good Luck.

---

### Post by wyattwhiteeagle on 2023-09-10
> **MAFoElffen said:**
> LMAO!!!! Wyatt-- You are still working on this? You are like a pitbull when you get something going.

I have to say, if nothing else, you are truly persistent. I think I would have given up long ago.

I'm rooting for you. Good Luck.

Thanks a bunch
Atm, I'm recovering important data personal to me from many different drive's.

Not sure when I'll be able to, but my next step is probably to find out what is causing the flash drive's to be rejected.
Yesterday, I loaded some thing's to a 128gb flash drive...perfectly readable...
Today, I attached that same flash drive and *buntu failed to mount the flash but was able to detect it in the partition manager.

---

### Post by dazz411 on 2023-09-12
Look for data recovery software such as r studio and try it out. also avoid overwriting data.

---

