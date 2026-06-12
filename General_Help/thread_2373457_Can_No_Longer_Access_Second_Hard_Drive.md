---
title: "Can No Longer Access Second Hard Drive"
date: 2017-10-06
forum: General Help
---

### Post by daniell59 on 2017-10-06
My Second hard drive is no longer on the launcher. I do not know how to access the files. Any assistance will be appreciated.

Ubuntu 14.04 32

---

### Post by Autodave on 2017-10-06
Have you checked to make sure that the cables are securely attached to the drive? Does the drive spin up when you turn the machine on?

---

### Post by leunam12 on 2017-10-06
Open the DISKS utility and check the SMART data, your disk may be failing.

---

### Post by daniell59 on 2017-10-06
I checked Smart data. The disk is ok.

---

### Post by daniell59 on 2017-10-06
The hard drive in question needs to be mounted. I don't know how to do it.

---

### Post by ajgreeny on 2017-10-06
Show us the output of ```
sudo fdisk -l
sudo blkid -c /dev/null
``` in terminal and we can tell you how to add a line to /etc/fstab which will then mount the disk at boot.

---

### Post by daniell59 on 2017-10-06
daniel@daniel-N68SA-M2S:~$   sudo mkdir /media/mynewdrive
[sudo] password for daniel: 
daniel@daniel-N68SA-M2S:~$ sudo mount /dev/sdb1 /media/mynewdrive 
mount: you must specify the filesystem type
daniel@daniel-N68SA-M2S:~$ clear

daniel@daniel-N68SA-M2S:~$ sudo fdisk -l
[sudo] password for daniel: 
Sorry, try again.
[sudo] password for daniel: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x32e232e2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   112965415    56482676+   7  HPFS/NTFS/exFAT
/dev/sda2       112965630   312580095    99807233    5  Extended
/dev/sda5       308393984   312580095     2093056   82  Linux swap / Solaris
/dev/sda6       112965632   308393983    97714176   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00046e07

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   304195583   152096768   83  Linux
/dev/sdb2       304197630   312580095     4191233    5  Extended
/dev/sdb5       304197632   312580095     4191232   82  Linux swap / Solaris
daniel@daniel-N68SA-M2S:~$ sudo blkid -c /dev/null
/dev/sda1: UUID="00F8AB1FF8AB1248" TYPE="ntfs" 
/dev/sda5: UUID="06a719a6-5e80-4c7b-b761-3ca4dee40b6e" TYPE="swap" 
/dev/sda6: UUID="1e343cf5-fe25-4b89-a646-8b3153b3deb9" TYPE="ext4" 
/dev/sdb5: UUID="f7cda503-237d-4505-9e98-26fa01206c86" TYPE="swap" 
daniel@daniel-N68SA-M2S:~$

---

### Post by ajgreeny on 2017-10-06
I am confused as it looks as if you have an installation of a Linux OS on that second drive, dev/sdb, according to the fdisk output.
```
/dev/sdb1 * 2048 304195583 152096768 83 Linux
/dev/sdb2 304197630 312580095 4191233 5 Extended
/dev/sdb5 304197632 312580095 4191232 82 Linux swap / Solaris
```
Is that what you expected?

Do you see icons in the left pane of your file manager for those partitions? Internal disk partitions are usually shown there and a click on them mounts the partition.
sdb1 is the only partition you will be able to read, but as it's ext4 you will probably not be able to write to it as you will not be the owner, and if it really is an OS you want to boot again you may not be able to use chmod to change ownership without damaging the ability to boot that OS.

---

### Post by Bashing-om on 2017-10-06
daniell59; Hello;

UNgood, but maybe not real bad .

Let's see what we can do.

Now what we know:
the target is sdb.
> 
mount: you must specify the filesystem type

tells us that the file system on the device is messed up.

Good thing here is that fdisk sees the file system :
> 
/dev/sdb1 * 2048 304195583 152096768 83 Linux


so, how bad is the file system corrupted - we run a simple file system check ?
Post back the results of terminal commands:
From liveDVD(USB) so everything is unmounted,swap off if necessary.
```

sudo swapoff -a

```
Make sure the target is still sdb1 with a current 
```

sudo fdisk -lu

```

And now to see what tale is told:
```

sudo e2fsck -C0 -p -f -v /dev/sdb1

```

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by daniell59 on 2017-10-06
WDC WD1600AAJS-00B4A0 (01.03A01) is my storage drive. Should I just format it, and start all over again?

---

### Post by Bashing-om on 2017-10-06
daniell59; Well,

We can know nothing to give advise about until we have the info to base a choice on.

What does -fsck have to say ?

[INDENT][INDENT]garbage in == garbage out
[/INDENT][/INDENT]

---

### Post by daniell59 on 2017-10-06
I tried to format the hard drive. could not do it. Please advise.
Error formatting volume
Error erasing device: Error writing 1048576 bytes to /dev/sdb1: Input/output error (udisks-error-quark, 0)

---

