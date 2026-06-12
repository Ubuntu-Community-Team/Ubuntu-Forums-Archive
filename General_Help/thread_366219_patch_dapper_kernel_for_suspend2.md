---
title: "patch dapper kernel for suspend2"
date: 2007-02-20
forum: General Help
---

### Post by frogotronic on 2007-02-20
How do I figure out the correct suspend2 patch for the 2.6.15.7 ubuntu kernel?

---

### Post by energiya on 2007-02-21
it should be a patch made exactly for your kernel version.

---

### Post by frogotronic on 2007-02-21
> **energiya said:**
> it should be a patch made exactly for your kernel version.

okay, so how do I find that specific a patch?  None of those posted on Suspend2 work

---

### Post by energiya on 2007-02-21
The only patch for the 2.6.15 kernel is [this (2.6.15.1)]("http://www.suspend2.net/downloads/all/suspend2-2.2-for-2.6.15.1.tar.bz2"). I don't see anyting for 2.6.15.7 . You could allways update... if you don't like the new stuff just download an older one with suspend 2 support (I have 2.6.18.6 allready patched kernel).

---

### Post by frogotronic on 2007-02-21
I'll try this patch and post my results.  I was using higher number patches, ie. rc15, rc 16 for the 2.6.15 kernel - probably my newbness.

Thanks!

- CH

---

### Post by frogotronic on 2007-02-22
okay, just another quick question...

Should I compile the suspend2-userui module (along with the nvidia module) into the kernel when I compile the the kernel with the suspend2 patch?

Thanks
CH

P.S.  Is the 2.6.15.7 kernel newer than the 2.6.18.6 kernel?  I thought that the lesser (smaller) the kernel number, the older it was...

---

