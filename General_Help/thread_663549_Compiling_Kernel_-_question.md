---
title: "Compiling Kernel - question"
date: 2008-01-10
forum: General Help
---

### Post by Mithrilhall on 2008-01-10
I'm attempting to compile a kernel. Before I compile and reboot using the new computer I have two network cards working. Yet, after compiling my kernel and booting off of it I only have one. Issuing a 'sudo ifconfig eth1 up' doesn't work.

I'm using my current config file for the new kernel. Is there a way to keep all the current drivers/modules when compiling a new kernel?

---

### Post by geraldm on 2008-01-11
In the top directory of the unmodified kernel source issue the command
make mrproper
# then copy your older config file into that directory as ".config" 
# Then issue the command 
make oldconfig
# You may have to answer a few questions if you are upgrading to a newer source.

After that, you can make the kernel and its modules.

Gerald

---

