---
title: "Help me kill Windows"
date: 2008-02-18
forum: General Help
---

### Post by BobLand on 2008-02-18
I have an XP only drive and a Windows2000 drive.  The XP drive refused to reformat the W2K drive saying another process had it in use.  I tried to erase the contents of the W2K drive but Windows ended up removing itself on C:.

```
 c:\ format h: /a
blah blah blah  OK (Y/N) y
c:\*.*
Ctrl-C
```

it ended up removing Docs & Settings from C: even though there was nothing that said to do this.

I also cannot reach the W2k partition from gParted.  Is says nothing is there.  180k empty, 93k in use.  Will let me do anything to the 180k but nothing to the 93k.

I'm ready to send both disk to the cleaners but can't reach that W2K partition.

Any ideas?
bobland

---

### Post by seventhc on 2008-02-18
You could boot from the ubuntu live cd and do it using gparted.

---

### Post by shadyedsan on 2008-02-18
you could try downloading a windows 98 boot disc with fdisk on and first delete all non-dos partitions then delete the primary partitions on both discs. failing that just use something like partition magic or a partitioning tool

---

