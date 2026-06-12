---
title: "cannot mount because folder is busy."
date: 2016-01-24
forum: General Help
---

### Post by javascripter on 2016-01-24
I have a windows 8.1 computer that broke somehow recently, and because I heard that I could use Ubuntu to get files off of it, I put it on a flash drive, and am trying to follow this tutorial ([http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)) with the end goal of being able to copy files from windows to the flash drive and then move them to other computers.

I followed the tutorial mostly successfully, with three complications.

Firstly, when I typed "sudo umount /dev/sbd1" into the terminal, it said something about the device being busy. I solved(?) this by typing "sudo umount -l /dev/sbd1" instead, after some googling.

Secondly, the top line of my fstab is "overlay / overlay rw 0 0" instead of "proc /proc proc defaults 0 0". I tried with both lines, and with each individually, and it didn't seem to affect anything that I observed.

Thirdly, this is where I am stuck, when I type "sudo mount -a" it says "mount: /dev/sdb1 already mounted or /home/ubuntu/Desktop/windows busy", and I am fairly sure that /dev/sdb1 isn't mounted, because if I type "sudo umount /dev/sdb1" is says "umount: /dev/sdb1: not mounted". I have confirmed that both google and the Ubuntu version I am using are 64 bit.

The Ubuntu version I am using is the default free version from here ([http://www.ubuntu.com/download/desktop/contribute/?version=14.04.3&architecture=amd64](http://www.ubuntu.com/download/desktop/contribute/?version=14.04.3&architecture=amd64)), which is 14.04.3.
My windows is FAT32, though I don't know what that means.

---

### Post by yancek on 2016-01-24
If you want to mount a partition, you need a mount point which is simply a directory to which you mount the partition to make it accessible.  I would be surprised if a windows 8 system is using a FAT32 format as windows systems have been using ntfs for twenty years.  You can find this out by opening a  terminal in Ubuntu and entering the following command:

```
sudo parted -l
```

That's a lower case letter L in the command.   Under the filesystem column, it will show the filesystem type and under the Number column it will show the partition number.  Above that you will see the drive information.  If you don't understand it, post the output here.  If the windows partition you actually want to mount is actually sdb1 you first create a mount point with the command:

```
sudo mkdir /mnt/sdb1
```

After that enter the command below:

```
sudo mount -t ntfs /dev/sdb1 /mnt/sdb1
```

If those aren't the correct parameters, you will need to change them based on the parted output.
You don't need any entry in fstab on the Ubuntu flash drive.

---

### Post by javascripter on 2016-01-24
So, I though I understood sudo parted -l; and then I noticed that I was only reading the last line, and there are 7 other file systems. I'm pretty sure that i was trying to mount the Ubuntu that I was using to type in the terminal.

So, here is the output:
```

Model: ATA ST1000LM024 HN-M (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size    File system  Name                          Flags
 1      1049kB  1050MB  1049MB  ntfs         Basic data partition          hidden, diag
 2      1050MB  1322MB  273MB   fat32        EFI system partition          boot, hidden
 3      1322MB  2371MB  1049MB  fat32        Basic data partition          hidden
 4      2371MB  2505MB  134MB                Microsoft reserved partition  msftres
 5      2505MB  960GB   957GB   ntfs         Basic data partition          msftdata
 6      960GB   987GB   26.8GB  ntfs         Basic data partition          msftdata
 7      987GB   1000GB  13.4GB  ntfs         Basic data partition          hidden, diag


Model: Lexar USB Flash Drive (scsi)
Disk /dev/sdb: 16.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  16.0GB  16.0GB  primary  fat32        boot, lba


```

So I think there are seven partitions on the windows? Which ones do I mount in order to find files on the desktop (or other places of the computer)? 
Also, why are some fat32, while others are ntfs, while one doesn't have a type?

---

### Post by Dennis N on 2016-01-25
From your display, mount and check the big one first: sda5
Some are fat32 because of the standards set for their function. sda2 for example, is an EFI system partition which contains the boot files to start up Windows.

---

### Post by javascripter on 2016-01-25
So, I got this error.

```

The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Failed to mount '/dev/sda5': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.

```

where in the command do i put "ro" to make it read only? 

Alternatively, Windows is as shut down as I know how to get it. In order to turn it off I have to hold down the power button (because something about the computer broke.) and now I just either set the Ubuntu to boot first, or I hold f12 and select the Ubuntu on startup. I'm not sure if there is a way to start up Ubuntu on the flash drive without getting that far into starting up the computer normally, or if there is a way to temporarily remove the windows boot from that list? Not even sure that that would help?

---

### Post by yancek on 2016-01-25
There are only two filesystems shown in the parted output, FAT32 and ntfs.  There are 7 partitions.  Your problem is that you cannot mount from Ubuntu or any Linux OS because your windows system is hibernated and not fully shut down.  That is the default on windows 8 and newer so they appear to boot faster.  I don't use hibernation myself or windows so I don't know if you can make these changes without booting windows.  You might check the BIOS to see if you can turn off hibernation  or anything related to fast boot and see if that helps.

---

### Post by javascripter on 2016-01-25
I looked through the setup menu (held down f2 when starting windows, only thing I can look through) and didn't see any options that would do anything like that. I tried turning secure boot off because it seemed the most relevant, but as I figured, that did nothing.

---

### Post by javascripter on 2016-01-25
Nevermind, I used google to find an example of mounting as read only and I can copy files from windows that way, so it is working well enough.

---

