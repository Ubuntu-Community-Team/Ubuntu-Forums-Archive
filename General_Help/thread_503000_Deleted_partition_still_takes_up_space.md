---
title: "Deleted partition still takes up space"
date: 2007-07-17
forum: General Help
---

### Post by ExileAmongYou on 2007-07-17
I tried dual booting Ubuntu for a while, and didn't like it so went back to Windows XP. The problem is that the partition I created for Ubuntu is still taking up space on my drive. 
I have about a 120GB hard drive, and I set up a 15GB partition for Ubuntu. When I deleted the ext3 partition though, I didn't get any space back. Instead, windows explorer now tells me that my hard drive is 105GB, with 20 GB free space (i.e. 85GB used, which is about right), while the Gnome partition manager tells me it's 120 GB, with 20GB free space (100 GB used, which isn't right). 
Anyone have any idea how I can get that space back?

---

### Post by Outrunner on 2007-07-17
If you formatted your Ubuntu partition, you still need to resize your Windows partition to include the unallocated space(that's what it's called now if you simply deleted the partition). I don't knnow how, or if you can do this with the preinstalled Windows utilities, so I'm going to recommend the Gparted LiveCD(check my signature). Download the latest one and burn it to a CD as an image(just like you did with Ubuntu). Now reboot and insert your Gparted LiveCD. Use the automatic config, first option, if I recall. Now, when it finishes booting, right click on your Windows partition and and click Resize. Should be straight forward from there, but if you still need help, come back and ask :)

---

### Post by ExileAmongYou on 2007-07-17
Would Gparted be the one that's on the Ubuntu Live Install CD? If so, that's the program that's telling me that the partition is *already* using up the entire disk, but that I've used up 15GB more data than I actually have.

---

### Post by Outrunner on 2007-07-17
> **ExileAmongYou said:**
> Would Gparted be the one that's on the Ubuntu Live Install CD

That's the one. But I think there's a bit of confusion going on on my part. I'm not sure I understand what's happening. 

You have  your Windows partitions and you did... what exactly with your Ubuntu partitions - swap and / (root) probably? Or maybe it would be easier if you took a screenshot while having GParted open.

---

### Post by ExileAmongYou on 2007-07-17
As far as I can remember, I formatted both my Ubuntu partitions, then resized the windows one to take up all of the drive, then restored the master boot record using the windows xp cd.

Now that I think about it though, it's possible that I might have formatted the ubuntu partitions, then restored the master boot record without resizing the windows partition. Would that explain it?

If I still can't work this out, I'll get a screenshot for you, but I'm pretty sure Gparted just shows that I have one 120GB NTFS partition, with only 20GB free space, when I should have 35GB free.

---

### Post by Outrunner on 2007-07-17
It should be easier to fix if you upload a screenshot here ;) no need to take too much time with this ehh? Unless, of course, it has me and everyone else here bummed too :-k

---

### Post by gusanto on 2007-07-17
Hi there,
I am a newbie.
I cloned my 40 GB HD with Windows XP on it successfully into a 200 GB new HD. Then I created a 40 GB FAT32 Extended partition and allocate it for one logical partition. Then I created 30 GB EXT3 pirmary partition (I followed a page how to dual boots, forgot where).  When I want to create 2GB primary Linux swap partition, GParted told me it was not able to create more than 4 primary partitions (in fact I only added 1 extended and 1 primary partition from my original HD). It seemed that there is one partition (very small, 30MB called DellUtilty), which is also primary. Then I deleted my FAT32 extended partition then I created 2 GB primary Linux swap. I did my partion process using Ubuntu Feisty CD (GParted LiveCD and Rescue LiveCD both failed to start the X window even though I tried to configure it manually according its instruction).
I want to use 50 GB of the unallocated partition for storing data files that both Ubuntu and Windowds XP can have access to read and write. (I will leave the rest of unallocated partition for future use).
Please give me some direction.
Thanks.

---

### Post by az on 2007-07-17
> **ExileAmongYou said:**
> As far as I can remember, I formatted both my Ubuntu partitions, then resized the windows one to take up all of the drive, then restored the master boot record using the windows xp cd.

Now that I think about it though, it's possible that I might have formatted the ubuntu partitions, then restored the master boot record without resizing the windows partition. Would that explain it?

If I still can't work this out, I'll get a screenshot for you, but I'm pretty sure Gparted just shows that I have one 120GB NTFS partition, with only 20GB free space, when I should have 35GB free.


You may also have resized the windows partition, but not resized the filesystem on it.  
You can go back and resize the filsystem to fit the whole partition.

---

