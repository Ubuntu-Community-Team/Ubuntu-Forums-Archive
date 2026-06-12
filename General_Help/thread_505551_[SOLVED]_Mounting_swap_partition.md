---
title: "[SOLVED] Mounting swap partition"
date: 2007-07-20
forum: General Help
---

### Post by chris1974 on 2007-07-20
My Feisty install has lost its ability to swap.  I know swapping is bad, but I will need lots of swap space to develop iso files.

Both free -m and top show that I have 0 swap available, 0 swap used, and 0 swap free.

free -m
total used free shared buffers cached
Mem: 495 453 42 0 7 170
-/+ buffers/cache: 275 220
Swap: 0 0 0

My swap partition is entered in my fsab file, and it shows up when I run fdisk.  Gparted confirms that a swap partition does indeed exist on my hard drive (1.4 gig).

When I run the system manager, it only shows two partitions--root and my ntfs partition.

I don't know how I would have changed any settings accidentally.  But I would like my swap back.

Any suggestions?

---

### Post by HermanAB on 2007-07-20
Hmm, if the /swap partition exists and it is of type swap, then it should be as simple as issuing the command:
$ sudo swapon

'Hope that helps!

Herman

---

