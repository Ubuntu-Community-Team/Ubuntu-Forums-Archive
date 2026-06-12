---
title: "Is it possible to mount swap on different physical HDD for Ubuntu?"
date: 2015-05-12
forum: General Help
---

### Post by i12 on 2015-05-12
Is it possible to mount swap on different physical HDD for Ubuntu? How to do it?

---

### Post by sudodus on 2015-05-12
Yes, you can make a swap partition 'anywhere', and point to it using its UUID in the file **/etc/fstab**. So change the current entry for swap such that it points to this new swap partition. (You can even have more than one swap partition.)

I suggest that you use ***gparted*** to create the swap partition. After making the new swap partition, the following command will show the UUID, that you should use (without quotes)

```
sudo blkid
```

Edit with the following command line

```
sudo nano /etc/fstab
```

---

### Post by plucky on 2015-05-12
> **i12 said:**
> Is it possible to mount swap on different physical HDD for Ubuntu? How to do it?

Yes

See [SwapFaq](https://help.ubuntu.com/community/SwapFaq)

Good Luck

---

### Post by buzzingrobot on 2015-05-12
During a fresh install, select the "Something Else" option at the partitioner.

---

### Post by oldfred on 2015-05-12
I have several drives with a swap on each(not sure why I have one per drive?). 

But a new install finds all my swaps  and adds each to my fstab automatically. My install to my SSD added the swaps on both HDD. SSD does not have swap, but I have enough RAM that I never use swap anyway.

So if you create swap in advance with gparted the installer will auto magically find it.

---

