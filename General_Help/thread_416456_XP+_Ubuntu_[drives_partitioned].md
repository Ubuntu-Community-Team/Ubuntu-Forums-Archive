---
title: "XP+ Ubuntu [drives partitioned]"
date: 2007-04-21
forum: General Help
---

### Post by phoenixankit on 2007-04-21
I have a pc with XP and my Hard Drive with 4 partitions, 20GB each. My C drive has Windows, and D n E have other stuff, my F drive is COMPLETELY empty. I want to install ubuntu there.
I've seen many tuts on how to dual boot xp w/ Ubuntu, but all of them are targeted on pc's with no partitioned drives. I already have a separate 20GB partition reserved for Ubuntu. 
Someone please help...

---

### Post by spin2cool on 2007-04-21
this will be easy for you to do.  Boot up from the Ubuntu live CD, and when you get to the part about partitioning, choose the manual option. 

Choose the partition that is empty, and delete that partition.  

Then, create two new paritions in that space.  One should be about 1GB and formatted as "linux-swap" (and you should mount swap there).  The other, filling the remainder of the space should be ext3 (and you should mount '/' there).

Then continue through the installer, and you should be in business.  Good luck!

---

### Post by phoenixankit on 2007-04-21
I'm a total noob at linux...so please dont mind
a live cd? is it the same one as the one i'm downloading from [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) ?
and what do you mean by > formatted as "linux-swap" and > the space should be ext3 (and you should mount '/' there)

---

### Post by spin2cool on 2007-04-21
Yes, the CD you're downloading is both a liveCD and a install cd.  It'll let you play around with a stripped-down version of ubuntu and/or install it.

After you start the install, you'll get to a step that talks about partitioning.  You'll want to select "Manual"

Then, choose the partition that is empty from the list, and click on "delete partition"  (be sure you are deleting the correct one!)

Then, where that partition used to be, you'll want to create two new paritions.  

One will be about 1gb in size.  You'll choose 'use as: swap' to format that partition as linux-swap, and then for 'mount point', you'll choose (you guessed it) swap. 

Then, create another partition with all the remaining space.  Under 'use as', choose ext3 (that's the type of filesystem).  And mount point will be "/"  - this tells the installer to install the root of the linux system there.

After that, just follow the prompts and you should be fine.

---

### Post by phoenixankit on 2007-04-21
Hey thanks!! Big help....

---

### Post by sdowney717 on 2007-04-21
If you want you can also delete the partition from windows to create unallocated space. The ubuntu installer can then use this.

in xp, go to control panel, administrative tools, computer management, storage, disk management,
select the partition, right click and delete it.

---

