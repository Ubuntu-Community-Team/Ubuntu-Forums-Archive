---
title: "Resize Partition ?"
date: 2007-08-02
forum: General Help
---

### Post by cessna_89702 on 2007-08-02
I deleted my windows ntfs partition which had around 40GB on it. Can I put the unallocated space on my ext3 ubuntu partition? I tried with the paritioner on the live disk and it wouldnt do it for some reason.

---

### Post by merlinus on 2007-08-02
Try gparted live cd:

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

-merlin

---

### Post by bodhi.zazen on 2007-08-02
+1 merlinus

FYI The version of gparted on the gparted live CD is newer and has some more advanced features. The issuer is older versions of gparted can not add unallocated space to a partition unless if FOLLOWS the partition. Newer versions do not have this limitation.

---

### Post by cessna_89702 on 2007-08-03
thanks

it worked 
took 4 hours though

---

