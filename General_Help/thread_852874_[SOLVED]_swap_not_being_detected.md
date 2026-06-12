---
title: "[SOLVED] swap not being detected"
date: 2008-07-08
forum: General Help
---

### Post by Samrat Rao on 2008-07-08
I am using 7.10 Gutsy. I wished to expand the root partition using the utility 'gparted'. I was unable to expand the root partition as it was necessary to unmount the partition which I did not do. But in the process I shifted the swap to another location. So now while booting, the swap partition is not getting detected and I am unable to change /etc/fstab as I don't know the details of the new swap space i.e. UUID and mount point. So what do I do?

---

### Post by sdennie on 2008-07-08
To find the UUID and partition number, try:

```

sudo blkid

```

Once you've found that, you should be able to just update the old fstab swap entry with the new UUID.

---

### Post by iaculallad on 2008-07-08
Input the command below on your terminal and post the result:

```
sudo swapon -a -v
```

---

