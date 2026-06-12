---
title: "Ubuntu 22.04 won't boot (ALERT! UUID=xxx does not exist. Dropping to a shell)"
date: 2022-10-05
forum: General Help
---

### Post by 0atmeal on 2022-10-05
I was trying to restart my computer, but clicking the option from the drop-down wouldn't do anything for some reason, so I held down the power button. But now, when I try to boot it back up, it gets stuck. After it shows the Asus loading screen, for the next 10 minutes it just spits out a long list of errors. The last thing it prints is:
```
ALERT! UUID=[long string of numbers and letters] does not exist. Dropping to a shell.
```

And then it prompts for text, but beginning with ```
(initramfs)
``` instead of the usual ```
uname@uname:~$
```. 

I've tried going to BIOS, but I can't find anything that looks like it might help. I have no idea what any of it does.

Booting from a live usb works, though. I checked Disks, and it looks like something is wrong with the one named "Hard Disk" (the one I have my OS and all my files stored on). Apparently it has no data associated with it anymore. The model is blank, the size is also blank, and in Volumes it just says "No Media". Only piece of info it does display is the directory, "/dev/sda".

Is there any way that I can fix this? Are all my files gone? Please help!

---

### Post by yancek on 2022-10-06
>  ALERT! UUID=[long string of numbers and letters] does not exist. Dropping to a shell

It's looking for the UUID of the root filesystem partition and can't find it.  Did you make any changes just prior to this happening?  What you need to do is boot the live usb and run the command:  blkid
After doing that compare the UUID for your root filesystem partition with the UUID referenced in the error and check the /boot/grub/grub.cfg file as well as /etc/fstab to see if the UUIDs are the same.

Try the command:  sudo fdisk -l to see what output you get.  Also you might try running a filesystem check on the root filesystem partition.  The link below explains how to do that and gives various options so give that a read.

