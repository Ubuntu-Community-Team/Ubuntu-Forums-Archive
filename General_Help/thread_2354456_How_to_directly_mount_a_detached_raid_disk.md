---
title: "How to directly mount a detached raid disk"
date: 2017-03-02
forum: General Help
---

### Post by cjsmall on 2017-03-02
I want to be able to directly mount and access the contents of a hard disk that has been detached from a mirror.  When I try to mount the disk, I get the message:

    **mount: unknown filesystem type 'linux_raid_member'**

My question is whether there is a way to configure things so that I can mount the disk RO, then unmount it and reattach it to the mirror.  The RAID-1 mirror consists of two stable disks.  Occasionally, I attach a third disk, allow it to sync, then detach it.  I want to be able to mount this third disk for the purpose of file recovery in case of user error.


Here are the particulars:

The system is running Xubuntu 16.10 with two sets of RAID-1 mirrored disks.

The primary disk is a set of SSDs which have two partitions:
    /dev/md0:  the root partition with a ext4 filesystem
    /dev/md1:  the swap partition with a linux-swap filesystem

The second mirror -- the one in question -- consists of a set of 4TB hard drives.  These disks were formatted using GParted with single full disk partition:
    Partition Table->gpt
    Partition->New
        Free space preceding (MiB):  1
        New Size                 (MiB):  3815447
        Free space following  (MiB):  0
        Align to:                            MiB
        Create as:                         Primary Partition
        File system:                       ext4
        Label:                               md2_d[123]

When the mirror is mounted at boot, Linux typically creates it as /dev/md127 and the accessible contents as /dev/md127p1.  Partition /dev/md127p1 is a ext4 filesystem and the component devices vary upon boot, but are typically created as /dev/sda, sdj & sdk.

When /dev/sda is detached, GParted shows it as having a linux-raid filesystem.

Being new to Linux, I read a number of articles on raid configuration and there were suggestions to use the entire disk as a raid member vs. partitioning the disk and then using the manually created partition for the raid.  I opted to use the entire disk, but now wonder if that was a mistake.  Insights into that area are welcome.

So, back to my question.  Is there a method of mounting the ext4 filesystem on this disk? 

Thanks.

---

