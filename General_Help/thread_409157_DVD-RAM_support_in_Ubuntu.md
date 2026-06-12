---
title: "DVD-RAM support in Ubuntu"
date: 2007-04-14
forum: General Help
---

### Post by sicofante on 2007-04-14
DVD-RAM should behave like a big floppy or removable drive. It should be possible to format it the same you would an USB pendrive, for instance. It seems though, that Ubuntu treats DVD-RAM as ordinary (rewritable) DVDs and CDs.

Is there a way to use DVD-RAM "the right way"? Maybe I'm doing something wrong?

---

### Post by rai4shu2 on 2007-04-14
Last I tried it, DVD-RAM still worked like DVD-RW (i.e. you have to import old sessions). So far, I've only seen this work consistently with K3b.

---

### Post by sicofante on 2007-04-14
No K3b or other specific app should be necessary. DVD-RAM support should be part of the OS itself, just like USB pendrives, floppy drives, etc.

Any idea if it'll be supported in the future?

---

### Post by rai4shu2 on 2007-04-14
This may not work, but it may be worth a shot (I haven't tried it recently):

Add this line to your /etc/fstab

```
/dev/cdrom /media/cdrom udf,iso9660 user,rw,noauto 0 0
```

Then insert your disc and type this:

```
sudo mount -a
```

---

### Post by matthias_k on 2008-03-21
that did not help for me. I am still unable to write to a DVD-RAM in Ubuntu Feisty.

---

