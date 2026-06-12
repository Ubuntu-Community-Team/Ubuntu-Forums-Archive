---
title: "Can not access files on external hard disk"
date: 2018-07-28
forum: General Help
---

### Post by offir on 2018-07-28
I have an old laptop hard disk
With a pata connection

I want to transfer the files on it to another hard disk

I connected the disc to the usb adapter
And connected to the computer

The computer recognized the disk and showed me the files
I clicked the desired folder with the files (25 GB)
I clicked Copy
I went to the new folder on my second hard disk
And clicked paste


The computer started copying the files
And got stuck in 1849 files which are 3.7 gigabytes
I tried it three times


I tried it on a computer with Windows 7 operating system
The same result


Now I tried to connect the disc to the computer with the Ubuntu
The computer does not recognize the disk
It shows that the disk is connected but it is not formatted
I tried to run gparted but does not work when the disc is connected to the computer

How can I access and copy the files without the disk stopping 
When the disc is running it has no unusual noise

---

### Post by dragonfly41 on 2018-07-28
I assume from your signature that "the computer" is a Ubuntu 16.04?

If gparted cannot view your external drive try running testdisk (from Ubuntu 16.04) to inspect the external device.

[https://www.cgsecurity.org/wiki/Damaged_Hard_Disk](https://www.cgsecurity.org/wiki/Damaged_Hard_Disk)

---

### Post by offir on 2018-07-28
> I assume from your signature that "the computer" is a Ubuntu 16.04?
Yes, I forgot 
i have ubuntu 16.04



> If gparted cannot view your external drive try running testdisk (from Ubuntu 16.04) to inspect the external device.
when the external hdd is connected gparted is Not working (run/open) at all

---

### Post by dragonfly41 on 2018-07-28
Check if external device is detected by running command

```
sudo -H fdisk -l
```

---

### Post by offir on 2018-07-28
this is what i got 

According to the result computer recognizes the disc
It appears in the last two lines


```
Disk /dev/loop0: 11.6 MiB, 12165120 bytes, 23760 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop1: 86.6 MiB, 90812416 bytes, 177368 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop2: 86.9 MiB, 91099136 bytes, 177928 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop3: 4.8 MiB, 4976640 bytes, 9720 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop4: 10.6 MiB, 11116544 bytes, 21712 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop5: 9.1 MiB, 9519104 bytes, 18592 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop6: 86.9 MiB, 91115520 bytes, 177960 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 149.1 GiB, 160041885696 bytes, 312581808 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x7ad93477

Device     Boot     Start       End   Sectors   Size Id Type
/dev/sda1  *         2048 304472063 304470016 145.2G 83 Linux
/dev/sda2       304474110 312580095   8105986   3.9G  5 Extended
/dev/sda5       304474112 312580095   8105984   3.9G 82 Linux swap / Solaris




Disk /dev/sdb: 93.2 GiB, 100030242816 bytes, 195371568 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x30ff8ef5

Device     Boot    Start       End   Sectors  Size Id Type
/dev/sdb1             63  12594959  12594897    6G 12 Compaq diagnostics
/dev/sdb2  *    12594960 195366464 182771505 87.2G  7 HPFS/NTFS/exFAT

```

---

### Post by dragonfly41 on 2018-07-28
I suggest that you research threads such as this one ..

[https://askubuntu.com/questions/697767/listing-the-files-on-a-device-from-the-command-line](https://askubuntu.com/questions/697767/listing-the-files-on-a-device-from-the-command-line)

explaining that your external device needs to be mounted in order to transfer files.

i.e. you need to mount device /dev/sdb2 to start file transfer.

---

### Post by offir on 2018-07-28
I understand that
the question is
Why when I first copied files it got stuck at 3.7 GB
And the disk was stuck and had to be disconnected and reconnected
And now it does not recognize the disc at all

If now I could make the computer recognize the disc
How do I avoid the first problem (I can not copy a file without having the disc stuck)

---

### Post by dragonfly41 on 2018-07-28
> [COLOR=#000000]I clicked the desired folder with the files (25 GB)[/COLOR]
[COLOR=#000000]I clicked Copy[/COLOR][COLOR=#000000]

I would not copy 25GB in that way. Certainly not 25GB in one bite. In fact I'm not sure if you can.
Why not use a file transfer tool (there are many) but I would look at FileZilla.
Or Thunar. Or Grsync.

In fact I use Krusader for file navigation but it does carry a lot of KDE baggage.
There is also Midnight Commander.[/COLOR]

---

### Post by offir on 2018-07-28
I succeeded mount the hdd
But I went back to the original problem
Every time I copy something it starts and after about 10 seconds gets stuck
No matter how many files I want to copy if it's 10 MB or 10 GB or 3 GB

---

### Post by dragonfly41 on 2018-07-28
Then as another idea I would try testdisk and copy files from device via testdisk.

---

### Post by offir on 2018-07-28
how do i do that ?
do i need to copy evrey file separately or i can copy a Folder

---

### Post by dragonfly41 on 2018-07-28
I would prefer to point you to official guidance ...

[https://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](https://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

---

### Post by dragonfly41 on 2018-07-28
I should add an explanatory note that you should hide deleted files (listed in testdisk) since you do not want to copy those previously deleted files into your recovery destination.   There may be other times when this feature of recovering deleted files is useful but not for your current scenario.

[https://yz.mit.edu/wp/recovering-files-using-testdisk/](https://yz.mit.edu/wp/recovering-files-using-testdisk/)

Read comments from that blog ..
"[COLOR=#2A2E2E][FONT=&quot]TestDisk copies your files to the directory from which you started the program."

That is ensure that you create an empty recovery directory in your Ubuntu 16.04 home directory.
Then launch testdisk from within that recovery folder .. sudo testdisk
If you do not follow this workflow you may find recovered files mixed with your other files.[/FONT][/COLOR]

---

### Post by offir on 2018-07-28
will it work if i will select the main folder 25 giga?

---

### Post by dragonfly41 on 2018-07-28
Should do so provided that you don't included deleted files (as explained) and you have at least 25GB available in your recovery folder.
I recollect that there is a dry run option in testdisk which tests if the operation will work without errors.
And you have set log file to see what is going on.

But you could post a question at testdisk forum.

Note that some operations might take hours, sometimes overnight.

---

### Post by offir on 2018-07-29
I tried it


it says 96 ok 
but it copy barely 50 MB

It keeps stopping after a short period of time
And it copies barely 50 MB

---

### Post by offir on 2018-07-29
I spoke too early
Now it has risen to 727

Probably as you wrote it could take a whole night

What is the final number to reach? (To what number it counts ?)

---

### Post by dragonfly41 on 2018-07-29
I have no idea what the maximum count might be.  It will depend on the number of files to be copied.
I would have tried a smaller recovery file set, just to test the process.
And a word of warning. Usually the destination for recovery is an external device (such as flash drive) and not the host computer.
But I assume that you don't have another device to avoid using your host Ubuntu 16.04.
Another approach is to launch testdisk in a Ubuntu LiveUSB (you will need to install testdisk each time you use LiveUSB).
There are many tutorials if you search.

I assume that you have a backup of your Ubuntu 16.04?

---

### Post by offir on 2018-07-29
> I would have tried a smaller recovery file set, just to test the process
A little problematic
All folders there appear in letters in a language other than English
The main folder is English
So I just chose it


> And a word of warning. Usually the destination for recovery is an external device (such as flash drive) and not the host computer
Yes
The destination folder is an external drive.


> I assume that you have a backup of your Ubuntu 16.04? 
You mean installation disk?

---

### Post by dragonfly41 on 2018-07-29
Backup of Ubuntu 16.04 is less important (but still recommended) since you confirm above that you are using an external drive into which testdisk copies recovered files. I had worries of testdisk overwriting Ubuntu 16.04 filesystem if not set up correctly.
You should be able to inspect testdisk logfile without quitting the testdisk run.

---

### Post by offir on 2018-07-29
Thank you

it worked
Extract the entire main folder 25.1 gb

I left the computer working
And I left the house for an hour
Now I came back and saw that it was finished

I did not see what number it reached

---

