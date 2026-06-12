---
title: "disk devices change often after reboot"
date: 2007-05-15
forum: General Help
---

### Post by plmuon on 2007-05-15
I have 7 disks in my system, /dev/sda through /dev/sdg.

4 of these are on the mainboards ICH8 southbridge, 2 are on a Jmicron interface also included on the mainboard and 1 is an external USB disk.

Now sometimes the ICH8 southbridge gets detected as first, sometimes as second (after the jmicron or the external USB disk) and sometimes as last. This has the effect that my boot disk, /dev/sda, sometimes appears as /dev/sdc and sometimes as /dev/sdd instead. (the order of the 4 disks on the ICH8 remains constant).

This is pretty irritating. Since grub always sees the same order, and /etc/fstab uses UUID, this causes no immediate problems, however for setting up raid (md) and luks (crypto disks) this changing of devices is a pain and a risk.

Is it possible to mandate the kernel, when booting, to detect the disks (devices they're connected to) in a fixed order?

---

### Post by LaRoza on 2007-05-15
I though it did detect them in a fixed order. Drive names are assigned at boot up according to their status, /dev/sda is the Master and /dev/sdb would be a slave, the partitions are numbered, Primary first. Are these drives set properly? Are they scsi, sata, or ata/pata?

---

### Post by rbmorse on 2007-05-15
I see the same behavior here is I have both PATA and SATA drives on the machine. When there are only SATA drives (including the optical) partition detection and enumeration is consistent. 

Vexing, to be sure.  Using disk labels or UUIDs in fstab keep this from being a problem, but I don't do RAID or other stuff that depends on consistent partition enumeraton.

---

### Post by rgb129 on 2007-06-13
I have this same problem.  I have a software raid config as well as other drives and this problem messes up the software raid.  Any solutions?

---

### Post by madanasta on 2007-06-22
Same problem here, with Feisty. One SATA drive and one RAID 1 array on a Promise ex8350 are assigned the paths /dev/sda and /dev/sdb on a seemingly random basis at almost every boot. I use UUIDs in fstab so I don't have problems mounting, however I'd really like to fix that as it's inconsistent behaviour and, hence, a potential risk.

---

### Post by emarchman on 2007-07-23
I have motherboard similar to plmuon.  I have 4 SATA ports on the Intel southbridge and two additional ports on a Jmicron.  I have my boot drive on the primary port of the Jmicron and a second drive on the first primary port of the ICH8.  My drives randomly swap between sda and sdb.  

I'm about to install another drive on the second primary ICH8 port for software raid.  I need to resolve this device swapping before I configure the raid.   Has anyone figured this out?

---

### Post by emarchman on 2007-07-24
After some further searching and reading I found a workaround/solution to this problem:

[https://help.ubuntu.com/community/UsingUUID]("https://help.ubuntu.com/community/UsingUUID")

I first found this discussed in a [bug report]("https://bugs.launchpad.net/ubuntu/+source/grub/+bug/8497").

---

### Post by fjgaude on 2007-07-24
> **emarchman said:**
> After some further searching and reading I found a workaround/solution to this problem:

[https://help.ubuntu.com/community/UsingUUID]("https://help.ubuntu.com/community/UsingUUID")

I first found this discussed in a [bug report]("https://bugs.launchpad.net/ubuntu/+source/grub/+bug/8497").

Yes, yes... here is what my fstab looks like to avoid using the "old" way:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=ac668c47-c94e-46ab-9fee-00b1407531bd /   ext3   defaults,errors=remount-ro 0       1
# /dev/sda7
UUID=691be35d-c2bf-44e8-aa71-464ee5ba4b28     none       swap    sw             0       0
/dev/hdd       /media/cdrom0   udf,iso9660 user,noauto    0       0
/dev/hdc       /media/cdrom1   udf,iso9660 user,noauto    0       0
/dev/fd0       /media/floppy0  auto    rw,user,noauto     0       0
#/dev/sda2      /media/sda2     ext3    defaults           0       0
#/dev/sda5      /media/sda5     ext3    defaults           0       0
#/dev/md32      /home/raid      ext3    defaults
UUID=cb9209fc-6f62-4be0-8f86-070278a64bd1  /media/sda2 ext3 defaults  0   0
UUID=0070f51b-b9bf-49f5-905b-ab43c4b50f91  /media/sda5 ext3 defaults  0   0
UUID=631b8942-72bf-4e08-b50c-2d9eeed23e07  /home/raid  ext3 defaults  0   0

Notice the five devices commented out and how the UUID for each is now used.

It's taken awhile but we are all getting there. <smile>

frank

---

### Post by ambrosa on 2007-12-09
> **plmuon said:**
> I have 7 disks in my system, /dev/sda through /dev/sdg.

4 of these are on the mainboards ICH8 southbridge, 2 are on a Jmicron interface also included on the mainboard and 1 is an external USB disk.


I've the same problem with Gutsy and I suppose that the problem is around JMicron.
Since two weeks ago I've only 2 x 200GB SATA harddisk (sda  sdb) inside my motherboard (DFI Infinity 975 equipped with a JMicron eSATA controller). No problem at all. 

Two weeks ago I've added an external 500GB eSATA disk connected to JMicron eSATA controller.
Well, at every reboot I can have (totally random):
/dev/sda ->  first internal SATA disk
/dev/sdb -> second internal SATA disk
**/dev/sdc -> external eSATA disk**

or

**/dev/sda -> external eSATA disk**
/dev/sdb ->  first internal SATA disk
/dev/sdc -> second internal SATA disk

It's not a problem about boot or mounting volume: in /etc/fstab all my disks are mapped with UUID, but there are some tasks that work only with device and not with UUID (parted, TrueCrypt with device crypto volume, ...).

Do anyone know if this bug has been solved ?

Thanks

---

### Post by Menthu_Rae on 2008-05-25
Has anyone found a fix for this yet?

I have a mdadm RAID5 array with 4x 320GB Seagate 7200.10 Drives - they're running on a P35 / ICH9 motherboard (Gigabyte P35 DS3) and even though I've stopped using the JMicron Ports and put in a SIL3114 SATA RAID card (running the OS Drive and DVD Drive off it) - with the RAID5 running off the ICH9 ports - I still get this issue with drives swapping names randomly!

Sometimes it happens when rebooting, cold booting, sometimes it's fine! There's no logical pattern to it :confused:

Here are my mdadm.conf and fstab's for some uber linux person to please help me out - I'm pretty sure I've done everything right though...?

RAID5 performance when the drives don't swap names is excellent:

```
menthurae@Photon:~$ sudo hdparm -Tt /dev/md0


Timing cached reads:   3038 MB in  2.00 seconds = 1518.99 MB/sec

Timing buffered disk reads:  668 MB in  3.00 seconds = 222.46 MB/sec


menthurae@Photon:~$ sudo hdparm -Tt /dev/sda1

/dev/sda1:


Timing cached reads:   2800 MB in  2.00 seconds = 1400.29 MB/sec

Timing buffered disk reads:  166 MB in  3.01 seconds =  55.10 MB/sec


menthurae@Photon:~$ sudo hdparm -Tt /dev/sdb1

/dev/sdb1:


Timing cached reads:   2806 MB in  2.00 seconds = 1402.96 MB/sec
Timing buffered disk reads:  224 MB in  3.01 seconds =  74.31 MB/sec


menthurae@Photon:~$ sudo hdparm -Tt /dev/sdc1

/dev/sdc1:


Timing cached reads:   2814 MB in  2.00 seconds = 1407.19 MB/sec

Timing buffered disk reads:  228 MB in  3.02 seconds =  75.57 MB/sec


menthurae@Photon:~$ sudo hdparm -Tt /dev/sdd1

/dev/sdd1:


Timing cached reads:   2802 MB in  2.00 seconds = 1401.34 MB/sec

Timing buffered disk reads:  238 MB in  3.02 seconds =  78.80 MB/sec


menthurae@Photon:~$ sudo hdparm -Tt /dev/sde1

/dev/sde1:


Timing cached reads:   2832 MB in  2.00 seconds = 1416.04 MB/sec

Timing buffered disk reads:  232 MB in  3.02 seconds =  76.89 MB/sec
```

**mdadm.conf:**

```

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

# 



ARRAY /dev/md0 UUID=ca8a8991:792a87df:e4423db6:25c12c23 level=raid5 num-devices=4 auto=md



# This file was auto-generated on Mon, 14 Apr 2008 21:50:59 +1000

# by mkconf $Id: mkconf 324 2007-05-05 18:49:44Z madduck $

```

**fstab:**

```

# /etc/fstab: static file system information.

#

# <file system> 				<mount point>   <type>  <options>       		<dump>  <pass>

proc            				/proc           proc    defaults        		0       0



# /dev/md0



/dev/md0					/RAID		auto	defaults			0	1



# /dev/sda1

UUID=5e1d155c-2c26-4579-8ae2-39acc139833c 	/               ext3    defaults,errors=remount-ro 	0       1



# /dev/sda2

UUID=8da1bda1-bf1b-4db8-a783-27cd93d25ca0 	none            swap 	sw 				0 	0





/dev/scd0       				/media/cdrom0   udf,iso9660 user,noauto,exec 		0 	0

```

---

### Post by Menthu_Rae on 2008-06-09
> **Menthu_Rae said:**
> Has anyone found a fix for this yet?

I have a mdadm RAID5 array with 4x 320GB Seagate 7200.10 Drives - they're running on a P35 / ICH9 motherboard (Gigabyte P35 DS3) and even though I've stopped using the JMicron Ports and put in a SIL3114 SATA RAID card (running the OS Drive and DVD Drive off it) - with the RAID5 running off the ICH9 ports - I still get this issue with drives swapping names randomly!

Sometimes it happens when rebooting, cold booting, sometimes it's fine! There's no logical pattern to it :confused:

Here are my mdadm.conf and fstab's for some uber linux person to please help me out - I'm pretty sure I've done everything right though...?

I believe I solved my problem by removing the auto=md part from mdadm.conf:

ARRAY /dev/md0 UUID=ca8a8991:792a87df:e4423db6:25c12c23 level=raid5 num-devices=4 **auto=md**

to

ARRAY /dev/md0 UUID=ca8a8991:792a87df:e4423db6:25c12c23 level=raid5 num-devices=4

Haven't had any problems since doing this *touch wood* (and have rebooted/started up a fair few times now)

---

### Post by Menthu_Rae on 2008-07-07
> **Menthu_Rae said:**
> I believe I solved my problem by removing the auto=md part from mdadm.conf:

ARRAY /dev/md0 UUID=ca8a8991:792a87df:e4423db6:25c12c23 level=raid5 num-devices=4 **auto=md**

to

ARRAY /dev/md0 UUID=ca8a8991:792a87df:e4423db6:25c12c23 level=raid5 num-devices=4

Haven't had any problems since doing this *touch wood* (and have rebooted/started up a fair few times now)

Gah! Still having this issue - it seemed to work as I stated above - though it's swapped over 2 times now... not good :(

Might be time to ditch the RAID5 array and go for 2x 1TB drives seeing they're so cheap now.

---

