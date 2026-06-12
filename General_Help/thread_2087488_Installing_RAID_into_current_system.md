---
title: "Installing RAID into current system"
date: 2012-11-23
forum: General Help
---

### Post by DanBender on 2012-11-23
Hi folks!

I'm trying to install a set of disks as a RAID array into my current Mythbuntu system. And much of the help topics I can consistently find on the subject are either 1) how to install Ubuntu in a RAID environment or 2) detailed instructions on how to use mdadm. Neither of which is proving very useful right now.

Here's what I *want*: I currently have two disks in my system, a 500 GB drive with several partitions for /, /home, etc. (mainly ext4-formatted), and a 1 TB XFS-formatted disk mainly for MythTV stuff. I currently have photos stored on one of the first disk's partitions, and home videos in a folder on the second. I just installed two 2 TB drives, and want to RAID1 them and migrate the photos and videos there for better fail-resistance. I do NOT want to make the entire system RAID-driven; the single-disk nature of the system is more than sufficient since I can rebuild the system if part of it dies. Not so the pictures and movies.

I do have the new drives physically installed in the machine; they are now /dev/sdc and /dev/sdd respectively. No partitions have been defined on them yet.

I took a look at [the official documentation page on installing to RAID,]("https://help.ubuntu.com/community/Installation/SoftwareRAID") but it's for installing on a new system, so much of it appears to not applicable, specifically what tools to use. It's also for 9.10, so some of it may be outdated.

I then found [this page about mdadm]("http://linuxdevcenter.com/pub/a/linux/2002/12/05/RAID.html"), but something about it totally turns my head sideways when I try to read it. I got partway through the first page, but I'm pretty sure I did something wrong, since it keeps talking about sdx#'s and I haven't partitioned them yet. [This page]("http://ubuntuforums.org/showthread.php?t=408461") seems to indicate you partition *then *RAID, but do I have to do it that way? Or can I RAID the base drives together *then *partition them as a unit?

So what I want to accomplish is:
1) stop and erase any existing multi-disk configurations already on my computer. It is unclear how to do that from the mdadm --help information. Whether or not one of the links I already pointed to actually have the info I think I'm looking for and I'm just confusing myself out of using it, this part needs to happen.
2) find a straightforward step-by-step information on how to set up a RAID array into my system,* including when and how to partition the disks,* whether that be GParted or mucking about in fstab or some other means. Preferably one without anything about installing Linux when I'm done.

If any of you can help turn my head the right direction, I would be eternally grateful.

---

### Post by DanBender on 2012-12-02
I think I have it figured out. Read the whole thing before you ask questions on it.

I was following the instructions on [this page.]("http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch26_:_Linux_Software_RAID#.ULp61dfNl8E")

**1) I added a partition to both disks** of ext4, using GParted. partitions take the whole disk.

**2) I created the RAID:**
```
sudo mdadm --create /dev/md0 --name=sharedisk --level=1  --raid-devices=2 /dev/sdc1 /dev/sdd1
```3) I added the following to  /etc/mdadm/mdadm.conf:
```
DEVICE /dev/sdc1 /dev/sdd1
ARRAY /dev/md0 metadata=1.2 name=tv-computer:sharedisk  UUID=
f9faa9b8:f736bfa6:8356a741:3420b211
```which was the result of  sudo mdadm --detail --scan.

**4) I formatted the array itself:**
```
mkfs.ext4 /dev/md0
```

**5) I tested.** I then created a folder for it and mounted.
```
sudo mkdir /media/share_disk
sudo mount /dev/md0 /media/share_disk
sudo chmod 777 /media/share_disk
```I placed a file inside. Then I  unmounted it and the file went away -- I re-mounted it and it came back. So it worked.

**6) I set the new md partition to automount.** I  added the following to /etc/fstab:
```
# sharedisk RAID array
/dev/md0   /media/share_disk   ext4   defaults   1   2
```...and rebooted.

_**This is where it stopped working.**_ The loader complained that it could not find the device /dev/md0, so I skipped that mount. GParted now shows a device /dev/md127 with much the same details, but it obviously isn't what I told it to be. The output of mdadm now reads:```
tv@tv-computer:~$ sudo mdadm --detail /dev/md0
mdadm: cannot open /dev/md0: No such file or directory
tv@tv-computer:~$ sudo mdadm --detail --scan
ARRAY /dev/md/tv-computer:sharedisk metadata=1.2 name=tv-computer:sharedisk UUID
=f9faa9b8:f736bfa6:8356a741:3420b211
tv@tv-computer:~$ sudo mdadm --detail /dev/md/tv-computer:sharedisk
/dev/md/tv-computer:sharedisk:
        Version : 1.2
  Creation Time : Sat Dec  1 15:56:33 2012
     Raid Level : raid1
     Array Size : 1953382208 (1862.89 GiB 2000.26 GB)
  Used Dev Size : 1953382208 (1862.89 GiB 2000.26 GB)
   Raid Devices : 2
  Total Devices : 2
    Persistence : Superblock is persistent

    Update Time : Sun Dec  2 15:04:47 2012
          State : active 
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           Name : tv-computer:sharedisk  (local to host tv-computer)
           UUID : f9faa9b8:f736bfa6:8356a741:3420b211
         Events : 40

    Number   Major   Minor   RaidDevice State
       0       8       33        0      active sync   /dev/sdc1
       1       8       49        1      active sync   /dev/sdd1
```I then figured that maybe it wasn't storing the actual device number, but the disk name. so I tried:
```
tv@tv-computer:~$ sudo mount /dev/md/tv-computer:sharedisk /media/share_disk
```...and it mounted, unmounted, and re-mounted! So I edited /etc/fstab again, changing the last line to:
```
# sharedisk RAID array
/dev/md/tv-computer:sharedisk   /media/share_disk   ext4   defaults   1   2
```And now it works, even with reboots.

---

### Post by dcstar on 2012-12-03
> **DanBender said:**
> 
.........
And now it works, even with reboots.

Then MARK the thread.

---

### Post by DanBender on 2012-12-18
Well, an update to the Linux kernel and it seems it doesn't recognize the /dev/md/tv-computer:sharedisk stuff anymore. but /dev/md0 appears to be consistent again. I don't know what's going on again.

---

### Post by steeldriver on 2012-12-18
Not 100% sure about this but I *think* that you need to run update-initramfs one time so that your mdadm.conf is available at boot time

[http://ubuntuforums.org/showthread.php?t=1764861](http://ubuntuforums.org/showthread.php?t=1764861)

I don't see that step anywhere in your post. And yes I did read the whole thing. ;)

---

### Post by DanBender on 2012-12-20
> **steeldriver said:**
> Not 100% sure about this but I *think* that you need to run update-initramfs one time so that your mdadm.conf is available at boot time

[http://ubuntuforums.org/showthread.php?t=1764861](http://ubuntuforums.org/showthread.php?t=1764861)

I don't see that step anywhere in your post. And yes I did read the whole thing. ;)
That sounds very similar to the behavior I was seeing. I will look into it. Thanks!

-Dan

---

