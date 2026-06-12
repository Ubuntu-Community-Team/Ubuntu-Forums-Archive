---
title: "&quot;Trapped&quot; partition"
date: 2007-12-06
forum: General Help
---

### Post by computerex on 2007-12-06
Hello Guys. This is how my partition table looks like: [http://i37.photobucket.com/albums/e80/computerex/gparted.png](http://i37.photobucket.com/albums/e80/computerex/gparted.png)

hda5 is my linux partition, hda1 is windows, and hda7 is just a storage partition. I want to get some more space to hda5, but it seems I can't move the partition back and give it the unallocated space. What can I do?

---

### Post by ccprog on 2007-12-07
hda5 is one of the extended partitions. That means that physically it depends on the size and position of its wrapper, hda2.

Before resizing hda5, you need first to resize hda2 (mark the line or click on the cyan-colored frame surronding the partitions to the right.)

---

