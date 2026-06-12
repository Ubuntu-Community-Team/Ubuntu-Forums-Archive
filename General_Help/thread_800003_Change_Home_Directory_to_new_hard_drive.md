---
title: "Change Home Directory to new hard drive"
date: 2008-05-19
forum: General Help
---

### Post by homerj742 on 2008-05-19
My current dual-boot setup, has 2 hard drives:

250GB - Windows XP
500GB - Ubuntu 7.10

I want to wipe the windows xp partition and install Ubuntu 8.04 on there, and then mount the 500GB hard drive as my home directory. Thus allowing my to perserve my data and do fresh installs of Ubuntu when new releases come. 

How would I go about changing my home directory to whatever is on the 500GB hard drive?

---

### Post by roe_polak on 2008-05-19
Well, if you're just doing a fresh install it's as simple as mounting /dev/sdb1 as /home in the partitioner of the installer. Here I'm assuming that the harddisk is called sdb1. Replace with the actual disk/partition.

EDIT: Do you plan to wipe both disks?

---

### Post by homerj742 on 2008-05-19
Thanks for the response. I'm only planning on wiping the 250GB hard drive. 

Since the 500GB HD is already ext3 file system, I'm just going to delete everything except the contents of the home folder. Thus no need to really backup my data (since I do not have an external HD).

---

### Post by roe_polak on 2008-05-19
I usually just rename my old home dir. In that way Ubuntu won't get confused by different .(dot)-files in home. A side effect of this is that my home folder(s) have absolutely no structure whatsoever. It's a big mess :oops:  I've got old things lying around all the way back to 2006. 

Now please don't reformat it in the installer :)

---

