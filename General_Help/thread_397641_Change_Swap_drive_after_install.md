---
title: "Change Swap drive after install?"
date: 2007-03-30
forum: General Help
---

### Post by Funzo22 on 2007-03-30
I just switched one of my friends to ubuntu as she was having loads of problems with windows since her computer was too slow for anti-virus protection...

 I only had one problem, her partition scheme was pretty cracked out, she had a 20gb hard drive split into 3 partitions + the system, and all NTFS, not something I want to mess around with in ubuntu.

During installation time, I wiped the system partition and used it as the ubuntu boot partition and I resized one of the extra partitions to make room for a swap, however now my plan is to back up all the stuff on those 3 extra partitions and delete them and make the hard drive into 1 big partition + swap.

The problem is, I am not sure how it is going to work with the swap, the partition scheme is roughly like this:

1. 5gb Ubuntu Boot Partition
2. 15gb Extended Partitions ---------
3. 5gb Data Partition 1
4. 200mb swap drive
5. 5gb data partition
6. 4.8gb data partition

If I delete all of the extended partitions, and make the ubuntu boot partition about 19.8gb and recreate the 200mb swap partition as the 2nd partition, how will I make ubuntu recognize it as the swap?



Thanks


PS: You can tell, when it takes about 5 minutes after installing to teach a windows user to setup linux on their pc, that it must be a well made linux distro.

Nice job guys!!

---

### Post by smbm on 2007-03-31
You can use swapon.

You can read up on it like this:
```

man swapon
```

I used it once but can't remember the exact command.

Good luck.

---

### Post by Rui Pais on 2007-03-31
hi, 
you will need only to add (or change) a line on the /etc /fstab like;
> /dev/hdaX   none            swap    sw              0       0

setting hdaX according to partition scheme (you can check it with fdisk)

If you don't understand habe doubts or not know what i'm telling about, post about it.

---

### Post by Funzo22 on 2007-03-31
I think the swapon command is only used for this session, whereas fstab it will change it forever.

Thanks you guys, I'll try it out soon

---

### Post by user481516 on 2008-02-10
If you don't like me and you are scared of what you could screw up in the terminal...

Add/Remove Programs - Install "GParted"
Find your linux-swap partition and right click it and click "Swapon".
That should do it.

---

