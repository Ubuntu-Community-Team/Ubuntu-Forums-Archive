---
title: "After deleting partition can't resize to reclaim space."
date: 2018-02-12
forum: General Help
---

### Post by sports fan Matt on 2018-02-12
Since I deleted a partition to get ready for the upcoming 18.04, I cannot seem to reclaim that space so only one partition is showing.  I installed the partition via USB if that matters.  

boot repair:  ============================= Boot Info Summary: ===============================

 => Grub2 (v2.00) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub. It also embeds following components:
    
    modules
    ---------------------------------------------------------------------------
    fshelp ext2 part_msdos biosdisk
    ---------------------------------------------------------------------------

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 16.04.3 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/i386-pc/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        /grub2/grub.cfg /grub2/i386-pc/core.img

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________
Disk /dev/sda: 596.2 GiB, 640135028736 bytes, 1250263728 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   604,215,295   604,213,248  83 Linux
/dev/sda2       1,242,101,758 1,250,263,039     8,161,282   5 Extended
/dev/sda5       1,242,101,760 1,250,263,039     8,161,280  82 Linux swap / Solaris
/dev/sda3         604,215,296   606,312,447     2,097,152  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        15ef628f-f9e4-4b50-9ced-f8445f885a77   ext4       
/dev/sda3        7693ed4a-604a-4781-b2b0-5db58406a333   ext4       
/dev/sda5        398524a9-0191-439f-bc28-792577f0a487   swap       

Let me know if I need the entire thing.

---

### Post by TheFu on 2018-02-12
Can't tell for sure (code tags would help readability greatly), but sda2 is a "container" for sda5 and higher partitions because the disk is formatted MBR, not GPT.  sda3 might be inside the extended partition too. My memory on the MBR rules is failing.

This is one of those very few times when using **gparted** to get a visual representation will make it clearer ... er ... probably.

---

### Post by sports fan Matt on 2018-02-12
That sounds right, honestly.  Now how to get it out of the extended partition.

---

### Post by oldfred on 2018-02-12
Your extended partition is the exact size as your swap (other than required sectors before a partition).
So your space is not inside the extended.

Are you using a live installer's version of gparted or gparted's own live system?
And unmounting swap as Ubuntu's live installer normally mounts swap?

---

### Post by vanadium on 2018-02-12
Does not look like this to me. First comes sda1, from sector 2,048 to 604,215,295. Then there is sda3 from 604,215,296 to 606,312,447. The swap partition sda5 is (practically) fully filling the extended partition sda2, that extends from 1,242,101,758 	to 1,250,263,039. The gap is between 606,312,447 and 1,242,101,758. It should be possible to add another primary partition in that gap, or expand sda3 to fill that space.

---

### Post by TheFu on 2018-02-12
If swap is the only partition inside the extended partition, I would ```

0. turn off swap, 
1. delete the swap partition, 
2. delete the extended partition,
3. create a new extended partition using all available storage,
4. create a 4G swap inside the extended,
5. create another data partition inside the extended
6. use mkswap to make the 4G "swap"
7. use mkfs -t ext to create the ext4 on the other partition
8. use swapon to add the swap
9. use mount with UUID= /path-to-empty-mount-point to test the mounting.
then go into the /etc/fstab and manually add the swap and new mount with UUIDs. Be certain to remove the old swap line (or just edit it for the new UUID).
```

You can find the new UUID mappings in /dev/disk/by-uuid/ with an **ls -alF**. There is a command that works too, but I forget it.

Clear as mud?

---

### Post by sports fan Matt on 2018-02-12
I'm using Gparted from inside 16.04.  I will need help on doing all these tasks because I am just not understanding.  

3. create a new extended partition using all available storage
4. create a 4G swap inside the extended, (not sure how)
5. create another data partition inside the extended (only thing I did was create the extended partition)
6. use mkswap to make the 4G "swap" (I need help on 6-9)
7. use mkfs -t ext to create the ext4 on the other partition
8. use swapon to add the swap
9. use mount with UUID= /path-to-empty-mount-point to test the mounting.
then go into the /etc/fstab and manually add the swap and new mount with UUIDs. Be certain to remove the old swap line (or just edit it for the new UUID).

Screenshot is where I am now.

---

### Post by Impavidus on 2018-02-12
> **sports fan Matt said:**
> Since I deleted a partition to get ready for the upcoming 18.04, I cannot seem to reclaim that space so only one partition is showing.

What do you mean by "so only one partition is showing"? Do you wish to expand the existing partitions into the unallocated space?

---

### Post by sports fan Matt on 2018-02-12
Yes, correct.

---

### Post by oldfred on 2018-02-12
If using gparted you do not need to use the command line method.

But surprised it is working as little key icon says sda1 is mounted. And normally you have to use gparted from live installer.
Perhaps now as long as not trying to change sda1, it still works?

Just click on unallocated in extended and add partition. I usually add swap first, but make it at end and 4000MB.
Then easy to just use remaining for an ext4 partition. I also like to label partition at same time, once created (right click).

