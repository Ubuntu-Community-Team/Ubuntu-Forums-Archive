---
title: "Ubuntu 12.04 will not recognise external HHD"
date: 2016-12-31
forum: General Help
---

### Post by harrydawizard on 2016-12-31
Hey folks, disclaimer: I am not wise in the ways of ubuntu so please speak as if speaking to a nube!

I am running ubuntu 12.04.

I have gotten myself a new 2 TB external HHD factory formatted to NTFS. When I plug it in the icon appears as normal, however when I open to view in a folder nothing appears on the screen. At the bottom of the window there is an indication of 2TB free, (however when opening on a different computer I know there is only 1.87ish TB free).
If I copy a file into the window, the file copy progress shows it copying but when finished nothing happens.
What to do?

---

### Post by ajgreeny on 2016-12-31
With the disk inserted show us the output of ```
sudo fdisk -l
```
Please use **Code-Tags** for terminal output. See my signature below for a **How-to**

---

### Post by TheFu on 2016-12-31
nube?  --> Noob. ;)

Support for 12.04 will end in a few months. Time to upgrade.  You probably want 16.04 (support until 2021). That's what I run on 1 system and plan to move other systems over the next year.

When it comes to Linux systems the first thing to check are the log files.  In most desktop releases, there is a log file checker for noobs. ;)  On servers, we do it with a few typed commands.  [https://help.ubuntu.com/community/LinuxLogFiles](https://help.ubuntu.com/community/LinuxLogFiles) has more explanation.  Normally, any problems will be in the log files.  I look for 'warn' or 'error' case insensitive across all log files. This is pretty easy and a basic skill to have.

```
$ egrep -i 'warn|error' /var/log/*log |less

```
is how I do it.

---

### Post by harrydawizard on 2017-01-02
```
brittany@brittany-AOD257:~$ sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xd32a253e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    27265023    13631488   27  Hidden NTFS WinRE
/dev/sda2       232271870   472770559   120249345    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/sda3   *    27265024    27469823      102400    7  HPFS/NTFS/exFAT
/dev/sda4        27469824   232269823   102400000    7  HPFS/NTFS/exFAT
/dev/sda5       232271872   468865023   118296576   83  Linux
/dev/sda6       468867072   472770559     1951744   82  Linux swap / Solaris

Partition table entries are not in disk order

WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdc: 2000.4 GB, 2000365289472 bytes
256 heads, 63 sectors/track, 242247 cylinders, total 3906963456 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x16f2a91f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1  4294967295  2147483647+  ee  GPT
brittany@brittany-AOD257:~$ ^C
brittany@brittany-AOD257:~$
```

---

### Post by harrydawizard on 2017-01-02
The util fdisk doesn't support GPT. Use GNU Parted.
How do I fix this?

Updating to 16.04 is not an option as this computer is not up to spec.
1GB ram
Intel® Atom&#8482; CPU N570 @ 1.66GHz × 4 
32 bit

---

### Post by TheFu on 2017-01-02
**sudo parted -l**

Also please, please, please, please use "code tags." Impossible to read otherwise.
You can run Lubuntu 16.04. Support for 12.04 ends shortly and forum rules mean we cannot help when that happens.

I had a netbook with that CPU. A $99 chromebook will be faster these days.

---

### Post by harrydawizard on 2017-01-02
Sorry I don't know what you mean but use "code tags"?

Sudo parted -l:

```
brittany@brittany-AOD257:~$ sudo parted -l

Model: ATA WDC WD2500BPVT-2 (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  14.0GB  14.0GB  primary   ntfs            diag
 3      14.0GB  14.1GB  105MB   primary   ntfs            boot
 4      14.1GB  119GB   105GB   primary   ntfs
 2      119GB   242GB   123GB   extended
 5      119GB   240GB   121GB   logical   ext4
 6      240GB   242GB   1999MB  logical   linux-swap(v1)


Model: WD My Passport 259F (scsi)
Disk /dev/sdc: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name         Flags
 1      1049kB  2000GB  2000GB  ntfs         My Passport  msftdata


brittany@brittany-AOD257:~$
```

---

### Post by TheFu on 2017-01-02
> **harrydawizard said:**
> Sorry I don't know what you mean but use "code tags"?


Post #2 has a link that explains it.

---

### Post by harrydawizard on 2017-01-02
```

brittany@brittany-AOD257:~$ sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xd32a253e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    27265023    13631488   27  Hidden NTFS WinRE
/dev/sda2       232271870   472770559   120249345    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/sda3   *    27265024    27469823      102400    7  HPFS/NTFS/exFAT
/dev/sda4        27469824   232269823   102400000    7  HPFS/NTFS/exFAT
/dev/sda5       232271872   468865023   118296576   83  Linux
/dev/sda6       468867072   472770559     1951744   82  Linux swap / Solaris

Partition table entries are not in disk order

WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdc: 2000.4 GB, 2000365289472 bytes
256 heads, 63 sectors/track, 242247 cylinders, total 3906963456 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x16f2a91f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1  4294967295  2147483647+  ee  GPT
brittany@brittany-AOD257:~$ 


```

---

### Post by TheFu on 2017-01-02
Try:```

sudo mkdir /mnt/mp
sudo mount /dev/sdc1 /mnt/mp
```

That will mount the partition into /mnt/mp.  Did it work?

---

### Post by harrydawizard on 2017-01-03
Do you mean to use these one after the other? If I copy both commands only the first line works. Here's what I got:
```

brittany@brittany-AOD257:~$ sudo mkdir /mnt/mp
mkdir: cannot create directory `/mnt/mp': File exists
brittany@brittany-AOD257:~$ sudo mount /dev/sdc1 /mnt/mp
mount: /dev/sdc1 is not a block device
brittany@brittany-AOD257:~$

```

---

### Post by TheFu on 2017-01-03
Has the My Book been formatted? Thought those arrived with NTFS?  

You can try to format it, but I suspect it is a bad drive and should be returned.  I'd use **gparted** to do the formatting. Be very careful. Don't pick the wrong device. It would be bad. Very bad.

It might be 12.04.  Perhaps if you installed 16.04 some of the drivers would handle that disk correctly? Don't really think this is true and not really all that likely. Just throwing out the idea.

I have an older, WD My Book 1140, BTW.

---

### Post by harrydawizard on 2017-01-03
It's a "My Passport" and I actually bought two of them, and they work on my friends Windows 8, so it must be 12.04. They are both acting the exact same and I seeing how they work on another compu I think we can rule out a faulty drive.
It is formatted to NTFS. Is there another format I could try?

---

### Post by TheFu on 2017-01-03
If you want access to the files from Windows, NTFS is really the only choice.

Excellent point about working on other systems.  Might boot up Ubuntu 16.04 on a flash drive (Try Ubuntu) on your friend's computer and see if they still work there. Try this on yours as well.

Oh - and if the other Windows computer doesn't properly "close" the file system, Linux will never open it.  Win8 and later have a setting for this. By default it is enabled, but I don't know if it is enabled for USB connected disks or not. It is meant to make mount/un-mount quicker on Windows, but since that isn't part of the spec, breaks other OSes. [http://www.howtogeek.com/236807/how-to-mount-your-windows-10-or-8-system-drive-on-linux/](http://www.howtogeek.com/236807/how-to-mount-your-windows-10-or-8-system-drive-on-linux/) has more details.

---

### Post by ajgreeny on 2017-01-03
I seem to remember reading that a My Passport drive is usable on Windows only unless it is first reformatted; I think they carry some Windows encryption or protection which can maybe be turned off or removed using Windows if you want any files already on the disk, so it may be worth searching that to see if my memory is correct or playing tricks on us.

A reformat of the disk to a Linux usable filesystem should be quick using gparted, but it will, of course, remove any files now on the disk.

---

### Post by #&amp;thj^% on 2017-01-03
Some more information here: [https://community.wd.com/t/how-to-use-wd-my-passport-with-ubuntu-linux/9115](https://community.wd.com/t/how-to-use-wd-my-passport-with-ubuntu-linux/9115)
I have a 2TB that i use now as storage...and I booted an installed Linux OS from it also.
Hope this is helpful.

---

### Post by harrydawizard on 2017-01-09
As it turns out the problem lay not in the file system type but rather in the partition type.
Disk drives are now formatted with GPT Partition Style. Apparently 12.04 uses MBR Partition Style. Anyways, I cleaned the HDD and initialized the disk with MBR partition style. Now it works just fine. Thanks for the help everyone!

---

### Post by TheFu on 2017-01-09
I started booting from GPT disks in early 2012 while using 32-bit Ubuntu Server on a non-UEFI system. Worked. No issues. Also booted from GPT on a 64-bit Ubuntu Server then. GPT has been well-supported by the core OS/kernel since 10.04.  

Use **parted**/**gparted** for GPT disk partitioning.  Eventually fdisk will support GPT properly, but for now don't use fdisk. It is easier that way.

If you don't use a GUI, mounting of drives works fine - MBR or GPT. That has worked since at least 10.04, maybe earlier.

---

