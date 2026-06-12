---
title: "Issues compiling modules for Virtualbox"
date: 2007-10-04
forum: General Help
---

### Post by Skilldibop on 2007-10-04
When I invoke "/etc/init.d/vboxdrv setup"
It attempts to compile the module and looks promising for about 15 seconds. Then it throws up a fatal error and tells me to check dmesg to find out what bjorked.

dmesg reveals this....

vboxdrv: disagrees about version of symbol boot_cpu_data
vboxdrv: Unknown symbol boot_cpu_data


What can I do about this?  Kernel is 6.06 Server and I'm not massively skilled in Linux so the more simple the fix the better.

---

### Post by Skilldibop on 2007-10-05
Anyone?

---

### Post by strikenowhere on 2007-11-12
I'm running across the same problem myself...did you happen to come across a solution?

Thanks,
Greg

---

