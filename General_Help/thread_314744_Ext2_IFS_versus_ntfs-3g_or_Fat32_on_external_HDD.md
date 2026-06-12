---
title: "Ext2 IFS versus ntfs-3g or Fat32 on external HDD??"
date: 2006-12-08
forum: General Help
---

### Post by eeried on 2006-12-08
Hello,

I've been reading some threads about these two ways of reading files on an external HD drive from Windows and Linux.

I have to find a very safe way of setting up an external HDD (250Go, I think) for someone. He's on dual boot for the time being but he'll need this external drive to be readable and writable from any Windows machine.

ntfs-3g is very tempting, and the easiest solution but this guy can't afford to lose any data (he can't store it all on his computer, but perhaps he could buy an extra internal HDD for backup).

He does a lot of PAO stuff (books and magazines) -- he loves Scribus btw though he used to use Xpress in his job -- and I suppose he carries his huge PDF files on his external HDD to the printer. He copies photos and pictures from other computers onto his HDD as well.

The problem with Ext2 IFS is that he would have to install it on any Windows machines he comes across, and the printer, for instance, may not want to install any program.

We could move all his files to the computer and reformat his HDD in Fat32. Would Fat32 work fine on such a big HDD? Okay we can partition the HDD but then I've read Windows may not see all the partitions on an external HDD.

First I thought we could make 2 partitions: one in FAT32 for serious everyday use and one in NTFS to experiment with ntfs-3g, and see how safe it is.

The HDD is far from being full up but the serious partition may become full in the long or short run.

I'll tell you what, Windoze is a pain... ](*,) but what's your advice?
many thanks in advance

---

### Post by grsing on 2006-12-08
I've got two externals, both as FAT32 (one is 120GB, the other 250, in two partitions).  FAT32 is easy, because both Ubuntu and Windows can read and write to it, without any problems at all, and for the stuff he's doing, safe/reliable sounds like the way to go.

---

### Post by eeried on 2006-12-08
Many thanks for your reply grsing.

Does Windows see both partitions on your external HDD?

Is it necessary to partition the HDD, or was it just your choice?

---

