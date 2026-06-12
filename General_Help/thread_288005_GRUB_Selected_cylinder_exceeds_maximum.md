---
title: "GRUB: Selected cylinder exceeds maximum"
date: 2006-10-29
forum: General Help
---

### Post by Deomanh on 2006-10-29
Hi folks

I recently upgraded to edgy (from scratch). But after some reboots today and some custom kernel recompilations, I suddenly can't boot into _any_ kernel unless it's on single user mode, and I gather that's nothing more than a parameter on boot? :confused: . By any I mean even the generic and 386 kernels from the ubuntu repositories. GRUB returns "Error 18: Selected cylinder exceeds maximum supported by BIOS". I've tried reinstalling kernels, reconfiguring packages, updating grub, but so far I've gotten nowhere ](*,). Naturally I've also checked the BIOS but everything seems quite normal.

Ideas?

Oh and I can boot into Windows without a problem as well.

---

### Post by Deomanh on 2006-10-29
Through trial and error I discovered that by commenting out the "savedefault" lines in menu.lst it all works again. I also found bug #66278 ([https://launchpad.net/distros/ubuntu/+source/grub/+bug/66278](https://launchpad.net/distros/ubuntu/+source/grub/+bug/66278)) which may be related to this. Any solutions would be appreciated, though it apparently isn't that important anymore.

---

### Post by rumli on 2006-11-03
Thanks very much for this workaround!  :)

I ran into this problem on a couple of machines after I changed ```
default 0
``` to ```
default saved
``` in my /boot/grub/menu.lst.

Commenting out the "savedefault" in the Ubuntu section of /boot/grub/menu.lst as you suggested resolved the issue.

---

