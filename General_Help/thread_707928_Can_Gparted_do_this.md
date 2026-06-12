---
title: "Can Gparted do this?"
date: 2008-02-25
forum: General Help
---

### Post by rollinroll on 2008-02-25
Hi, say i want to extend my ubuntu partition size from Gprated. Do i have to use the live CD or can Gparted work with the linux partition within the OS?

---

### Post by bodhi.zazen on 2008-02-25
You can not resize a partition if it is mounted, thus to resize your root partition -> live CD

---

### Post by rollinroll on 2008-02-25
Ok, thx. But how can vista's built in partition manager do this? I remembered resizing my vista partition to make space for ubuntu and it did it all when the partition was mounted.

---

### Post by bodhi.zazen on 2008-02-25
Well, Vista is new and I do not run it.

My understanding is that the partitioning tool with Vista is the best tool to use to resize vista.

I doubt it will resize anything but FAT or NTFS partitions (ie does Vista recognize your Ubuntu partition ?).

IMO gparted is your best option, although there may be some windows tools like partition magic that will do it for you. Occasionally the windows tools fail though :(

---

