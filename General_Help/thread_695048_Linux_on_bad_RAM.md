---
title: "Linux on bad RAM"
date: 2008-02-12
forum: General Help
---

### Post by JordanII on 2008-02-12
I have been using Linux for a while and I really like it. Anyway, I have a laptop (an older thinkpad model) that has some bad RAM (about 30MB of RAM is bad.) Is there a Linux distro that will work on it? (I've tried Ubuntu 7.04, Xubuntu 7.10, PCLinuxOS Gnome, Mandriva 2008, and Shift and none of them worked.) Thanks!

No... it doesn't directly have anything to do with ubuntu, but whatever.

---

### Post by chadeldridge on 2008-02-12
Bad memory is bad memory, the OS you install that will access the memory has no bearing on your issue.  Anything from Dos to Unix that you install on that machine when accessing the bad memory block is going to lock up or do something undesirable.  Memory is very cheap now and I would recommend at least replacing the chips if they are removable for a few $$$.

---

### Post by JordanII on 2008-02-12
> **chadeldridge said:**
> Bad memory is bad memory, the OS you install that will access the memory has no bearing on your issue.  Anything from Dos to Unix that you install on that machine when accessing the bad memory block is going to lock up or do something undesirable.  Memory is very cheap now and I would recommend at least replacing the chips if they are removable for a few $$$.

Unfortunately they aren't removable. :P I saw this [http://rick.vanrein.org/linux/badram/](http://rick.vanrein.org/linux/badram/) and thought maybe there was a distro that had that kernel or something like it.

---

### Post by danwood76 on 2008-02-12
are you sure they arent removable?

even some of the really old (10+ years) laptops and desktops ive seen have removable ram.
with laptops you do sometimes with the old ones have to rip them to pieces to get them out.

---

### Post by russell.h on 2008-02-12
That BadRAM project looks interesting. Unfortunately, it doesn't seem to be included with the Kernels in the Ubuntu repositories. 

Here is some information on how you could go about building your own kernel with the BadRAM patch: [https://help.ubuntu.com/community/BadRAM](https://help.ubuntu.com/community/BadRAM)

---

