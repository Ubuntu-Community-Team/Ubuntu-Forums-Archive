---
title: "Using ext4 loopback image"
date: 2012-12-11
forum: General Help
---

### Post by carlsiu on 2012-12-11
I've created a 8GB disk image (ext4) from a partition of USB flash drive via 'dd'. I mount it to a directory:
mount -o loop disk.img mount_dir/

I can access the files inside it. The problem is that when I copy files to the mount_dir, the system seems to have large IO Wait and the system is nearly hang. I also tried to copy only few small files. Though the 'cp' command is returned quickly, it takes long time to finish a following 'sync' command.

This gives me an impression that, when the system flush the data to a disk image, it will re-write the whole image file again. Thus, in my case, no matter what I have modified, I need to pay the cost of writing 8GB file to disk. I would like to know does such assumption match the reality? Any workaround for that?

Thanks in advance.

---

