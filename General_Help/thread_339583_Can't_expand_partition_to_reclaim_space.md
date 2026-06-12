---
title: "Can't expand partition to reclaim space"
date: 2007-01-16
forum: General Help
---

### Post by richardq on 2007-01-16
Hi,

I've got 2 160GB drives in my machine. One of them had a 120GB ntfs partition with some data on it from before I switched to linux. The remaining 40GB was my /home partition.

I booted into XP (it's a dual boot machine) and deleted a lot of the data on that ntfs partition. I used partition magic to reduce the size of it to about 50GB . I wanted to resize my /home partition to reclaim the remaining space (about 60GB). But all I could get Partition magic to do was reduce the ntfs partition size and leave the reclaimed 60GB as unused space. It wouldn't resize the ext3 home partition to gain the 60. It threw a #702 error whatever that means.

I then booted into Ubuntu (Edgy) and ran GParted. I select the 40GB ext3 partition but resizing it is greyed out. I can create a new /ext3 partition to use the 60GB of reclaimed space but can't figure out how to mount it (can I do that from GParted?)

Ideally of course I just want to expand the /home partition from 40GB to 100GB but how can I do it?

I'm pretty much a newb when it comes to partitioning so be gentle. ;)

---

### Post by bodhi.zazen on 2007-01-16
You can not resize a partition if it is mounted.

Adn you can not add free space in front (to the right) of a partition....

So

boot the the Ubuntu desktop CD

Run gparted.

You will see:

ntfs
free space
ext3

Move the ex3 partition so that you have

ntfs
ext3
free space

Now resize the ext3 partition

Watch that the number does not change, else you will need to update /etc/fstab

---

### Post by richardq on 2007-01-16
> **bodhi.zazen said:**
> 

boot the the Ubuntu desktop CD

Run gparted.

You will see:

ntfs
free space
ext3

Move the ex3 partition so that you have

ntfs
ext3
free space

Now resize the ext3 partition


I booted the ubuntu cd and ran gparted. I do indeed have ntfs--unused--ext3.  However, I can only resize the ext3 partition (which then leaves it unchanged position-wise). I can't seem to move it to the left.

Any ideas?

---

### Post by bodhi.zazen on 2007-01-16
Well, if you can resize the ext3 and reclaim the space I guess ther is no need to move it.

If you can not you need to move the partition. In Gparted do you see the copy and paste buttons ?

Create an ext3 partition same size as your current ext3, then copy, then delete, then resize.

Of course you have backed up your data I presume :p

Oh, and if the number of the partition changes you will need to update or re-install grub (/boot/grub/menu.lst) and fstab (/etc/fstab) on your Ubuntu partition 

**[color=red]From the Live CD or your Ubuntu partition will not boot**[/color]

Just though I would warn you about the back up and boot issues :p

---

### Post by comer on 2008-07-07
I think there is few software could resize EX3 partition:

paragon  [http://www.partition-manager.com/](http://www.partition-manager.com/) 
It's free,but may not work on linux.

easeus partition manager 
I download from brother soft 
[http://www.brothersoft.com/easeus-partition-manager-51814.html](http://www.brothersoft.com/easeus-partition-manager-51814.html)

It worked OK, but failed when i tried to  merge partition. so i have to allocated the free space to another partition. 
Partition magic may merge two partitions which will cost you $69.95

cute partition manager
It's free on giveawayoftheday today(within 24 hours)
[http://www.giveawayoftheday.com/freeware/partition_download.shtml](http://www.giveawayoftheday.com/freeware/partition_download.shtml)

---

