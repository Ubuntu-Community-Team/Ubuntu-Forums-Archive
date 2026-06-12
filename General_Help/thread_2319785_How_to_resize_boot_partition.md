---
title: "How to resize boot partition?"
date: 2016-04-07
forum: General Help
---

### Post by galapogos on 2016-04-07
Hi,

I have a Ubuntu 14.04 LTS 64-bit virtual machine, and I am running out of space so I expanded the disk capacity in the VM settings. Now, when I run gparted I see unallocated space. However, when I try to resize my boot partition /dev/sda1, I'm not given the option to increase nor decrease it.

[IMG]http://i63.tinypic.com/28jfmec.png[/IMG]

How can I resize this partition?

Thanks.

---

### Post by ajgreeny on 2016-04-07
As the root partition is separated from the unallocated space you could delete the swap partition though you will first have to use swapoff from a right click. secondly delete the extended partition and finally enlarge the root partition into the unallocated space except for a new swap partition at the far right end.

This will take a long time and you must not interupt the activity or you will probably lose everything.

A better way to proceed is just to create a new ext4 partition in the currently unallocated space and mount that using fstab.  You can then use that partition for data files. It is possible to use symbolic links to the data folders in your current home so that all files appear to be sited in your home even though they are in that data partition.

---

### Post by galapogos on 2016-04-07
> **ajgreeny said:**
> As the root partition is separated from the unallocated space you could delete the swap partition though you will first have to use swapoff from a right click. secondly delete the extended partition and finally enlarge the root partition into the unallocated space except for a new swap partition at the far right end.

This will take a long time and you must not interupt the activity or you will probably lose everything.

A better way to proceed is just to create a new ext4 partition in the currently unallocated space and mount that using fstab.  You can then use that partition for data files. It is possible to use symbolic links to the data folders in your current home so that all files appear to be sited in your home even though they are in that data partition.

Thanks. I ended up using the 1st method. Booted up with a Live CD so that the boot partition is unmounted.

---

