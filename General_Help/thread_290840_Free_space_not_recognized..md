---
title: "Free space not recognized."
date: 2006-11-01
forum: General Help
---

### Post by Protoss on 2006-11-01
I just booted into the Ubuntu live CD, resized my root partition from 20GB to 50GB, and it completed fine, but Ubuntu is not recognizing the 30 gigs of free space, it still says it has 2GB free, yet recognizes that the partition is 50 gigs. 
Is there something screwy with my partition table? Or is there something I need to do to make Ubuntu re-read my partition table?

---

### Post by matthewstory on 2006-11-01
what does the output of this command look like:

df -h /dev/hda1

of course, replace /dev/hda1 with whatever the partition in question is.

---

### Post by Protoss on 2006-11-01
Hmm..strange, I get this:
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda4              18G   16G  1.3G  93% /

```
But if I go into Gparted, it says 50GB total.

---

### Post by Protoss on 2006-11-02
Anyone got an idea as to what is wrong? I just tried booting into the live cd, and just re-doing the partition edit, it completed successfully, but my df -h still only shows 18G. I would re-install except for the fact that I just now got everything how I like it.

---

