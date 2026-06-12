---
title: "SSD as HDD cache, or apple fusion like facility"
date: 2016-11-27
forum: General Help
---

### Post by ivo-welch on 2016-11-27
I have a 128GB SDD and a 5TB HDD.  I can use 64GB as my boot and root partitions, but 64GB is too small for all my user files.  (same for 1TB.)  alas, it would seem to me that this would be ideal for caching the hdd, perhaps even in a similar intelligent way that OSX runs its fusion drive.

are there some ubuntu solutions to this issue?

sincerely,

/iaw

---

### Post by oldfred on 2016-11-28
I have a 128GB SSD & 1TB HDD. 
I put several Ubuntu / (root) partitions on SSD (old, new or future installs) and all data on HDD. 
Since recent activity is cached in RAM, system is fast booting thru SSD & most of my use is the same applications so most in RAM. Then only loading data from HDD may be a bit slower, but new HDD are relatively quick and data is small.  

 One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)
UEFI/gpt partitioning in Advance:
[http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu](http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu)
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
[http://askubuntu.com/questions/461394/how-to-partition-ssdhdd](http://askubuntu.com/questions/461394/how-to-partition-ssdhdd)
[http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation)

I do not have a lot of data, so both drives not fully allocated, yet.
 Oldfred's current partitions Dec 2015
[http://ubuntuforums.org/showthread.php?t=2305833&p=13404413#post13404413](http://ubuntuforums.org/showthread.php?t=2305833&p=13404413#post13404413)

---

### Post by 1clue on 2016-11-28
Remember that on large drives you need to use gpt partition tables or you'll have no access to anything past 2tb.

I use lvm on my drives wherever possible.  That gives me the option to resize partitions on the fly.  Been at it for 20 years now, still not great at guessing which partitions need to be what size for any given box.

I'm not sure if two separate drives make sense as a "fusion" drive. A fusion drive is basically using the ssd as a really big cache if I understand correctly, but the activity between the ssd and the spinner is through a separate channel, not through the SATA pipe that your motherboard uses.

I'm also of the opinion that this is a waste of an ssd. I'd set up your OS and a few other time-critical files on the ssd and then use the spinner for everything else. Another thing to keep in mind is that you should keep your ssd somewhat sparsely populated. As long as your SSD has some empty space to work with, it can easily and quickly rearrange things to avoid data issues.  The firmware on a modern SSD is pretty sophisticated, so if one block gets too many writes the drive will swap it with something that's either empty or has few writes.

---

