---
title: "Windows no longer boots after ubuntu install"
date: 2007-08-20
forum: General Help
---

### Post by designer17 on 2007-08-20
Hello, I installed ubuntu on a portable hard drive a while ago and haven't been able to boot into windows ever since the install.  Grub is loaded on my portable hard drive and I can't seem to figure out why I can't boot windows.

When I power on my laptop with my portable hard drive unplugged I get something like error 21, can't remember exactly.

I had tried doing the system restore and fixing as well as creating a new mbr but nothing seems to of worked.  I am sure I could do a complete reinstall of windows but really would like to avoid that option if possible.

Any help would be greatly appreciated. Thanks in advance.

---

### Post by jnorthr on 2007-08-20
Any chance you can get grub to show you your partitions ? It would be interesting if we could know if grub 'sees' your fat32 windows partition or not. If not grub may only offer you the choice of booting from partitions on  the same disk as it is on. 

Perhaps grub installed itself over the master boot record on your main hard drive hence why you cannot see the windows partition. Can you boot into ubuntu on the removable drive ?

---