### Post by Yellow Pasque on 2017-10-06
Use gparted to make a new boot sector. Otherwise, you're probably looking at a bad drive.

---

### Post by Bashing-om on 2017-10-06
daniell59; Well.

1) you format a device (sdb)
2) partitions (sdb1) contain the file system.

What system are you working from to re-format the sdb devices ? and what tool are you using therein ?
how are you creating the partitions ?


[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by daniell59 on 2017-10-06
No matter what I do in Gparted I get the following Input/output error during write on /dev/sdb

---

### Post by ajgreeny on 2017-10-06
If there is nothing on sdb that you need, the easiest way is probably for you to create a new partition table and then a new partition using gparted.

Accept the default msdos PT, then in the unallocated space you've just made, create a new partition and format it as ext4 if for use with Ubuntu only, or as fat32 or ntfs if you need to use it in Windows as well.  If you chose ntfs you really need Windows as that is the only way that it is repairable if it should ever need that in the future.

---

### Post by daniell59 on 2017-10-06
> **ajgreeny said:**
> If there is nothing on sdb that you need, the easiest way is probably for you to create a new partition table and then a new partition using gparted.

Accept the default msdos PT, then in the unallocated space you've just made, create a new partition and format it as ext4 if for use with Ubuntu only, or as fat32 or ntfs if you need to use it in Windows as well.  If you chose ntfs you really need Windows as that is the only way that it is repairable if it should ever need that in the future.

Tried to create new partition table. The following is the result.

Libparted bug found
Input/output error during write on /dev/sdb

---

### Post by ajgreeny on 2017-10-07
It sounds as if that disk is dead as a new PT should be possible, as far as I'm aware, whatever the state of the current filesystem on it.

Strange! Can you check again with SMART in the Disks application to see if anything else appears in the output; something is obviously wrong somewhere but nothing is appearing yet to tell us what that is.

---

### Post by daniell59 on 2017-10-10
I ran a test on the hard drive in question. It seems to have passed all tests. I don't why I cannot partition the hard drive.

---

### Post by daniell59 on 2017-10-10
I changed the SATA cable and and put it into a different SATA socket. I was then able to create a partition and format it to ext 4.

---

### Post by Bashing-om on 2017-10-10
daniell59; :)

You do good work . Thanks for providing the solution .

[INDENT][INDENT]Where there us a will .......[/INDENT][/INDENT]

---

### Post by daniell59 on 2017-10-10
There is still something that I do not understand.
On the launcher I see 160GB volume. Under that is 58GB volume. Only the 58 one is usable. I would like to be able to use the entire drive.

Thanks

---

### Post by Bashing-om on 2017-10-10
daniell59; Hey ..

Me, the terminal minded that I am, 
> 
 I would like to be able to use the entire drive.

I want to see a terminal output of what is:
```

sudo fdisk -lu
sudo blkid -c /dev/null -o list

```

[INDENT][INDENT]deduce what ain't
[/INDENT][/INDENT]

---

### Post by daniell59 on 2017-10-10
Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x32e232e2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   112965415    56482676+   7  HPFS/NTFS/exFAT
/dev/sdb2       112965630   312580095    99807233    5  Extended
/dev/sdb5       308393984   312580095     2093056   82  Linux swap / Solaris
/dev/sdb6       112965632   308393983    97714176   83  Linux

Partition table entries are not in disk order
daniel@daniel-N68SA-M2S:~$ sudo blkid -c /dev/null -o list
device     fs_type label    mount point    UUID
-------------------------------------------------------------------------------
/dev/sda1  ext4             /media/daniel/34b6bb40-bc7e-4fb7-a64f-f65ac77b5740 34b6bb40-bc7e-4fb7-a64f-f65ac77b5740
/dev/sdb1  ntfs             /media/daniel/00F8AB1FF8AB1248 00F8AB1FF8AB1248
/dev/sdb5  swap             <swap>         06a719a6-5e80-4c7b-b761-3ca4dee40b6e
/dev/sdb6  ext4             /              1e343cf5-fe25-4b89-a646-8b3153b3deb9
daniel@daniel-N68SA-M2S:~$

---

### Post by Bashing-om on 2017-10-10
daniell59; Hummm ...

For all intents and purposes you are using all the space on sdb
never the mind that 62 sectors are not used for alignment purposes at the start of the disk and that 1713 sectors at the end - overprovision - :
we have 2 partitions 
sdb1 as  windows 
sdb2 as extended ..

Now we talk about that extended partition. It is a "container" partition - that holds "logical" partitions .
In your case these logical partitions are  sdb5 as swap and sdb6 as the linux partition.

As you are mounting from /media I would expect on the GUI that you see:
sda1
sdb1
sdb6

But confused ! here . Why is ubuntu mounted from /media ? And how ?
Please post back - Between code tags to maintain the formatting - the outputs of: 
```

cat /proc/mounts
cat /etc/fstab

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

See what we can finger out .

Are we looking at an explicit mount that redirects the GUI ?

[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

