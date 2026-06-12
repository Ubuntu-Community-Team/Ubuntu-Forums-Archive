---
title: "Can't reclaim all disc space after uninstalling ubuntu"
date: 2014-10-14
forum: General Help
---

### Post by haiiya on 2014-10-14
When I installed ubuntu i choosed 20gb as the ubuntu partition size, and after uninstalling ubuntu i could only reclaim 16gb. What happened to the last 4gb? I can't seem to reclaim it or see it anywhere

---

### Post by slickymaster on 2014-10-14
Were you dual booting Ubuntu with windows? If so, you just need a partition program to delete the Ubuntu partition and then resize the Windows partition to claim the space Ubuntu was using. Just make sure you don't delete your other Windows partitions.

---

### Post by Impavidus on 2014-10-14
Maybe a 4GB swap partition? Without knowing how you installed and uninstalled Ubuntu it's difficult to guess.

---

### Post by kc1di on 2014-10-14
you should be able to use Gparted to reclaim the lost 4 GB, my guess is it's a swap partition.  Gparted will delete the partition and you can resize the windows partition to reclaim that space. remember Windows can not see a linux partition. so what ever you do you need to reformat it to NTFS , or Fat.

---

### Post by haiiya on 2014-10-14
> **slickymaster said:**
> Were you dual booting Ubuntu with windows? If so, you just need a partition program to delete the Ubuntu partition and then resize the Windows partition to claim the space Ubuntu was using. Just make sure you don't delete your other Windows partitions.
Yes I was dual booting. I used windows disk management but it won't let me see all the partitions. I was able to reclaim 16gb through that but not the last 4gb

> **Impavidus said:**
> Maybe a 4GB swap partition? Without knowing how you installed and uninstalled Ubuntu it's difficult to guess.
That's my guess too

> **kc1di said:**
> you should be able to use Gparted to reclaim the lost 4 GB, my guess is it's a swap partition.  Gparted will delete the partition and you can resize the windows partition to reclaim that space. remember Windows can not see a linux partition. so what ever you do you need to reformat it to NTFS , or Fat.
I'll try gparted, ty

---

