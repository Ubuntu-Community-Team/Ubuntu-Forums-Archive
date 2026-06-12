---
title: "Cloning Storage disk to replacement HD"
date: 2013-01-14
forum: General Help
---

### Post by SuperFreak on 2013-01-14
I just purchased a new WD Black 4TB hard drive which I intend to use as my Storage disk. I just want to make sure I am going about this the right way, that is copying all the data from my old Storage drive to the new WD drive. This how I intend to do it.
1) Install WD drive in spare bay.
2) Unmount drive and using Gparted format WD drive EXT4
3) Using GParted copy all files from old Storage drive to new
4) Remove old drive and plug sata cable for new drive in old sata connection on Motherboard
5) Run blkid on terminal and copy UUID of new Storage drive
6) Replace UUID of old Storage drive in fstab with new UUID
7) Reboot


Does this seem reasonable

---

### Post by Herman on 2013-01-14
Wow, a 4 TB drive? I haven't seen or heard of one that big yet where I live. 
Yes, your proposed procedure looks okay to me.
You can optionally set a file system label with GParted too, file system labels are quite useful.

EDIT: "3) Using GParted copy all files from old Storage drive to new"
How come you want to use GParted for copying files? I would just use a cp command or simply copy and paste.

---

### Post by SuperFreak on 2013-01-14
Thanks for your reply Herman.
Yes it is a massive drive and presently I only have 1 TB of data. The drive is warrantied for 5 years so within that time frame I expect to fill quite a bit of it with data (future proofing)
To answer your question I don't know if it makes any difference how I copy the data, I had thought of using Grsync or copy and paste as you mentioned(which is my usual method with new drives) , but I thought in the end that GParted might be the safest way of doing it. But I have no evidence of this and it may all be the same.

---

### Post by tgalati4 on 2013-01-14
If you really want to clone the drive, try:

```
sudo cp /dev/sda /dev/sdb
```

This assumes that /dev/sdb is larger than /dev/sda (and it should be at 4 TB).  Use Gparted to expand the existing partition, or make new partitions past the original data set.  Use blkid to get the UUID and fix grub entries and /etc/fstab entries as needed to reflect the new drive.  Not sure where else UUID is used, but you will find out soon.

---

### Post by oldfred on 2013-01-14
the author of gdisk posted here once that you should never use dd to copy a MBR partition to a gpt drive. Something about internal partition structures. It may work for an entire drive. Not sure if then gparted would be ok or not?

I would just use cp or rsync. Some have posted that rsync is quicker. What format is partition(s) as that can make a difference. You have to add parameters to either cp or rsync if you want to preserve ownership & permissions. 

Also do you really want one massive partition? file issues on partitions could mean fsck or chkdsk take weeks not days.

---

### Post by SuperFreak on 2013-01-14
Thanks OldFred
Partitioning the drive into 2 or 3 partitions probably makes sense. I use Grsysnc which is based on rsync. That should work right?
The drive will be EXT4 and existing drive is EXT4 also

---

### Post by oldfred on 2013-01-14
I have not used grsync. I would expect it has a way to in effect add the extra parameters to maintain ownership & permissions. 

Rsync has so many parameters it can be very confusing. I found some suggestions on what to use & they seem to work for my backups.

---

### Post by SuperFreak on 2013-01-14
So just to reiterate my plan. Once the files are copied over and I have removed the old drive, using Blkid to find the new drives UUID and inserting this in where the old drive was labelled in FSTAB will set me up. Now if I in fact split the drive into 2-3 partitions then blkid will find several UUIDs which I will need to include in FSTAB. Is that accurate?

by the way Grsync provides quite simple graphical choices including keeping file ownership and permissions

---

### Post by Herman on 2013-01-14
> Now if I in fact split the drive into 2-3 partitions then blkid will  find several UUIDs which I will need to include in FSTAB. Is that  accurate?Yes, if you add them to /etc/fstab they will be automatically mounted on every reboot. 
Otherwise you can leave them unmounted and mount them when required by starting your file browser and going 'Go', 'Computer', and clicking on the icon for the partition you want.

