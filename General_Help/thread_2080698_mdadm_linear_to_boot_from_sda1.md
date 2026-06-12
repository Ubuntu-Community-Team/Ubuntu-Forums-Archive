---
title: "mdadm linear to boot from sda1?"
date: 2012-11-04
forum: General Help
---

### Post by snowball2 on 2012-11-04
Hi all,

I currently have Ubuntu 12.10 installed on my boot disk (sda1) and I have added a 2nd drive (sdb1) which I would like to use to create a linear drive (md0) with mdadm. My question is, can I create md0 and still retain the original file system and boot sector from sda1?

Would the following command do the trick?

```
mdadm --create --verbose /dev/md0 --level=linear --raid-devices=2 /dev/sda1/ /dev/sdb1
```

EDIT : Ok,  I tried the above command and I can see the md0 device with cat /proc/mdstat as :

[I]md0 : active linear sda1[0] sdb1[1]
      201603056 blocks super 1.2 0k rounding

unused devices: <none>[/I]

But now when I boot I get dumped at a ***grub rescue*** prompt.. Is there any way to still boot from sda1/recover data?

---

### Post by snowball2 on 2012-11-04
Ok I've rolled back to the initial configuration by replacing the superblocks on sda1 and sdb1.. So question again is really to know if it is possible to convert an existing install to boot from a newly created md0?

---

