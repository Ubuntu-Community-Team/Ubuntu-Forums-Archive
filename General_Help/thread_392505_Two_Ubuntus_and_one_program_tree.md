---
title: "Two Ubuntus and one program tree"
date: 2007-03-24
forum: General Help
---

### Post by MaaSTaaR on 2007-03-24
Hello ...

If i have Ubuntu in partition (A) and another Ubuntu in partition (B) , Ubuntu B is new installed and A is old.

Can i make share between A and B in installed programs? i mean when i install new program in A it installed automatically in B and when i install new program in B it installed automatically in A (The programs which i install are .deb packages and compiling from source -sometime-), And transfer all programs which installed in A to B without delete them from A. 

Thanks :)

---

### Post by aysiu on 2007-03-25
What do you mean by "new" and "old"? Are they different versions--6.06 and 6.10, for example? Or do you mean "new" (I just installed it) and "old" (same version but installed a while ago)?

---

### Post by MaaSTaaR on 2007-03-25
Hello ...

I mean

> do you mean "new" (I just installed it) and "old" (same version but installed a while ago)?

---

### Post by aysiu on 2007-03-25
You can do it, but I think it'd be kind of a pain. It involves creating separate partitions for all these directories:
/etc
/lib
/usr

There may be more, but I think those are the ones that programs install to.

---

### Post by Ramses de Norre on 2007-03-25
If you want all those things the same, then why do you have two different installs?

---

