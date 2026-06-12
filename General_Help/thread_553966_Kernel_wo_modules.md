---
title: "Kernel w/o modules"
date: 2007-09-18
forum: General Help
---

### Post by fireonyx on 2007-09-18
I have an assignment to rebuild my kernel without any modules needed, aka everything build in.  Is there a nice command to transfer lsmod results into the .config file?  Or is there a nice howto somewhere on the subject?

---

### Post by dcstar on 2007-09-19
> **fireonyx said:**
> I have an assignment to rebuild my kernel without any modules needed, aka everything build in.  Is there a nice command to transfer lsmod results into the .config file?  Or is there a nice howto somewhere on the subject?

There are kernel build HOWTOs in the "Tips and Tricks" forum, you just do the config with everything built in and not as a module - but you will end up with a MASSIVE kernel file full of code that will not ever be used.

Modules exists as things to be used when they are actually needed, your assignment may be to find how fat a kernel can get by not using modules.........

---

### Post by fireonyx on 2007-09-21
The idea is to build in only the hardware that my laptop needs.

---

