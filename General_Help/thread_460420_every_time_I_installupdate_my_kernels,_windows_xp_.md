---
title: "every time I install/update my kernels, windows xp gets wiped from grub menu.lst"
date: 2007-05-31
forum: General Help
---

### Post by harty83 on 2007-05-31
How do I prevent this?  Its getting a little aggravating having to manual add windows back to my menu.lst every time I install/update a kernel.

Thanks!
Alan

---

### Post by tkjacobsen on 2007-05-31
All entries between 
### BEGIN AUTOMAGIC KERNELS LIST
and
### END DEBIAN AUTOMAGIC KERNELS LIST
is wiped with each new kernel install. Add your windows entry before the first of after the last.

---

### Post by harty83 on 2007-06-04
Thanks!

---

