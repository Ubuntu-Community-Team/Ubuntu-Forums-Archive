---
title: "Merging Unallocated space to starting of an extended partition."
date: 2013-09-01
forum: General Help
---

### Post by 7Starphy on 2013-09-01
I am using Ubuntu 12.10 which is on a dual boot with Windows 7. I initially had 30 GB for Ubuntu ,but I decided I need more , now I booted Ubuntu from its Live CD ,used GParted , shrunk Windows partition by 50 GB ,so I got 50GB-unallocated space. Now I want to merge that with Ubuntu's partition (extended) . But I keep getting an "overlapping partition" error , and I am not able too identify where the overlapping is happening. Can anyone please help me out here ?

---

### Post by ibjsb4 on 2013-09-01
You must first move the free space to sda4 and then to sda5.  Is that what your doing?

---

### Post by 7Starphy on 2013-09-01
> **ibjsb4 said:**
> You must first move the free space to sda4 and then to sda5.  Is that what your doing?

I am not able to move the free space from to sda4. That is , I am not able to merge sda4 with unallocated. I keep getting an error like "Overlapping partitions" . I am not able to see where the overlap is .

---

### Post by TheFu on 2013-09-01
30G should be plenty for / and /usr (OS and programs).
Rather than merging, why not mount the new partition space under /home and split the OS/Apps from that?  It is a **"best practice"** after all.

Looking at your Gparted, it seems that you have already used the 4 allowed primary partitions, so you'll need to grow the Extended partition (sda4) to the left. Does that not work? Should be a mouse drag-n-drop + "apply" thing.  Then I would create a new logical partition for /home inside the extended partition. That's just me.

It should go without saying, but you'll want a **100% complete, perfect, backup** of everything on this disk before you start - including the partition table.  I'd use **ddrescue** or **partimage** to handle that, if it were me.

---

### Post by 7Starphy on 2013-09-01
> **TheFu said:**
> 30G should be plenty for / and /usr (OS and programs).
Rather than merging, why not mount the new partition space under /home and split the OS/Apps from that?  It is a **"best practice"** after all.

Looking at your Gparted, it seems that you have already used the 4 allowed primary partitions, so you'll need to grow the Extended partition (sda4) to the left. Does that not work? Should be a mouse drag-n-drop + "apply" thing.  Then I would create a new logical partition for /home inside the extended partition. That's just me.

It should go without saying, but you'll want a **100% complete, perfect, backup** of everything on this disk before you start - including the partition table.  I'd use **ddrescue** or **partimage** to handle that, if it were me.

Yes , I need to first merge the Unallocated with sda4 (I am not able to do that ,it is throwing an error at my face) , if it had allowed me to do that , I would have merged the unallocated (50 GB) with sda5 , so that I totally get 80 GB. (Yes ,I will have to resize sda5 to the left for which it complains ,GRUB might get uninstalled ,but I guess re-installing GRUB is not that big a problem )

I just want some 80 GB Hard-drive space for my Ubuntu . I am really not specific about "how" it is done.

---

### Post by TheFu on 2013-09-01
[LIST=1]
[*]First, you need to boot off a flash or liveCD with **gparted**. Check?  We cannot modify any partitions while they are in-use.
[*]Next, select the drive you want to modify.
[*]Next, select the partition 
[*]and right click on it, then select "move/resize"
[/LIST]

That should start the wizard.  If that doesn't work, I'm out of ideas.  When I do stuff like this, I always align on cylinder boundaries too.

---

### Post by Quackers on 2013-09-01
What is the output of the terminal command ```
sudo fdisk -l
``` The last digit is a lower case L not a 1.

Sometimes an extended partition can be listed wrongly in the partition table so it looks like it is overlapping another partition. In these circumstances gparted won't allow any changes so that no further damage is done.

---

### Post by 7Starphy on 2013-09-02
> **TheFu said:**
> 
[LIST=1]
[*]First, you need to boot off a flash or liveCD with **gparted**. Check?  We cannot modify any partitions while they are in-use.
[*]Next, select the drive you want to modify.
[*]Next, select the partition
[*]and right click on it, then select "move/resize"
[/LIST]

That should start the wizard.  If that doesn't work, I'm out of ideas.  When I do stuff like this, I always align on cylinder boundaries too.

I was able to shrink sda3 partition by 50 GB and apply that rule successfully using gparted (yes,I am doing it from a Ubuntu LiveCD) . What I am not able to do is merge the unallocated space (which is between sda3 and sda4) with sda4 , so that my Ubuntu gets roughly 80 GB disk space. sda4 contains sda5 and sda6 (where sda5 is 27GB of my Ubuntu and 3 GB is Linux Swap).

When I merge sda4 and unallocated , I get the error - " Doesn't satisfy all constraints of the partition - Overlapping partitions "

---

### Post by 7Starphy on 2013-09-02
> **Quackers said:**
> What is the output of the terminal command ```
sudo fdisk -l
``` The last digit is a lower case L not a 1.

