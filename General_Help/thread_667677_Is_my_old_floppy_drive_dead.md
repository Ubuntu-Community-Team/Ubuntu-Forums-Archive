---
title: "Is my old floppy drive dead?"
date: 2008-01-14
forum: General Help
---

### Post by megamania on 2008-01-14
For some reason, after four years I had to connect my old floppy drive to my computer. This is the output of dmesg:

```
[   18.376602] Floppy drive(s): fd0 is 1.44M
[ 1014.731489] end_request: I/O error, dev fd0, sector 0
[ 1201.546651] end_request: I/O error, dev fd0, sector 0
[ 1201.570631] end_request: I/O error, dev fd0, sector 0
[ 1242.462294] end_request: I/O error, dev fd0, sector 0
[ 1242.486268] end_request: I/O error, dev fd0, sector 0

```
It's not a problem with the floppy disk, because (the same floppy is read correctly by my USB floppy drive on the same computer.

Also, if I try to mount the internal floppy from Places -> Computer -> floppy, I get:
```
mount: /dev/fd0 is not a valid block device
```

Since the floppy drive is recognized, I'd assume it is connected correctly; however, since it reads no floppy, I'd assume it's dead. Am I right?

Just checking before I trash it and rush out to buy a new one...

---

### Post by wolfen69 on 2008-01-14
i would say it's dead. ive had 2 die on me, it does happen.

---

### Post by megamania on 2008-01-14
> **wolfen69 said:**
> i would say it's dead. ive had 2 die on me, it does happen.
:( Thought so... I just can't bear the hassle of going out and buy such an old thing, considering I'll use it 3 or 4 times...

Thanks for your advice!

---

