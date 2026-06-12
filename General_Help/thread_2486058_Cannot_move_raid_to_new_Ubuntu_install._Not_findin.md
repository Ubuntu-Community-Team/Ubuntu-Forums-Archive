---
title: "Cannot move raid to new Ubuntu install. Not finding superblocks."
date: 2023-04-18
forum: General Help
---

### Post by lasivian on 2023-04-18
So we had a motherboard die. Copied the mdadm.conf to the new install (Could not get the old install running on the new motherboard, but the files are fine)

I moved over /etc/mdadm/mdadm.conf and it contains:
```
# mdadm.conf
#
# !NB! Run update-initramfs -u after updating this file.
# !NB! This will ensure that initramfs has an uptodate copy.
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default (built-in), scan all partitions (/proc/partitions) and all
# containers for MD superblocks. alternatively, specify devices to scan, using
# wildcards if desired.
#DEVICE partitions containers

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
ARRAY /dev/md/0  metadata=1.2 UUID=81589382:0deb199e:78a8c4ce:c7e2b9db name=lasivian-media:0

# This configuration was auto-generated on Sat, 21 Nov 2020 07:28:10 -0800 by mkconf
```

When I try to run mdadm --assemble --scan I get```

mdadm: looking for devices for /dev/md/0
mdadm: No super block found on /dev/loop12 (Expected magic a92b4efc, got 3be3e454)
mdadm: no RAID superblock on /dev/loop12
mdadm: No super block found on /dev/loop11 (Expected magic a92b4efc, got b94e0a62)
mdadm: no RAID superblock on /dev/loop11
mdadm: No super block found on /dev/loop10 (Expected magic a92b4efc, got 217afcb3)
mdadm: no RAID superblock on /dev/loop10
mdadm: No super block found on /dev/loop9 (Expected magic a92b4efc, got 3e22646e)
mdadm: no RAID superblock on /dev/loop9
mdadm: No super block found on /dev/loop8 (Expected magic a92b4efc, got 6042ae44)
mdadm: no RAID superblock on /dev/loop8
mdadm: No super block found on /dev/sde1 (Expected magic a92b4efc, got 0000041d)
mdadm: no RAID superblock on /dev/sde1
mdadm: No super block found on /dev/sde (Expected magic a92b4efc, got aa5caca8)
mdadm: no RAID superblock on /dev/sde
mdadm: No super block found on /dev/sdd (Expected magic a92b4efc, got 00000000)
mdadm: no RAID superblock on /dev/sdd
mdadm: No super block found on /dev/sdc (Expected magic a92b4efc, got 00000000)
mdadm: no RAID superblock on /dev/sdc
mdadm: No super block found on /dev/sdb (Expected magic a92b4efc, got 00000000)
mdadm: no RAID superblock on /dev/sdb
mdadm: No super block found on /dev/sda3 (Expected magic a92b4efc, got 00000476)
mdadm: no RAID superblock on /dev/sda3
mdadm: No super block found on /dev/sda2 (Expected magic a92b4efc, got 00000000)
mdadm: no RAID superblock on /dev/sda2
mdadm: No super block found on /dev/sda1 (Expected magic a92b4efc, got f4d143af)
mdadm: no RAID superblock on /dev/sda1
mdadm: No super block found on /dev/sda (Expected magic a92b4efc, got 00000000)
mdadm: no RAID superblock on /dev/sda
mdadm: No super block found on /dev/loop7 (Expected magic a92b4efc, got 2073e02a)
mdadm: no RAID superblock on /dev/loop7
mdadm: No super block found on /dev/loop6 (Expected magic a92b4efc, got 6405001a)
mdadm: no RAID superblock on /dev/loop6
mdadm: No super block found on /dev/loop5 (Expected magic a92b4efc, got 6405001a)
mdadm: no RAID superblock on /dev/loop5
mdadm: No super block found on /dev/loop4 (Expected magic a92b4efc, got c4b43b1a)
mdadm: no RAID superblock on /dev/loop4
mdadm: No super block found on /dev/loop3 (Expected magic a92b4efc, got f9eb15cb)
mdadm: no RAID superblock on /dev/loop3
mdadm: No super block found on /dev/loop2 (Expected magic a92b4efc, got 32138a62)
mdadm: no RAID superblock on /dev/loop2
mdadm: No super block found on /dev/loop1 (Expected magic a92b4efc, got 32138a62)
mdadm: no RAID superblock on /dev/loop1
mdadm: /dev/loop0 is too small for md: size is 8 sectors.
mdadm: no RAID superblock on /dev/loop0
```

