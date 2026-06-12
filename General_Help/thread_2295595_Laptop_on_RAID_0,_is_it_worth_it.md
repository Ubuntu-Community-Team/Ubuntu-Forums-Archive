---
title: "Laptop on RAID 0, is it worth it?"
date: 2015-09-20
forum: General Help
---

### Post by edher67 on 2015-09-20
Hi, 

I have a laptop with 2x250GB SSD and I wanna know if it's possible to use RAID 0 (I asume it's with Ubuntu server) but even if it's possible, is it worth it?

I'm looking for a read/write speed improvement but there is a risk associated with RAID 0.

So, has anyone tried on a productive machine? (This is my work station, and it has to be reliable)

The laptop it's a System 76 Gallago Ultra Pro with 32GB RAM

Thanks

---

### Post by Bucky Ball on 2015-09-20
Read [here]("https://en.wikipedia.org/wiki/RAID#Standard_levels") under the heading 'RAID 0'. Looks like it does improve performance and explains how. I don't know by how much or if it's worth doing, though.

As explained there, it may make retrieving data from either drive more difficult if one of the drives crashes (or if your OS install breaks and you can only retrieve from a live session, USB or DVD).

---

### Post by tgalati4 on 2015-09-20
With 32 GB of RAM, you can simply run everything with RAM and use *preload* or *ureadahead* to stuff common programs into RAM.  The risk of pool failure doubles with RAID0 and laptops generally don't have superfast datapaths to take advantage of the speed doubling that RAID0 offers.  Only testing will tell.

A system set up this way could be unbelievably fast.  Open programs even as you think about them.  But, it will fail at the worst possible moment--just as you are trying to finish an important work project.

Let us know what speeds you come up with.

---

### Post by edher67 on 2015-09-20
Am gonna give it a try and see what happens.

Thanks

---

