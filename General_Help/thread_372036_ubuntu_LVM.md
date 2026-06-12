---
title: "ubuntu LVM"
date: 2007-02-27
forum: General Help
---

### Post by apocolpse on 2007-02-27
I just added a new hard drive to my system. So now i have  the following when i do fdisk -l


```
Disk /dev/hda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9587    77007546   83  Linux
/dev/hda2            9588        9964     3028252+   5  Extended
/dev/hda5            9588        9964     3028221   82  Linux swap / Solaris

Disk /dev/hdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        9964    80035798+  83  Linux
```

hdb1 is the new drive. How can i create a single LVM volume that will attach both my active hda1 and my secondary hdb1 together.....

---

### Post by k|d&lt;FuNkY&gt;FrY on 2007-02-27
I'd start here... 

[http://tldp.org/HOWTO/LVM-HOWTO/index.html](http://tldp.org/HOWTO/LVM-HOWTO/index.html)

I'm not versed enough in this particular area to provide you with a step by step tutorial. However, the above link should get you started in the right direction. 

Good Luck!

---