Then to see UUID.
       sudo blkid -c /dev/null -o list 
    or:
 lsblk -o NAME,LABEL,PARTLABEL,SIZE,UUID,MOUNTPOINT

---

### Post by TheFu on 2018-02-12
That image is completely different from what I expected - much easier since the extended partition is empty and fills the rest of the disk.

You don't want to fill the other partitions into that space to "make room for 18.04" - that would be bad.

I have a few rules of thumbs when it comes to partitioning.
* swap should be a little over 4GB in size. Doesn't matter if you have a 2G RAM or 32G RAM machine.  4.1G for desktops. Never use hibernation or standby modes when you care about security like me. Swap for servers is different.
* OS and application partitions for desktops are never larger than 15G-25G.  There are many, many, many, reasons for this size limit.  Too large causes multiple issues.
* Data partitions can be any size you need. There is a reserved 5% on Linux file systems, so making them too big can waste huge amounts of storage, by default. It is possible to override this.
* I prefer to use LVM. Much more flexible when storage needs to change.  With this setup, LVM doesn't make sense, unfortunately.

You seem to be missing the swap. What happened?

---

### Post by sports fan Matt on 2018-02-12
I think i accidentally deleted it with the post that was with the code tags,

---

### Post by sports fan Matt on 2018-02-12
UUID:

/dev/sda1  ext4             /              15ef628f-f9e4-4b50-9ced-f8445f885a77
/dev/sda2  ext4             (not mounted)  4194fdba-34dc-4f1d-a9fc-bc30419558ba
/dev/sda3  ext4             (not mounted)  7693ed4a-604a-4781-b2b0-5db58406a333

---

### Post by TheFu on 2018-02-12
> **oldfred said:**
> And normally you have to use gparted from live installer.

It is only an issue of the partitions are mounted/in-use.  Without the swap inside the extended partition anymore, there's lots of freedom.

But, as you know, it is often 1000x easier to use alternate boot media so there aren't any mounted/in-use partitions on the disks inside the machine.

288GB for / means that ... 14.4GB is being reserved (5% of the partition) for use only by root. Use tune2fs to see the reserved block amounts. 5% is the default.

---

### Post by sports fan Matt on 2018-02-12
So, how much trouble am I in when I try and upgrade this to 18.04?  Would it be better to start fresh (thinking I have borked the partitions so much I can't reclaim the space) or is this a fixable issue, because I just want one partition plus swap.  I don't plan to test anything else out.

---

### Post by TheFu on 2018-02-12
> **sports fan Matt said:**
> So, how much trouble am I in when I try and upgrade this to 18.04?  Would it be better to start fresh (thinking I have borked the partitions so much I can't reclaim the space) or is this a fixable issue, because I just want one partition plus swap.  I don't plan to test anything else out.

No trouble at all, really.
Swap can be shared by the current Linux and 18.04 when it is there. No need for separate swap.

I would add 3 partitions inside the extended partition.
* 4.1G for swap
* 25G for the OS - /
* IDK - 50G for /home/ (whatever size du -sh /home/ shows + a little more).

then I'd move all the data in sda1 (current /home/ directory) into the new partition for /home.
Then I'd shrink sda1 down to whatever size is 25G or less, assuming it will fit after everything from /home is moved.

This way you could install 18.04 like it was "fresh" into a nice new partition inside the extended partition, but keep using your /home/ which has all your personal settings.  It is nice to have the current OS and the new OS both available.

Linux can boot from partitions inside extended partitions, no problem. I think Windows still has an issue with that, but I really don't know. Haven't dealt with Windows on real hardware in almost 10 yrs now.  

Or you could do nothing.

---

### Post by oldfred on 2018-02-12
If you only want one large partition (which I also do not recommend), you were there before.
Its just with little key icon in gparted, it showed sda1 mounted, so from gparted you could not expand/change sda1.
You need to use live installer to be able to edit sda1.

You still can put swap at the end of the extended partition and shrink the extended back to the size of swap. Then all the unallocated is next to sda1 which you can then expand.

Often better to have separate /home, or data partition.
I prefer new install but normally have at least two / (root) partitions of 25GB or so and then larger data partition.
Then I can have 16.04 in one partition and 18.04 in other. That also then is better than the typical houseclean as new install starts from scratch.
And then you can check that your back up procedures work, as you still have old install to find something you missed.

---

### Post by TheFu on 2018-02-12
> **oldfred said:**
> If you only want one large partition (which I also do not recommend), you were there before.
Its just with little key icon in gparted, it showed sda1 mounted, so from gparted you could not expand/change sda1.
You need to use live installer to be able to edit sda1.

You still can put swap at the end of the extended partition and shrink the extended back to the size of swap. Then all the unallocated is next to sda1 which you can then expand.

Often better to have separate /home, or data partition.
I prefer new install but normally have at least two / (root) partitions of 25GB or so and then larger data partition.
Then I can have 16.04 in one partition and 18.04 in other. That also then is better than the typical houseclean as new install starts from scratch.
And then you can check that your back up procedures work, as you still have old install to find something you missed.

+1 - golf clap for oldfred's posts.  Very nice.

---

