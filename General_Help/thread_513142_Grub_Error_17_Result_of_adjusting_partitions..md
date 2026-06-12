---
title: "Grub Error 17: Result of adjusting partitions."
date: 2007-07-30
forum: General Help
---

### Post by suupaabaka on 2007-07-30
I recently got into Ubuntu full swing, and decided to reallocate space from my NTFS partition to ext3. Partition Magic did the job, but when I restarted the computer, I found that dratted Grub Error 17. Following some advice from these forums, I booted up the live cd and tried the advice on this page.

[http://ubuntuforums.org/showthread.php?t=224351&highlight=grub+error+17](http://ubuntuforums.org/showthread.php?t=224351&highlight=grub+error+17)

However, I couldn't even do

```
find /boot/grub/stage1
```

since it simply returned "Error 15: File not found."

I would greatly appreciate any advice as to how I should proceed from here.

---

### Post by logos34 on 2007-07-30
Look here:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#17](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#17)

Get supergrub cd or boot from your live cd and check /boot/grub/menu.lst

---

### Post by merlinus on 2007-07-30
If you re-sized a partition, then certainly the UUID has changed.

You can either boot from supergrub as logos34 suggested, or boot from the ubuntu live ced, mount your linux partition manually (use sudo fdisk -l to find it), and blkid will give the new UUID.

Then change it accordingly in /boot/grub/menu.lst.

-merlin

---

### Post by suupaabaka on 2007-07-31
Thanks for the quick replies, guys. My Linux-savvy friend dropped around this morning to get a lift to uni, and offered to look at my problem in return. 

It turns out that my only option was to reinstall Linux; Partition Manager had done something icky to my Linux partition. From now on, any reshuffling of free space will be done from Linux.

Thanks again!

---

### Post by TBerben on 2007-07-31
The first thing I did after installing Feisty is to modify fstab to use the normal device names in stead of UUIDs... I ran into a similar problem after resizing a spare partition...

---

