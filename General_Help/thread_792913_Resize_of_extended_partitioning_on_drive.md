---
title: "Resize of extended partitioning on drive"
date: 2008-05-13
forum: General Help
---

### Post by briandu on 2008-05-13
Problem statement

I have drive with primary and extended then primary and primary.

I wish to resize my extended (which had 7 logical partitions therein) as I can remove the second last primary partition so freeing up space.

Situation:
I used GParted and yes I can delete the primary partition and I can change the size of logical partitions but I **cannot** seem to increase (resize) my extended partition.

Question:
Does GParted support resizing of extended partitions?

---

### Post by briandu on 2008-05-14
Bump!!!!

Alternatively, has anyone moved a system to another hard drive (same model size) BUT with different partitions and/or rearranged partitions?

Any advice?

---

### Post by mikewhatever on 2008-05-14
Is there some unallocated space to enlarge the extended partition to? If there isn't, then I don't think you'd be able to resize it before deleting the second primary partition.

---

### Post by briandu on 2008-05-14
As described in post 1 I have the space however gparted will not allow me to change the extended size. Oh yes, I mean the deleted primary partition is in the contiguous space after the extended partition NOT after it (otherwise the remaining primary partition would be in the way)

Even if I boot from cdrom I cannot change it.

---

### Post by mikewhatever on 2008-05-14
What I gather from post #1 is that you have free space allocated to other partitions. The point to understand here is you can't enlarge a partition over another one, it has to be over unallocated space. Hence the question. Do you have any unallocated space?

---

### Post by briandu on 2008-05-14
Well I gave up and re-installed on the new hard-drive - I am just about finished and hopefully I can pickup all the settings.

thx

---

### Post by mshumer on 2008-05-28
I have the same problem and I'm trying to fix without reinstalling AGAIN. I have a 100GB drive with two partitions: sda1 which has my system files loaded and sda2 which is a logical (extended) partition. My /home directory is there. I've backed up all those files and resized my /home partition. Now I want to reduce the size of the logical partition so I can grow sda1 to take up the space. gparted won't do anything except offer to make a new file system in the unallocated space. I'm tempted to delete the logical part and recover my backed up data but I'd rather not if possible. It looks like this:
|<--sda1---->||<--unallocated-->||<--/dev/sda5-->||<--swap->|

---

