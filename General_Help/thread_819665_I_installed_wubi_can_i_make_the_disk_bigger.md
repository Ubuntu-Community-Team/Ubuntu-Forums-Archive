---
title: "I installed wubi can i make the disk bigger?"
date: 2008-06-05
forum: General Help
---

### Post by pclover on 2008-06-05
I installed wubi can i make the disk bigger? Thanks

---

### Post by ago on 2008-06-06
Use LVPM

---

### Post by Paqman on 2008-06-06
More info about [LVPM](http://lubi.sourceforge.net/lvpm.html).

Scroll down to the bit about "Resizing virtual disks using LVPM"

---

### Post by unicorn_2003_1 on 2008-06-06
Correct me if I'm wrong.

The thing about the current LVPM is: when you want to resize it, it actually creates a new file disk and copy the original file bit by bit to the new disk, then renaming the new disk root.disk, thus the resizing.

The only problem is, the free space on my hard disk is limited, and that's the reason why I didn't gave the Wubi installer a bigger share of space.

I was wondering if LVPM or some tool can do the resizing "in situ"? I only got 2G of free space left, so to have a new disk 5G of size is not the option I have.

Thanks

---

### Post by ago on 2008-06-06
No it doesn't do it in-situ, although it is technically possible to do so.
On the wubi guide there is a script that allows you to move a single directory to a dedicated disk.
This is an intermediate solution since you do not need 2X root.disk size + K. But root.disk size + K.

---