EDIT: Thanks for the info on [Grsync]("http://www.opbyte.it/grsync/") too, by the way, by coincidence I was just at this moment looking for something like that and will install it and start using it myself. It looks like just what I want.

---

### Post by SuperFreak on 2013-01-14
Most welcome...thanks for your help

---

### Post by miklcct on 2013-01-15
Here is what I did a few days ago to copy my entire OS from an old drive to a new drive:

1. Install the new drive
2. Boot an external medium
3. Partition the new drive
4. Create an ext4 file system on my target partition
5. Mount both the old system partition and the new one
6. Do a "cp -ar" to copy all data
7. Modify /etc/fstab in the new system FS to use the new one
8. Reinstall GRUB in the new system
9. Shut down the machine
10. Remove the old drive

---

### Post by sdowney717 on 2013-01-15
I cloned an entire ubuntu onto a new drive using gparted cp, fstab.

[http://ubuntuforums.org/showthread.php?t=2097275](http://ubuntuforums.org/showthread.php?t=2097275)

It worked out and fairly quick to copy a lot of files.
Quicker than an install since no updates had to be downloaded again and I had a system already configured.

---

### Post by Herman on 2013-01-15
Has anybody used GParted for copying a partition from one disk to another?

I have used GParted many times in the past for copying partitions from place to place on the same disk but I'm not sure about copying from one disk to another.
The interesting thing about copying and pasting to the same disk with GParted is the  UUID number is preserved in the new copy and the old copy is given a different UUID, so no need to edit /etc/fstab if you're deleting the old partition. EDIT: Or if you want to keep the old partition as a backup the UUIDs won't clash.

For copying a partition from one disk to another I have always needed to use other methods, but this functionality may have been added to GParted since last time I tried.

---

### Post by SuperFreak on 2013-01-15
GParted was my original thought on how to clone my drive, but I am undecided if I should use GParted or Grsync, because of comments OldFred made in this thread about copying GPT partitions.

> the author of gdisk posted here once that you should never use dd to copy a MBR partition to a gpt drive. Something about internal partition structures. It may work for an entire drive. Not sure if then gparted would be ok or not?


---

### Post by oldfred on 2013-01-15
I found the reference which may or may not offer more clarity.

       Do not use dd to copy partition with gpt due to unique guids & UUIDs post #12
[http://ubuntuforums.org/showthread.php?t=1680929](http://ubuntuforums.org/showthread.php?t=1680929)

---

### Post by SuperFreak on 2013-01-15
> I found the reference which may or may not offer more clarity.


I am afraid I am still not sure about my particular case. First I am copying a data drive to a data drive neither of which have system files, although there is a SWAP partition on the old data drive. I am using GPT on both drives. Also my computer has an UEFI motherboard which through your help ,OldFred and others , now boots from the EFI partition. I would guess from the linked post that under these circumstances I could use GParted to copy from one drive to the other and FSTAB would automagically update without intervention.
I am not sure if there is any advantage to copying using GParted so so far Grsync is probably the way I will go.

---

### Post by Herman on 2013-01-15
I tried an experiment using a 512mb flash memory stick with a reiserfs partition in it about 90% full of files and a 1 GB flash memory containing an empty FAT32 partition occupying the whole disk.
Both flash memory drives have msdos MBRs.

I copied the 512mb partition from the first disk and pasted it into the 1 GB partition in the second disk using GParted 0.11.0 in Ubuntu Precise Pangolin 12.04.

The result is I have a clone of all of the files from the original 512 MB partition and now they're in a 1 GB reiser file system in the larger disk with the files occupying around 45% of the space . 
I ran blkid and this time both copies of the file system have the same UUID.

---

### Post by SuperFreak on 2013-01-16
I know I marked this as solved and it is. I just wanted to say  I stuck to my original plan with 2 modification based on what OldFred said earlier. I partitioned my new hard drive into 2 parts (3 if you include SWAP) and I used Grsync to copy my files, It seems to be working fine at this point. Thanks for everyones help:D

---

### Post by oldfred on 2013-01-16
Glad to know it worked. :)

---

