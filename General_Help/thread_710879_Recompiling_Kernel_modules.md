---
title: "Recompiling Kernel modules"
date: 2008-02-28
forum: General Help
---

### Post by dmitrijledkov on 2008-02-28
Hmmm I have succesfully managed to compile 2.6.24.3 kernels with some patches but it seems to me that I'm missing all kernel modules from ubuntu generic kernel.

How do I find out which modules are installed in current kernel?
Where/how rebuild them for a custom build kernel?
How do I know if I need all of these kernel modules?

Thanks for help.

---

### Post by pointone on 2008-02-29
"lsmod" will show you the currently loaded modules, "modprobe -l" will find all the modules on your system. I don't know how else to tell.

As for knowing if you need the kernel modules, are you missing any functionality? One of the benefits of a custom kernel is slimming down on unnecessary modules, so I wouldn't recommend just blindly rebuilding everything.

---

### Post by dmitrijledkov on 2008-02-29
Thanks.

---

