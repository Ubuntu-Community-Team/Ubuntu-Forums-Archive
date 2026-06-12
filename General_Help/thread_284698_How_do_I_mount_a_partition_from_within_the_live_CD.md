---
title: "How do I mount a partition from within the live CD?"
date: 2006-10-26
forum: General Help
---

### Post by TeeAhr1 on 2006-10-26
So I hosed my xorg.conf and need to restore it.  I'm using the live CD right now, but my drives aren't mounted, and trying a "sudo mount /dev/hda6 /media/foo" gives me "mount point /media/foo does not exist."

How can I mount this partition from within the live CD?

best regards-
p.

---

### Post by hearnden on 2006-10-26
You simply need to first create the directory where you want to mount your drive.  Something like:

```

$ sudo mkdir /media/disk

```

should be sufficient, then a

```

$ sudo mount /dev/hda6 /media/disk

```

You may need to give mount some help with "-t ext3" or something if it can't figure out the type of file system on your disk.

---

### Post by TeeAhr1 on 2006-10-26
Heh.  Probably would have remembered that if I hadn't been in such a "GODDAMMIT THIS THING NEEDS TO WORK NOW!" mentality.  Thx a ton...

-p.

---

