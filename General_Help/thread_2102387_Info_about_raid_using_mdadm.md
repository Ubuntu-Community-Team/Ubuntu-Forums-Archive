---
title: "Info about raid? using mdadm"
date: 2013-01-07
forum: General Help
---

### Post by sniffysniper on 2013-01-07
I'm running ubuntu server 12.10 and my first (and only) drive is running out of space so before i proceed buying new drives I've got some questions about using mdadm raid.

- If I buy a disk can I later on expand it with another drive using mdadm?
- If my system (or boot drive) fails while using raid5 can I easily transfer this to a new machine?

---

### Post by catalin.vasilescu on 2013-01-07
You can expand it later and you can transfer the hdd to a new machine and rebuild it.

---

### Post by sniffysniper on 2013-01-07
Is that a straight forward process?

---

### Post by rubylaser on 2013-01-07
> **sniffysniper said:**
> Is that a straight forward process?

Yes, transferring to a new machine is a very simple process. You just need to apt-get install mdadm on the new host.  Each disk in your mdadm has all of the array's important metadata stored in it's superblock.  If you use the Desktop version of Ubuntu, your array should be autodetected on the new machine.  The server version is very easy to import from the command line as well.

---