This is what I get with mdadm --misc -E /dev/sd*
```
/dev/sdb:
   MBR Magic : aa55
Partition[0] :   4294967295 sectors at            1 (type ee)
/dev/sdc:
   MBR Magic : aa55
Partition[0] :   4294967295 sectors at            1 (type ee)
/dev/sdd:
   MBR Magic : aa55
Partition[0] :   4294967295 sectors at            1 (type ee)
```

Any suggestions? Thanks

---

### Post by MAFoElffen on 2023-04-19
Followed the link from your other thread... ([https://ubuntuforums.org/showthread.php?t=2486015](https://ubuntuforums.org/showthread.php?t=2486015))

I am assuming, by this post, that there were no backups, right?

First make dd images of the disks, so you have a backup of the disks for fallback.
```

mdadm: No super block found on /dev/sdb (Expected magic a92b4efc, got 00000000)
mdadm: no RAID superblock on /dev/sdb
mdadm: No super block found on /dev/sdc (Expected magic a92b4efc, got 00000000)
mdadm: no RAID superblock on /dev/sdc
mdadm: No super block found on /dev/sdd (Expected magic a92b4efc, got 00000000)
mdadm: no RAID superblock on /dev/sdd

```
and
```

/dev/sdb:
   MBR Magic : aa55
Partition[0] :   4294967295 sectors at            1 (type ee)
/dev/sdc:
   MBR Magic : aa55
Partition[0] :   4294967295 sectors at            1 (type ee)
/dev/sdd:
   MBR Magic : aa55
Partition[0] :   4294967295 sectors at            1 (type ee)

```
Here is I what I see. The 3 disks were formally GPT partitioned drives. Protected MBR type GPT, denoted as type EE... The original RAID was created without superblocks being written, because there were GPT partition table still there (without being zapped first by sgdisk --zap for disks being used as "whole disk RAID" that were formerly partitoned as GPT... but at the time, the system got away with it because the initramfsfs image was created while that Array was still active... I also found this:
> 
Another important argument is that some mainboards may delete your RAID superblocks if you use whole disk devices and are not super careful with wiping them when adding disks to a RAID array that once were GPT devices.

I always recommend to people that if they are creating mdadm Software RAID, LVM2, or ZFS, that they do it inside of created partitions (bond) instead of whole-disk (unbound). It can be done, but I've had nightmarish, disastrous results from them. For mdadm partitions, I use type 'fd' (Linux RAID autodetect).

Too late for this one except to do something risky to rescue it... Therefore the need for images of the disks, beforehand.

First
```

lsblk -o NAME,SIZE,TYPE,FSTYPE,MOUNTPOINT -i /dev/sd[a-d],/dev/nvme[0-2]n[1-4]
sudo mdadm --examine /dev/sd[b-d]
sudo mdadm --detail /dev/md0

```
I suspect it's going to still say it can't find RAID superblocks on those devices.

There is a work around, but it isn't for the light heart'ed and it risky. Zero out the drives
```

sudo sgdisk --zap /dev/sdb
sudo sgdisk --zap /dev/sdc
sudo sgdisk --zap /dev/sdd

```
Once that is done for all 3 drives, then do
```

mdadm --create /dev/md0 --level=5 --raid-devices=3 /dev/sdb /dev/sdc /dev/sdd

```
This will start to create a new RAID Array, but will see that something already exists there. It will tell you that it already detects past data there , and asks if you want to continue re-using that data. Say yes of course...

Create a new mdamd.conf file in case anything changed (such as the new superblock, hint), and do an update-intramfs to update the images...
```

sudo mdadm --detail --scan >> /etc/mdadm/mdadm.conf
sudo update-initramfs -u

```

---

### Post by lasivian on 2023-04-19
For the love of... **Facepalm** 

Thanks. I'm just finding this all very frustrating because I didn't figure that Linux would have problems like this that I can't solve.

I guess the best solution is to replace the dead hardware with older hardware to get the original install running since we don't have backups or the space to make backups. 

Thank you

---

### Post by MAFoElffen on 2023-04-19
This can run on new hardware.... It will just take time.

I do IT Consulting... So my wife tells people that "I can do things". LOL

I have a 2 Drive USB3 SATA Dock that I use just for these kinds of things. Put the old drive in with another drive to dd copy to. Done. Or plugging it in to rescue data off someones's computer... Or to test booting something. I think it was only $40. It was a very good investment.

RE: [https://ubuntuforums.org/showthread.php?t=2485881&p=14139613#post14139613](https://ubuntuforums.org/showthread.php?t=2485881&p=14139613#post14139613)

We used to use similar to test and erase drives at a computer recylcer that I volunteered for.

---

### Post by TheFu on 2023-04-19
a) if you can't spend to have backups, then the data isn't worthy of being RAID'ed.  Backups come BEFORE RAID.  RAID solves 2 issues.  Backups solve 101 issues, including a corrupted RAID.

b) Always, always, always, setup a partition table and place RAID devices into a partition with an exact, known, size. In this way, you aren't tied to HDDs with the exact same geometry going forward. Losing a little RAID storage is well worth the added flexibility in knowing that the size of the partition is exactly, 3880000000 sectors. Keep the sector count exact for all parts of the RAID.

I've moved my mdadm RAID arrays forward since Ubuntu 8.06, across 4 different hardware systems and at least than number of OSes.

---

### Post by MAFoElffen on 2023-04-19
Exactly. Like I said, I do not recommend installing mdadm, LVM2, or ZFS to full disks, outside of partitions. When I taught college students on this, it is possible to do, but is an invitation for disaster sometime down the road. What I referred to as bound and unbound storage containers.

If it were mine, or someone was paying me to recover their business'es data... I would (first) dd copy all to new disks, and recover those disks. After recovery, I would migrate it to a new array, set up on their old disk, created within partitions (set up correctly), so that this type of thing doesn't happen again. That is just the right thing to do.

RAID, and Snapshots (LVM and ZFS) are not a replacement for **Backups**. Backups do not need to be full system images, but rather just what is needed beyond a Fresh install to get you back to an acceptable point of time. That all factors on what is considered as "your" acceptable risk. As TheFu said, if you do not want to do backups, then I accept that your acceptable risk is losing everything.

I respect and feel that TheFu has such a great, amazing grasp on backups, backup strategies, and Disaster Recovery. I have been doing IT Professionally for over 33 years now, and I can read what he has written on those for hours and hours.

The problem already exists. That was not the fault of Linux. It was procedural. The same would happen on Windows soft-RAID. The superblocks read as "00000000" on those 3 disks, which is invalid. I suspect that your plan of going "to older" hardware will be the same kind of challenge. With the superblocks gone, the problem is there and is not going away.

I proposed that there is a way to (possibly) reuse and see the data there and recover your RAID Array. I was the project lead for 'mdadm-gui', so I had to learn a little more about mdadm than a lot of people. So I have a bit of experience recovering from strange circumstances. LOL I actually talked to TheFu about a lot of that. He actually convinced me to kill that project.

Most other's would have told you that with the circumstances "you have" that the Array is impossible to recover, and to start over from a freshly built array. You can always do "that'. Linux is more resilient and you can do a lot of things. Even things to recover from other's procedural mistakes.

---

