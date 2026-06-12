---
title: "backup and copy"
date: 2007-06-28
forum: General Help
---

### Post by teejayevans on 2007-06-28
2 questions:
If I have a backup of the c:/wubi directory, and need to restore,  what do I need to do? 

If I have a backup, but have a new machine (new hardware, etc), can I copy over since
everything appears to be dynamic (device drivers, tcp , etc)?
TIA, 
TJ

---

### Post by ago on 2007-06-28
> **teejayevans said:**
> 2 questions:
If I have a backup of the c:/wubi directory, and need to restore,  what do I need to do?

Rename c:\wubi.backup -> c:\wubi 

> If I have a backup, but have a new machine (new hardware, etc), can I copy over since
everything appears to be dynamic (device drivers, tcp , etc)?
Most things should work out of the box in the new setup. You might need to reconfigure the X settings and networking, but it should be fairly straightforward.

---

### Post by teejayevans on 2007-07-02
> **ago said:**
> Rename c:\wubi.backup -> c:\wubi 
Most things should work out of the box in the new setup. You might need to reconfigure the X settings and networking, but it should be fairly straightforward.
I also assume that I should backup the boot.ini file and restore it as well.
I'll have to give the copy method a try...
Thx

---