[https://www.tecmint.com/fsck-repair-file-system-errors-in-linux/](https://www.tecmint.com/fsck-repair-file-system-errors-in-linux/)

Rather than power down by holding down the power button which often creates problems, a safe way to reboot is to simultaneously hold down the alt key and the prtsc key while typing in reisub consecutively.

---

### Post by 0atmeal on 2022-10-06
The last thing I did before powering off was sudo apt uninstall and reinstall WINE, I haven’t messed with partitions or anything in awhile.

blkid didn’t list /dev/sda at all. It listed 7 /dev/loops though, not really sure what those are.

fdisk -l didn’t have an sda either. Only thing else out of the ordinary was some red text that said, “Partition 1 does not start on physical sector boundary”.

Trying to run “sudo fsck /dev/sda” returns, “Invalid argument while trying to open /dev/sda”, and then “The superblock could not be read or does not describe a valid ext2/ext3/ext4 filesystem”, and that if the file system really is valid then the superblock is corrupt, and to try running e2fsck with an alternate superblock. 
Trying to do that just results in the same error.

I also can’t even seem to get back to the “dropping to a shell” screen anymore. This time it just goes straight to this other screen, with an orange triangle logo and “American Megatrends” at the top. It lists some of the computer’s info and then at the bottom, it says that I need to replace my hard drive. Pressing F1 goes to BIOS. 

Could it really have completely died? The “Disks” application at least acknowledges the hard drive’s existence though. Maybe it’s possible to re-format it or something?

---

### Post by tea for one on 2022-10-06
> **0atmeal said:**
> Trying to run “sudo fsck /dev/sda” returns, “Invalid argument while trying to open /dev/sda”
You should run fsck on a partition such as sda1 or nvme0n1p1
```
sudo fsck /dev/sda1
```
> Maybe it’s possible to re-format it or something? 
Quite possibly but it would be useful if you could post the details.
Boot into a live session, open a terminal and run:-
```
sudo parted -l
```
Please post the command and output within code tags for legibility.

---

### Post by 0atmeal on 2022-10-06
Output of fsck:
```

ubuntu@ubuntu:~$ sudo fsck /dev/sda1
fsck from util-linux 2.34
e2fsck 1.45.5 (07-Jan-2020)
fsck.ext2: No such file or directory while trying to open /dev/sda1
Possibly non-existent device?

```
replacing "sda1" with "nvme0n1p1" gives the same error.

Output of parted (The "ignore"s are user inputs):
```
ubuntu@ubuntu:~$ sudo parted -l
Warning: Error fsyncing/closing /dev/sda1: Input/output error
Retry/Ignore? Ignore                                                      
Warning: Error fsyncing/closing /dev/sda2: Input/output error
Retry/Ignore? ignore                                                      
Error: /dev/sda: unrecognised disk label                                               
Warning: Error fsyncing/closing /dev/sda: Input/output error
Retry/Ignore? ignore                                                      
Model: ATA WDC WDS120G2G0A- (scsi)
Disk /dev/sda: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: unknown
Disk Flags: 

Model: SanDisk Cruzer Glide (scsi)
Disk /dev/sdb: 61.5GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  61.5GB  61.5GB  primary  fat32        boot, lba

```
It looks like it at least *sees* my hard drive, it lists the model number and size and everything (ATA WDC, /dev/sda, 120GB). The SanDisk Cruzer Glide is just the live usb I booted from.

---

### Post by tea for one on 2022-10-06
> **0atmeal said:**
> 
```
ubuntu@ubuntu:~$ sudo parted -l
Model: ATA WDC WDS120G2G0A- (scsi)
Disk /dev/sda: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: unknown

```
It looks like it at least *sees* my hard drive, it lists the model number and size and everything (ATA WDC, /dev/sda, 120GB).

Yes, the drive is visible - good news
Unknown partition table - bad news.
Without a partition table, there will be no partitions.
You can see that fsck also failed with the message "Possibly non-existent device? "

Before any more suggestions, do you have a recent backup of your personal data?

---

### Post by 0atmeal on 2022-10-06
> **tea for one said:**
> Before any more suggestions, do you have a recent backup of your personal data?
Eh, recent enough I guess - at this point I’d be happy to just have the hard drive back. Is the data even accessible in the drive’s current state anyhow?

---

### Post by tea for one on 2022-10-06
> **0atmeal said:**
> Is the data even accessible in the drive’s current state anyhow?
There is some software (testdisk and photorec) which may help with a forensic search of your drive.
I've never used it, but I understand that it is a long-winded process.
[https://www.cgsecurity.org/wiki/Main_Page](https://www.cgsecurity.org/wiki/Main_Page)
> Eh, recent enough I guess - at this point I’d be happy to just have the hard drive back
If you are happy that your backup is in good order, you can boot into a live Ubuntu session and see if Gparted can create a partition table and partitions.

---

### Post by 0atmeal on 2022-10-06
> **tea for one said:**
> If you are happy that your backup is in good order, you can boot into a live Ubuntu session and see if Gparted can create a partition table and partitions.

I'd like to do this, but the hard drive isn't showing up in Gparted. The only one that shows up is the live usb. Is there some way to make Gparted detect the hard drive?

---

### Post by tea for one on 2022-10-07
Via a live session, does the drive still show with the terminal command ```
sudo parted -l
```
There is another terminal command to try ```
edited@edited:~$  sudo gdisk /dev/sda
[sudo] password for edited: 
GPT fdisk (gdisk) version 1.0.8

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.

Command (? for help): q (press q to exit)
edited@edited:~$ 

```
Also, there is the GUI utility Disks (gnome-disks).

---

### Post by yancek on 2022-10-07
>  I'd like to do this, but the hard drive isn't showing up in Gparted

If the hard drive showed with parted which it did as you posted the output above, then it should show in GParted.  I don/t know how familiar you are with GParted.  Have you clicked the drop down arrow in the upper right of the page to show other drive options?

An "unknown" partition table is a pretty serious problem.  As suggested above, the most likely way you can get your data back is to use testdisk, see the link below.  It's pretty complicated for a newer user but there are Step By Step instructions.

[https://www.cgsecurity.org/wiki/TestDisk](https://www.cgsecurity.org/wiki/TestDisk)

---

### Post by Seb71 on 2022-10-07
Was it encrypted?

---

### Post by Paddy Landau on 2022-10-07
I wonder if your computer stopped responding because your drive became faulty, and had nothing to do with you forcibly powering it down?

[HR][/HR]
For future note, please avoid powering down by holding down your power button if at all possible. It can cause data corruption. Better methods include:

[LIST]
[*]Press Ctrl+Alt+F3 to log into a console. Once there, enter this command:
```
reboot
```
This closes down cleanly before rebooting.
[/LIST]

[LIST]
[*]If that doesn't work, you need to resort to [REISUB]("https://en.wikipedia.org/wiki/Magic_SysRq_key#Uses") (which reads BUSIER backwards). To use this, press the following keys, in order. (The [SysReq]("https://en.wikipedia.org/wiki/Magic_SysRq_key") key on most computers is Alt+PrintScreen.)
[LIST]
[*]SysReq+R — sets the keyboard to "raw"
[*]SysReq+E — asks the programs nicely to close down, so wait a minute after pressing this to let them close
[*]SysReq+I — forces all programs still running to close down immediately
[*]SysReq+S — synchronises data on your open partitions to prevent data corruption
[*]SysReq+U — sets your open partitions to read-only to prevent further writes
[*]SysReq+B — reboots the computer
[/LIST]
[/LIST]
(Ubuntu has disabled REI by default, so they'll do nothing, leaving just SUB. I don't know why Canonical did this.)

Commit these to memory. They come in handy!

---

### Post by 0atmeal on 2022-10-07
> **tea for one said:**
> Via a live session, does the drive still show with the terminal command ```
sudo parted -l
```
That's weird... I just tried it again, and parted doesn't actually show the hard drive anymore... it just shows the live usb now. Why would it just stop showing the hard drive?
```
ubuntu@ubuntu:~$ sudo parted -l
Model: SanDisk Cruzer Glide (scsi)
Disk /dev/sdb: 61.5GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  61.5GB  61.5GB  primary  fat32        boot, lba

```

Also, here's the output of gdisk:
```
ubuntu@ubuntu:~$ sudo gdisk /dev/sda
GPT fdisk (gdisk) version 1.0.5

Problem reading disk in BasicMBRData::ReadMBRData()!
Warning! Read error 22; strange behavior now likely!
Warning! Read error 22; strange behavior now likely!
Partition table scan:
  MBR: MBR only
  BSD: not present
  APM: not present
  GPT: not present


***************************************************************
Found invalid GPT and valid MBR; converting MBR to GPT format
in memory. THIS OPERATION IS POTENTIALLY DESTRUCTIVE! Exit by
typing 'q' if you don't want to convert your MBR partitions
to GPT format!
***************************************************************


Command (? for help):
```
What command should I give it?

---

### Post by 0atmeal on 2022-10-07
> **yancek said:**
> I don/t know how familiar you are with GParted.  Have you clicked the drop down arrow in the upper right of the page to show other drive options?
Yeah the drop-down only shows the live usb, unfortunately. But the hard drive doesn't show in parted either now for some reason, so I dunno.

---

### Post by 0atmeal on 2022-10-07
> **tea for one said:**
> Also, there is the GUI utility Disks (gnome-disks).
Yeah Disks does show the hard drive, but all the information about it is blank. it looks like this:
```

Model --
 Size --
Volumes
---------------------------------------------------------------
                       No Media
---------------------------------------------------------------
       Size --
     Device /dev/sda
   Contents --
```

---

### Post by tea for one on 2022-10-07
Let's try gdisk again and go a bit further (any data on the disk will be lost):-
```
sudo gdisk /dev/sda
```
Create a new GPT 
```
o
```
Write table to disk
```
w
```
Exit if not already done
```
q
```

No partitions yet but, I wonder if Gparted can see it now?

---

### Post by 0atmeal on 2022-10-07
Just ran it, but Gparted still cant see the drive :(
```
ubuntu@ubuntu:~$ sudo gdisk /dev/sda
GPT fdisk (gdisk) version 1.0.5

Problem reading disk in BasicMBRData::ReadMBRData()!
Warning! Read error 22; strange behavior now likely!
Warning! Read error 22; strange behavior now likely!
Partition table scan:
  MBR: MBR only
  BSD: not present
  APM: not present
  GPT: not present


***************************************************************
Found invalid GPT and valid MBR; converting MBR to GPT format
in memory. THIS OPERATION IS POTENTIALLY DESTRUCTIVE! Exit by
typing 'q' if you don't want to convert your MBR partitions
to GPT format!
***************************************************************


Command (? for help): o
This option deletes all partitions and creates a new protective MBR.
Proceed? (Y/N): y

Command (? for help): w
Caution! Secondary header was placed beyond the disk's limits! Moving the
header, but other problems may occur!
Warning! The claimed last usable sector is incorrect! Do you want to correct
this problem? (Y/N): y
Have adjusted the second header and last usable sector value.

Partition(s) in the protective MBR are too big for the disk! Creating a
fresh protective or hybrid MBR is recommended.

Final checks complete. About to write GPT data. THIS WILL OVERWRITE EXISTING
PARTITIONS!!

Do you want to proceed? (Y/N): y
OK; writing new GUID partition table (GPT) to /dev/sda.
Unable to save backup partition table! Perhaps the 'e' option on the experts'
menu will resolve this problem.
Warning! An error was reported when writing the partition table! This error
MIGHT be harmless, or the disk might be damaged! Checking it is advisable.

Command (? for help): q
```

---

### Post by tea for one on 2022-10-07
Perhaps venture into the next level of gdisk.
If you start gdisk again and enter
```
r
```
You will be presented with further choices including the e option mentioned in the output.
Here is the list of further options
```
Recovery/transformation command (? for help): ?
b	use backup GPT header (rebuilding main)
c	load backup partition table from disk (rebuilding main)
d	use main GPT header (rebuilding backup)
e	load main partition table from disk (rebuilding backup)
f	load MBR and build fresh GPT from it
g	convert GPT into MBR and exit
h	make hybrid MBR
i	show detailed information on a partition
l	load partition data from a backup file
m	return to main menu
o	print protective MBR data
p	print the partition table
q	quit without saving changes
t	transform BSD disklabel partition
v	verify disk
w	write table to disk and exit
x	extra functionality (experts only)
?	print this menu

```
From the various outputs so far, I would doubt that the drive can be successfully repaired but, you know, we live in mysterious times.

---

### Post by 0atmeal on 2022-10-08
Okay so I rebooted from the live usb, and Gparted can actually see the  hard drive now. I clicked on *Device/Create New Partition Table* and then  had to click ignore on 20+ error messages, but in the end it looks like  it *might* have worked. Gparted still thinks there's no partition table (it just says "unallocated"), but  gnome-disks now lists 2 partitions: sda1 and sda2. Its name under gnome disks also changed, from Hard Disk to 120 GB Disk.
What should I do from here?

Also I tried the r and e options on gdisk but they didn't seem to do much:
```
ubuntu@ubuntu:~$ sudo gdisk /dev/sda
GPT fdisk (gdisk) version 1.0.5

Problem reading disk in BasicMBRData::ReadMBRData()!
Warning! Read error 22; strange behavior now likely!
Warning! Read error 22; strange behavior now likely!
Partition table scan:
  MBR: MBR only
  BSD: not present
  APM: not present
  GPT: not present


***************************************************************
Found invalid GPT and valid MBR; converting MBR to GPT format
in memory. THIS OPERATION IS POTENTIALLY DESTRUCTIVE! Exit by
typing 'q' if you don't want to convert your MBR partitions
to GPT format!
***************************************************************


Command (? for help): r

Recovery/transformation command (? for help): e
Warning! This will probably do weird things if you've converted an MBR to
GPT form and haven't yet saved the GPT! Proceed? (Y/N): y
Error! Couldn't seek to partition table!

Recovery/transformation command (? for help): w
Caution! Secondary header was placed beyond the disk's limits! Moving the
header, but other problems may occur!
Warning! The claimed last usable sector is incorrect! Do you want to correct
this problem? (Y/N): y
Have adjusted the second header and last usable sector value.

Partition(s) in the protective MBR are too big for the disk! Creating a
fresh protective or hybrid MBR is recommended.

Final checks complete. About to write GPT data. THIS WILL OVERWRITE EXISTING
PARTITIONS!!

Do you want to proceed? (Y/N): y
OK; writing new GUID partition table (GPT) to /dev/sda.
Unable to save backup partition table! Perhaps the 'e' option on the experts'
menu will resolve this problem.
Warning! An error was reported when writing the partition table! This error
MIGHT be harmless, or the disk might be damaged! Checking it is advisable.

```

---

### Post by 0atmeal on 2022-10-08
Just tried formatting /dev/sda in Disks, but it didn't work. got this error
```
Error wiping device: Failed to probe the device '/dev/sda2' (udisks-error-quark, 0)
```
same error with sda1 as well, regardless of the filesystem selected. I even tried toggling "Erase", but no change.

---

### Post by ronakmehta on 2022-10-19
The solution was to run these commands from liveDVD, which allows me to execute tasks on my sda1 from that liveDVD (as far I understand)
```
[COLOR=var(--black-800)][FONT=var(--ff-mono)]sudo mount /dev/sda1 /mnt[/FONT][/COLOR]
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys
sudo chroot /mnt
update-initramfs -u
update-grub [COLOR=var(--black-800)][FONT=var(--ff-mono)]reboot[/FONT][/COLOR]
```

My friend from the Ubuntu Pl forum assisted me with resolving this [issue]("http://ubuntu.pl/forum/viewtopic.php?f=133&t=175292&p=993631#p993631"). He discovered a mistake in initramfs, which should be fixed as part of the kernel upgrade. Problems like mine might occur if something goes wrong during the upgrade.
The Debian installation procedure is rather pleasant in that it warns me that there may be non-UEFI partitions that would no longer operate if I try to install grub in UEFI mode (and suggests starting in BIOS compatibility mode) which Mint doesn't seem to worry about. As a result, mint setup my grub in UEFI mode. Although the semi-structured data model (as suggested [here]("https://www.scaler.com/topics/dbms/data-models-in-dbms/"))is a very generalised form of the relational model that allows representing data in a flexible manner, we cannot differentiate between data and schema in this model because, in this model, some entities may have a missing attribute(s) and, on the other hand, some entities may have some extra attribute(s), making it easy to update the database's schema.

---

### Post by ActionParsnip on 2022-10-19
in gdisk is you press P then ENTER to (P)rint the partitions, what is output?

---

