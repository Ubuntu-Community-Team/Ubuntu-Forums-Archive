---
title: "Reinstalling Fiesty without losing data?"
date: 2007-04-21
forum: General Help
---

### Post by smartboyathome on 2007-04-21
Is there any way to reinstall fiesty without losing any of the data on my hard drive? I need to reinstall for my wireless card to work (it got knocked out when I upgraded from dapper to edgy before I upgraded to fiesty). Right now, it won't let me use the wireless card, so I need to reinstall it. Is there any way to do this without losing data? Thanks!

EDIT: This is now resolved. Please see my last post for how I did it.

---

### Post by Jump on 2007-04-21
What I did was create another parition and then used partimage to make in image of my current  partition and restored it on the 2nd parition. Now I have two idential partitions and an image burned to a couple of CD-Rs that I can restore and mess with at any time.

---

### Post by smartboyathome on 2007-04-21
Ok, I will try this. Thanks!

---

### Post by smartboyathome on 2007-04-22
This is resolved now. Here is how I went about this...

1. Startup the Fiesty Desktop CD and install it on a new partition.
2. Move all your important files onto the new partition.
3. Get Gparted (or a similar partitioning program) on a CD and restart your computer.
4. Delete the old partition and add that space to the new partition.

---

