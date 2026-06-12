---
title: "Resizing Ubuntu Partition Help"
date: 2007-03-04
forum: General Help
---

### Post by b0ng0 on 2007-03-04
I currently have my hardrive in 3 partitions - one for (k)ubuntu at 35 GB, one for windows at 50GB and one for music, docs, etc (/home) at 68 GB.

I have realised that 35GB is far too much for just the OS and the partition I use for music, etc is 70% full. I was wondering if there is a safe way to resize the (k)ubuntu partition to about 25GB then extend the 68GB using the freed up space?

---

### Post by jimbob on 2007-03-04
Is that the physical order they are on the disk - ie Kub on hda1, winblows on hda2 and home on hda3? 
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by chggr on 2007-03-04
Sizing and merging partitions can be done using gparted livecd:
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

In any case, back up your data. 
This is generally a safe procedure, but you never know!!

---

### Post by b0ng0 on 2007-03-04
Can I just use the partition tool on the kubuntu livecd or ubuntu livecd? The order of the partitions is windows first, then swap space, the kubuntu then music, etc

Will I have to format the music, etc parition to increase the size or can i just add space on?

Thanks

---

### Post by Spaceomega on 2007-03-04
You should be able to use the partition tool on the Kubuntu or Ubuntu live cd's, seeing as how that is just gParted, same as the other CD the other member said to download.

You shouldn't have to format, just increase.

---

### Post by jimbob on 2007-03-04
Even if you shrink Kubuntu to 25 I don't think you will be able to move the beginning of the home partition without copying it off to anothed hd and then copying it back.   ASFIK you can't move the starting point with Gparted.
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by chggr on 2007-03-05
Well, the safest way is to backup and then experiment...
I suggested the liveCD because you cannot resize the root partition when linux is running from it.

---

### Post by b0ng0 on 2007-03-05
OK I just tried the QParted from the Kubuntu LiveCD, however when I select the ext3 partitions, resizing is not an option, only format.

What can I do, my kubuntu partition is way too big :(. Is it possible/safe to use PartitionMagic from Windows to resize?

---

### Post by jimbob on 2007-03-05
Download and burn the standalone Gparted.  That will let you shrink your Kubuntu partition.

Besides, it is an excellent tool to have on hand for future partition adjustments.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

