---
title: "[SOLVED] Removing Older Kernels"
date: 2008-05-15
forum: General Help
---

### Post by ghindo on 2008-05-15
I've had my Ubuntu install for a while, and now I'm noticing that old kernels are piling up.  I know it's good to keep an older kernel around to boot into if I'm ever having trouble with the current one, but how do I remove older kernels?  What about GRUB?

((I'm using Ubuntu 8.04, by the way)

---

### Post by MaindotC on 2008-05-15
Hi, ghindo.  If you want to keep the older kernels just in case but don't want to see them in the grub menu, you can edit this file with root permissions: /boot/grub/menu.lst.  This file has all the entries you see on the grub boot screen.  If you comment out the lines using #'s it won't display them.

If you want to completely remove the kernel, you can use the following in a command line:
```

sudo apt-get remove linux-headers-KERNEL_NAME

```

where KERNEL_NAME is the numeric version of the kernel you want to remove.  For example, I'm currently using the 2.6.22-14 kernel, so here's what it look like when I enter the command and press the tab button twice to display all possibilities:
```

311@a34lkj2348dsf311-laptop:~$ sudo apt-get remove linux-headers-2.6.22-14
linux-headers-2.6.22-14          linux-headers-2.6.22-14-generic

```

---

### Post by ghindo on 2008-05-15
Much appreciated, thank you :)

In the process, I found I could also do it using Synaptic.  Go figure.

---

### Post by MaindotC on 2008-05-15
Yay do I get a star :)

---

### Post by ghindo on 2008-05-15
Absolutely :p

---

