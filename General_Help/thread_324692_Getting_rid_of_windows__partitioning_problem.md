---
title: "Getting rid of windows / partitioning problem"
date: 2006-12-24
forum: General Help
---

### Post by BSAB_80 on 2006-12-24
Hey guys. I've run into a litte trouble with trying to establish a partition with Gparted.

I had a Windows partition that i deleted, and now i have 80GB unallocated that i want to add to my Ubuntu partition (/dev/sda2), but no luck.

If i try it during my normal Ubuntu session, the resize option is whited out, and if i try it with the Ubuntu Live CD i can only get to downsize it, i.e. reduce its size and i cannot seem to use the unallocated free space to increasse its size.

I'm also still getting the boot-up option for Windows when i start my laptop.


Any idea what am i doing wrong?

---

### Post by bodhi.zazen on 2006-12-24
> **BSAB_80 said:**
> Hey guys. I've run into a litte trouble with trying to establish a partition with Gparted.

I had a Windows partition that i deleted, and now i have 80GB unallocated that i want to add to my Ubuntu partition (/dev/sda2), but no luck.

If i try it during my normal Ubuntu session, the resize option is whited out, and if i try it with the Ubuntu Live CD i can only get to downsize it, i.e. reduce its size and i cannot seem to use the unallocated free space to increase its size.

I'm also still getting the boot-up option for Windows when i start my laptop.


Any idea what am i doing wrong?

You can only expand a partition to the right as it were.

I assume your free space is to the left of you Ubuntu partition.

You have several options:

[list=number][*]Format the free space and mount it as a data partition or /home
[indent][http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/)[/indent]
[*]use gparted and move your Ubuntu partition to the beginning of the disk and then re size[/list]

IMO I would format the partition and mount it as a data partition in say /mnt/data 

Use /media/data if you want a desktop icon ....

---

