---
title: "RAID: Change Non-persistent Superblock to Persistent Superblock on Existing Array?"
date: 2008-03-19
forum: General Help
---

### Post by WestCoastSuccess on 2008-03-19
I've long had a RAID 0 array consisting of sdb1 + sdc1 on /dev/md0 (with a separate, non-RAID drive handling boot, etc. - the RAID array is primarily for storing media), however the array has never successfully mounted during the boot sequence. To work around this, I created a simple script launched from a button on my panel, which I click after booting and which mounts the array with no problems:

#sudo mdadm --misc --stop /dev/md0
#sudo mdadm --build /dev/md0 --chunk=64 --level=0 --raid-devices=2 /dev/sdb1 /dev/sdc1
#sudo mount -a

However it's long irritated me that the array won't mount on boot, and after some (read: 10+ hours of) investigation, I THINK it comes down to a non-persistent superblock:

$ sudo mdadm --query --detail /dev/md0

/dev/md0:
        Version : 00.90.03
  Creation Time : Tue Mar 18 14:36:58 2008
     Raid Level : raid0
     Array Size : 621040640 (592.27 GiB 635.95 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0
    Persistence : Superblock is not persistent

    Update Time : Wed Mar 19 04:40:31 2008
          State : active
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

     Chunk Size : 64K

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8       33        1      active sync   /dev/sdc1

/var/log/dmesg repeats the following several times:

[   55.162741] md: md0 stopped.
[   55.162750] md: unbind<sdc1>
[   55.162765] md: export_rdev(sdc1)

My fstab entry for the array appears correct:

#/dev/md0    /mnt/raid    ext3    defaults    0    0

My question: how can I make the superblock of the md0 array persistent? Can it be done without jeopardizing the data in the array? Is this in fact what's preventing md0 from being mounted at boot? Any other thoughts/comments/suggestions? Please let me know if additional info would be useful.

Many thanks!

WCS

---

### Post by fjgaude on 2008-03-19
I think I understand the situation. How was the array originally built? How long ago?

I think there is a way to fix this but it will take some thought and study of the man pages for mdadm.

---

### Post by WestCoastSuccess on 2008-03-19
Thanks for the prompt response!

The array was built perhaps 9 months ago - it's never once mounted at boot. In building it, I created the partitions using fdisk, flagged them as linux autoraid (fd), then used mdadm to create the array:

#sudo mdadm --create /dev/md0 --level=0 --raid-devices=2 /dev/sdb1 /dev/sdc1

Then I THINK I used mkfs.ext3 to create the (single) partition on md0.

I have studied the man pages for mdadm but can't figure out if the mdadm --create command erases data - I presume mkfs.ext3 does...

---

### Post by fjgaude on 2008-03-19
I'm still trying to study more to make recommendations as what to do.

I do know that using "build" distroys the superblocks that were created with "create".

What does the mdadm.conf file show? It's in /etc/mdadm directory.

Have you ever used --assemble --scan to assemble the array?

More tomorrow, down the lines...

---

### Post by WestCoastSuccess on 2008-03-20
Appreciate the help, Frank. Here's some further info:

$ mdadm --assemble --scan
mdadm: /dev/md0 does not appear to be an md device

This is with the array mounted and operating fine!

Here's my mdadm.conf:

# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
ARRAY /dev/md0 level=raid0 num-devices=2 UUID=9ac48b34:0b7da976:e368bf24:bd0fce41


# This file was auto-generated on Sat, 26 May 2007 23:37:11 -0700
# by mkconf $Id: mkconf 261 2006-11-09 13:32:35Z madduck $

Also, here's what fdisk -l produces - the array is last one listed:

$ fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00086912

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2441       38913   292969372+  83  Linux
/dev/sda2            1833        2440     4883760   82  Linux swap / Solaris
/dev/sda3             374        1832    11719417+  83  Linux
/dev/sda4   *           1         373     2996091   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ae7ac

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38658   310520353+  fd  Linux raid autodetect
/dev/sdb2           38659       38913     2048287+  82  Linux swap / Solaris

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000cf093

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       38658   310520353+  fd  Linux raid autodetect
/dev/sdc2           38659       38913     2048287+  82  Linux swap / Solaris

Disk /dev/md0: 635.9 GB, 635945615360 bytes
2 heads, 4 sectors/track, 155260160 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

And here are the mount points, showing md0 mounted:

$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3              12G  8.8G  1.8G  84% /
varrun                2.0G  124K  2.0G   1% /var/run
varlock               2.0G     0  2.0G   0% /var/lock
udev                  2.0G   96K  2.0G   1% /dev
devshm                2.0G     0  2.0G   0% /dev/shm
lrm                   2.0G   38M  1.9G   2% /lib/modules/2.6.22-14-rt/volatile
/dev/sda4             2.9G  121M  2.6G   5% /boot
/dev/sda1             280G  175G  105G  63% /var/lib
none                  2.0G     0  2.0G   0% /dev/shm
/dev/md0              583G  403G  151G  73% /mnt/raid

---

### Post by fjgaude on 2008-03-20
The first time a --build command was used on the array the superblocks were destroyed. md uses them to assemble an array. The --create command created them when first used. Now if you use --create again you will lose all your data.

I've studied the man pages and can't seem to find any place where it says anything about re-creating the superblocks without destroying the data. 

Take a look using the search feature of the PDF to locate what you look for, and see if you can find anything.

What you are going through points to why we should always have one or two backups of important data.

---

### Post by fjgaude on 2008-03-20
I guess I didn't do the attachment correctly. Will try again. Says the file is too big. Sorry about that...

---

### Post by WestCoastSuccess on 2008-03-21
Thanks for confirming "mdadm --create" does indeed lose all the data on the drive - in all my searching I was never able to confirm that and was getting pretty tempted to try it out.

Hmmm...if "mdadm --build" destroys the superblocks, when would it ever be used?

As for backing up the data, the bulk of the array is used for recordings from mythtv, so they're not worth backing up but at the same time would hate to lose them before I've watched them, if that makes sense. In other words, I'd sooner live with having lost the shows than buying a 750GB drive to back up to. The other data in the array I cannot, in any circumstances, lose - my machine also functions as a digital audio workstation, and recorded material/songs/etc. get stored on the array specifically because it's significantly faster than a single disk, and the disk throughput speed is critical to very low latency (0.7ms) recording. Those files get backed up to DVDs.

The strange thing to me is that the array works at all, if it's true that it has no superblocks. What I've never been able to understand is why my simple little script gets it running just fine but it cannot assemble and run via the boot up process.

Any idea how I could insert my script into the boot scripts?

Also, do the disks comprising the array need to be mounted before the array is mounted? If so, perhaps my fstab needs to be edited to mount those first...just a thought.

---

### Post by fjgaude on 2008-03-21
Well, much of what you are curious about I am too.

I do remember that --build was initially used by very old versions of raid that didn't have persistent superblocks.

I would assume from your mdadm.conf file that the --assemble command would work, but doesn't.

No, the individusl drives, partitions do not have to be mounted before the array is assembled. The md function within the kernel starts the process and when it sees the line in fstab assembles the array from the superblocks.

I don't know of anyone who has ever used the --build command, not in the last two years.

I've attached the man page pdf file I use to search for things. Just use your archine manager to extract the file and then use it as a normal pdf file. Simple click it in Nautilus and the viewer comes up with the file showing, full up.

I wish I knew a way to produce the correct superblocks without destroying the data. I would think there is a way, and if anyone here reading this knows, please, please speak up.

---

### Post by WestCoastSuccess on 2008-07-18
Well, I finally have my computer mounting the raid array on boot. Here's what I did:

1) Created a text file called "start_raid" with the following:

```
sudo mdadm --misc --stop /dev/md0
sudo mdadm --build /dev/md0 --chunk=64 --level=0 --raid-devices=2 /dev/sdb1 /dev/sdc1
sudo mount -a
```where "md0" is the raid array and "sdb1" and "sdc1" are the disks/partitions comprising the array.

2) In a terminal, typed:

```
sudo crontab -e
```3) Entered the following (all on one line):

```
@reboot /path/to/start_raid
```On next reboot, raid array was assembled and running and all the files on the array were available.

Hope this helps someone...

Cheers.

---