Sometimes an extended partition can be listed wrongly in the partition table so it looks like it is overlapping another partition. In these circumstances gparted won't allow any changes so that no further damage is done.

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6c48a710


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63       80324       40131   de  Dell Utility
/dev/sda2   *       81920    29044735    14481408    7  HPFS/NTFS/exFAT
/dev/sda3        29044736   806342655   388648960    7  HPFS/NTFS/exFAT
/dev/sda4       912336894   976771071    32217089    5  Extended
/dev/sda5       912336896   968585215    28124160   83  Linux
/dev/sda6       968587264   976771071     4091904   82  Linux swap / Solaris
```

---

### Post by TheFu on 2013-09-02
Well, looks like it is time to backup everything, delete sda4/5/6 and repartition the Extended partition.

---

### Post by 7Starphy on 2013-09-02
> **TheFu said:**
> Well, looks like it is time to backup everything, delete sda4/5/6 and repartition the Extended partition.

I am sorry for this noob-like question , what is the difference between Deleting and Formatting my partition ? Does Deleting the partition lead to loss of data ?

---

### Post by TheFu on 2013-09-02
> **7Starphy said:**
> I am sorry for this noob-like question , what is the difference between Deleting and Formatting my partition ? Does Deleting the partition lead to loss of data ?

Both will remove all data.  You need to delete all those partition, then you can recreate them in a different place on the HDD. Backup everything you want to retain.  Ubuntu has a backup guide (google "ubuntu backup") and select the link(s) that have ubuntu.com in them.  Or [http://www.howtogeek.com/108869/how-to-back-up-ubuntu-the-easy-way-with-dj-dup/](http://www.howtogeek.com/108869/how-to-back-up-ubuntu-the-easy-way-with-dj-dup/) explains.

There are hundreds of reasons to have good backups - data loss, data corruption, viruses, human error, ... hundreds of others.

---

### Post by Quackers on 2013-09-02
I suspect gparted won't allow you to delete a partition as the overlapping partition error is likely to crop up again.
I can't see anything wrong with your partitions but it seems likely to me that your extended partition is either overlapping another partition or appears in the partition table to be overlapping something. This happens from time to time with extended partitions, depending on what program created it. Fixparts will re-write the extended partition boundaries, hopefully correcting the error.
My suggestion would be to download Fixparts (the .deb file for your acrchitecture - ie 32 bit/64 bit) from here
[http://sourceforge.net/projects/gptfdisk/files/gptfdisk/0.8.7/fixparts-binaries/]("http://sourceforge.net/projects/gptfdisk/files/gptfdisk/0.8.7/fixparts-binaries/")
 and run it following the guide in the link below.
[http://www.rodsbooks.com/fixparts/]("http://www.rodsbooks.com/fixparts/")

Once run inside Ubuntu you may then be able to adjust your partitions.

---

### Post by 7Starphy on 2013-09-02
> **Quackers said:**
> I suspect gparted won't allow you to delete a partition as the overlapping partition error is likely to crop up again.
I can't see anything wrong with your partitions but it seems likely to me that your extended partition is either overlapping another partition or appears in the partition table to be overlapping something. This happens from time to time with extended partitions, depending on what program created it. Fixparts will re-write the extended partition boundaries, hopefully correcting the error.
My suggestion would be to download Fixparts (the .deb file for your acrchitecture - ie 32 bit/64 bit) from here
[http://sourceforge.net/projects/gptfdisk/files/gptfdisk/0.8.7/fixparts-binaries/](http://sourceforge.net/projects/gptfdisk/files/gptfdisk/0.8.7/fixparts-binaries/)
 and run it following the guide in the link below.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

Once run inside Ubuntu you may then be able to adjust your partitions.

Can you tell what I should do in my case ,with respect to Fixparts ? Like what MBR command I should give to fix my partition table ?

---

### Post by TheFu on 2013-09-02
@Quackers - Do you think not using cylinder alignment during initial partitioning might have cause this?  I don't know, but I'm running an InstallFest in a few weeks and want to be ready as best I can.

---

### Post by Quackers on 2013-09-02
I know of no terminal commands that can correct a partition table (though such a thing probably exists).

If you're using Ubuntu 32 bit download the .deb file for 32 bit and similarly for 64 bit if that's the architecture of your Ubuntu system.
Then follow the directions in that second link. Basically you just run Fixparts and then write the new data to the partition table - a 5 minute job and no data should be lost.

I have used Fixparts in the past for the exact same problem you are having. The creator of the utility used to be a member here.

---

### Post by Quackers on 2013-09-02
@TheFu
no, I suspect not. For some reason this problem can arise from time to time with an extended partition. It seems to be improperly written in the partition table, but I have no idea why. Fixparts can fix that problem in a jiffy.
I do usually leave just 1MB gap in between partitions as a separator and so the boundaries can align properly but I don't think that's actually a requirement.

---

