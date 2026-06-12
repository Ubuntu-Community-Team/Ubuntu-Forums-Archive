---
title: "Warning on unallocated space"
date: 2014-11-20
forum: General Help
---

### Post by sports fan Matt on 2014-11-20
59.54 GiB of unallocated space within the partition.
To grow the file system to fill the partition, select the partition and choose the menu item:
Partition --> Check.

When I try to resize and grow the partition, I can't..I assume it has something to do with the mounting? (I was trying to install MINT for the 4th time, but gave up and want that space for Ubuntu 14.04

---

### Post by Impavidus on 2014-11-20
So, what do you get when you "choose the menu item: Partition --> Check"?

---

### Post by sports fan Matt on 2014-11-20
Greyed out menu and when I try to move EXT 4...nothing can be moved

---

### Post by mcduck on 2014-11-20
You can't resize the partition, there's no unpartitioned space on the drive. And you don't have to, the message is telling you that there's unallocated space inside that partition. So what you'll want to do is grow the *filesystem within that partition*. And yes, you will need to make sure that filesystem is unmounted before you grow it to use all of the partition. Since it seems to be your root filesystem, you'll need to do it from a live-CD/USB.

---

### Post by sports fan Matt on 2014-11-20
grow the filesystem within that partition..if it's the extended partition there is no option except "manage flags" and the other partition im not sure what to do..format it to ext 3 maybe? (all withion the live cd of 12.04)

---

### Post by oldfred on 2014-11-20
Is not the extended partition, but your / (root) partition. 
How did you create file system? Manually and you did not choose defaults to fill entire partition?

You need to use live installer so partition is unmounted and follow the instructions your screen shows.

---

### Post by yancek on 2014-11-20
You can't do anything with sda3, the Extended partition and there is no reason to.  What you are going to have to deal with is sda5 which is a logical partition within sda3 as is sda6, your swap partition.  I've never seen this before and am wondering how you accomplished it.

---

### Post by sports fan Matt on 2014-11-20
I'm in the live installer as we speak-I can delete (which obiviously I do not want to do), Resize and move (how much/where?) or format. (Main thing is trying to save my Windows 7 partition which will not boot)

---

### Post by sports fan Matt on 2014-11-20
What would happen if sda6 was swapped off?

---

### Post by sports fan Matt on 2014-11-20
This is radical, but since the partitions are pretty messed up, wouldn't the easiest thing to do be reinstalling Ubuntu? (removing sda6, sda5, and extending sda 2) although im not sure if my Windows 7 partition is there

---

### Post by oldfred on 2014-11-20
This is why my rsync script to backup  my /home, and list of installed apps includes running the script version of bootinfoscript. That way I have current documentation of my partitions and what is installed where. Then I can recreate system exactly the same, although I might not want to?

---

### Post by mcduck on 2014-11-21
> **sports fan Matt said:**
> This is radical, but since the partitions are pretty messed up, wouldn't the easiest thing to do be reinstalling Ubuntu? (removing sda6, sda5, and extending sda 2) although im not sure if my Windows 7 partition is there

There's nothing wrong with thre partitions.

It's just that the fielsystem inside the partition isn't using all space avaiable to it (can happen, for examply if you copy an image of a smaller filesystem into a larger partition). Ext filesystem can be grown to fill available space using the *resize2fs* command.

As far as I remember, if you don't give it any size as parameter, it will automatically grow the filesystem to match the partition size.

So, just running this should fix things. (You might need to do it from a live system, but Ext4 allows surprisingly much tweaking even on mounted filesystems so it *might* even be possible to do it while using that partition:
```
sudo resize2fs /dev/sda5
```

---

### Post by yancek on 2014-11-21
I don't see any windows except for the 100MB 'System Reserved' at the beginning of the drive.  The largest partition, sda2 is ext4 so I don't know what happened with your windows but it doesn't seem to exist.

---

### Post by sports fan Matt on 2014-11-22
I figured that so reinstalled last night....those 175 updates initally took forever

---

