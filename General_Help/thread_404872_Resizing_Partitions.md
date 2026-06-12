---
title: "Resizing Partitions"
date: 2007-04-09
forum: General Help
---

### Post by Exillo on 2007-04-09
Hi,

I dual boot Ubuntu 6.10 and XP Home and have found I want to use Ubuntu much more than I thought. 

I want to make my Ubuntu partition larger and my XP partition smaller (my XP is split into 5 partitions already).

I have partition magic 8.0 on XP but I've had bad experiences with partitioning in the past with my old computer and wanted to ask you all. 

Thanks in advance! =) :KS

---

### Post by bran on 2007-04-09
> **Exillo said:**
> Hi,


I want to make my Ubuntu partition larger and my XP partition smaller (my XP is split into 5 partitions already).

I have partition magic 8.0 on XP but I've had bad experiences with partitioning in the past with my old computer and wanted to ask you all. 

Thanks in advance! =) :KS

Gparted can be installed through synaptic or run from the live CD.  works well and easily.

---

### Post by Exillo on 2007-04-09
GParted looks good but it won't let me resize (or most other tasks) anything. :/

---

### Post by bran on 2007-04-09
> **Exillo said:**
> GParted looks good but it won't let me resize (or most other tasks) anything. :/

how odd. how are you invoking it?

---

### Post by foxmulder881 on 2007-04-09
There is no reason GParted shouldn't be able to resize your partitions.

---

### Post by Exillo on 2007-04-09
The enter my password when I open it but it doesn't let me resize anything. The ext3 is Ubuntu (I think at least :p) 

Screenshot: [http://i15.tinypic.com/3zhgj6w.png](http://i15.tinypic.com/3zhgj6w.png)

---

### Post by bran on 2007-04-09
you would need to unmount the partitions or call the utility from the live cd.   latter is my usual choice  for playing with my linux partition.  

scary number parts there for me:popcorn:

---

### Post by Exillo on 2007-04-09
Yeah, my harddrive is partitioned annoyingly/unlogically. =/

And I've kinda lost my Ubuntu CD so that my be tricky.

What does unmounting do? Doesn't that mean the sda* would dissapear?

---

### Post by robenroute on 2007-04-09
A mounted partition cannot be resized (which is not exactly true, as there is an online resize tool, but that's a wee bit too tricky). GParted (at the moment) only supports operations on partitions that are not "live", so to speak; you'll have to unmount the partition in question first.

If the partition you'd like to resize is your main Ubuntu partition, you can't resize that particular partition as it is used by the Ubuntu system (it contains your active Linux/Ubuntu installation). That's why you'll have to use a live distro (Ubuntu Live CDs don't come with GParted!) like GParted Live, or System Rescue.

Unmounting partitions, makes those partition disappear indeed, but only as seen from the system your running. Those partitions are still there, but the active system can't access the file system on them.

When resizing partitions, it's good to keep in mind that the file system (ext2, etx3, etc.) is a separate thing from the partition. Say you want to shrink a partition, you'll have to shrink the file system first (and in case of an ext3 file system, you'll have to disable the journalling first), before you can actually reduce the size of the partition. After resizing is complete, you'll want to turn on the journalling feature again (making it ext3 again).

Just make sure to back up your data before fiddling around with partitions. You wouldn't be the first nor the last person to lose valuable data....

Good luck.

P.S.1   If anything goes wrong, the testdisk utility is indispensable.
P.S.2   [Gparted]("http://gparted.sourceforge.net/") does the file system size adjustments for you, before/after the resizing of the partition itself. It is, however, good to understand that partitions and filesystems are separate things.

---

### Post by bran on 2007-04-09
> **robenroute said:**
> 
 (Ubuntu Live CDs don't come with GParted!) like GParted Live, or System Rescue.

.

I am glad you caught me being wrong.... must have installed it to the live session.

---

### Post by Exillo on 2007-04-09
Thanks for clearing things up guys, since I don't seem to need to know anything other than using a partition editor (and what you guys have said) I'll just go into XP and use partition magic. =)

---

### Post by psychok7 on 2007-04-12
IS it safe to use partition magic then from windows for a linux partition?? i was reading all the posts, and i realized that the explanations that are being given are quite complicated for a newbie..partition magic is a much simpler program. can anyone assure me that it is compatible with the ext3 from ubuntu??

---

### Post by psychok7 on 2007-04-14
i tried with partition magic and it works perfectly

---

