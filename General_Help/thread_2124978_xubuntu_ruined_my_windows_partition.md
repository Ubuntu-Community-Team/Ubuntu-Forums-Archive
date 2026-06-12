---
title: "xubuntu ruined my windows partition"
date: 2013-03-12
forum: General Help
---

### Post by ShadesOfGreen on 2013-03-12
EDIT: didn"t seem to ruin my windows partition , was abit frustrated excuse mej

So my xubuntu install crashed, and now i get an error each time i boot my pc 

> Error: no such partition.
Grub rescue>

---

### Post by ManamiVixen on 2013-03-12
You were supposed to repartition the hard drive first using Windows, then install Xubuntu to the partitioned space. Like say 20GB for Xubuntu. You could alos use WUBI installer if you have a Windows 7 PC or older. Windows 8 has issues with WUBI.

---

### Post by ShadesOfGreen on 2013-03-12
I didnt use Wubi. I had 2 partitions on my hard drive. Then used GParted from the Xubuntu 12.10 CD to make the partition which didnt contain my windows files smaller, with 30GB unallocated space to install Xubuntu. After that i tryed installing 12.04.02 on the partition that had xubuntu 12.10 , but the installer crashed..
  

Now , i just booted from CD again, and i saw my windows partition is still intact (atleast that is what i think). 
But when i boot my PC , i get an error message : 

```
"Error: No such partition.
Grub rescue>
```

how can i fix this? :s

---

### Post by QIII on 2013-03-12
Hello!

Have a look at [Boot-Repair](https://help.ubuntu.com/community/Boot-Repair).  It was written by a forum member.

First select "Create a BootInfo summary" and post the results back here.  That will help everyone understand what is on your disk.

Best wishes.

---

### Post by ShadesOfGreen on 2013-03-12
I just reinstalled Xubuntu, after reformatting the partition it was on, 
and I don't get the grub error anymore, LOL, 
sometimes things can be this simple :p

Thanks for trying to help though ;)

This thread can be destroyed now, or whatever

---

### Post by QIII on 2013-03-12
I won't destroy it (we don't do that), but you might want to change the title to something like "Xubuntu failed install, GRUB issue"

Glad it worked out.

---

