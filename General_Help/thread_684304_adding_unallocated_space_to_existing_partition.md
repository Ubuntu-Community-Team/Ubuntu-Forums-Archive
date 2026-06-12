---
title: "adding unallocated space to existing partition?"
date: 2008-01-31
forum: General Help
---

### Post by eheyl on 2008-01-31
Hey all. I've got 18gb of unallocated space (used to be an ext3 partition that I deleted) and I was wondering how can I add it to my main ext3 partition in ubuntu> for that partition I've got about 2gb space left and would like to increase it. 

Thanks!

:guitar:

---

### Post by nemilar on 2008-02-01
Google for "GParted LiveCD"

Burn one of those, you can delete the old partition and extend your current one; you'll have to do it off the liveCD, though.

---

### Post by Rocket2DMn on 2008-02-01
You will need to boot from the LiveCD since you cannot fiddle with a partition that is mounted (your root partition).  Once in the LiveCD, open GParted with System->Administration->Partition Editor

---

### Post by Clark Leach on 2008-02-21
And then what?  I don't see any explanation as to how to reallocate this unallocated space.  GParted is certainly not self-explanatory.

---

### Post by bodhi.zazen on 2008-02-21
Documentation: [Documentation](http://gparted.sourceforge.net/documentation.php)

---

### Post by housam on 2008-02-21
> **eheyl said:**
> Hey all. I've got 18gb of unallocated space (used to be an ext3 partition that I deleted) and I was wondering how can I add it to my main ext3 partition in ubuntu> for that partition I've got about 2gb space left and would like to increase it. 

Thanks!

:guitar:

Download [[COLOR="Red"]the new version of Gparted [/COLOR]]("http://gparted-livecd.tuxfamily.org/")and burn it , it'll help you doing the task easily.

---

### Post by eheyl on 2008-03-22
I'm sorry I still can't do it. I've got partitions in this order: NTFS 42 GB. Ext3 18GB free, ext3 7 gb taken, 1.7 free (thats where ubuntu is). I want to move the second ext 3 partition in front of the first but it seems I can't do that. The instructions aren't step by step enough. I can resize the partitions but thats not helping. I'm thorougly confused and would like some help.

---

### Post by eheyl on 2008-03-22
Better yet, here's a screenshot. I basically want to add the 18GB partition (all free space to the oneto the right of it. Nad yes I use the livecd :)

---

### Post by Rocket2DMn on 2008-03-22
Try right clicking the sda3 partition (which is what I think you are saying you want to delete) and hitting Delete.  Make sure your linux swap partitions are unmounted since I think the LiveCD mounts them - you can do that from the right click menu.  You may want to consider merging those swap partitions, too, which you can do by deleting one and growing the other to fill up the newly freed space.
Once you delete the sda3 partition, try growing the sda4 (logical) partition into that space.  That may leave you with empty space inside the sda4 extended partition.  Then perhaps you can expand your root partition to use that space.

This may not work because we are trying to combine a physical partition and a logical partition, but it's worth a shot.

---

