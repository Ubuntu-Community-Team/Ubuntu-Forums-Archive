---
title: "LVM partition not showing full size"
date: 2007-01-31
forum: General Help
---

### Post by jeeves on 2007-01-31
When I try using  **fstab** to automatically mount my new LVM "partition" it displays as the wrong size. I should have over 400GB of free space in LVM, but when mounted automatically it comes up as a mere 5GB.

Any ideas how to fix this. This is what I am using in my fstab:
[PHP]# my LVM partition
/dev/myth_vol_group/myth_store /mnt/video_store           ext3    defaults        0       2
[/PHP]
And I can manually mount the partition as root using the following and get the full size:
[PHP]mount /dev/myth_vol_group/myth_store /mnt/video_store[/PHP]

edit: Problem solved. I had typed an incorrect path in to my fstab.

---

