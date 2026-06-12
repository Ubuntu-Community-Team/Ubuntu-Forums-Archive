---
title: "Grub and Hibernation"
date: 2007-04-07
forum: General Help
---

### Post by ($4lDI#1~ on 2007-04-07
Just recently installed Edgy and it's been really good. ATM I'm dual booting using Grub as the boot manager and I have Windows installed on another partition. Before I hibernated for the first time, Grub had three entries (Ubuntu, Ubuntu (safe), Windows) but after hibernation I had this:
Ubuntu
Ubuntu Safe
Ubuntu
Ubuntu Safe
Windows

I'm not sure why the entries for Ubuntu have appeared twice. Can anyone help?

---

### Post by amd-64 on 2007-04-08
The entries come from the file /boot/grub/menu.lst
This file should give more information on the kernels installed on the system. 

One explanation is that you may have installed a new kernel since the last time you booted. The same five entries should be there if the system is restarted and not only after hibernation.

For a quick info on the kernels 
```
grep ^kernel /boot/grub/menu.lst

```

---

