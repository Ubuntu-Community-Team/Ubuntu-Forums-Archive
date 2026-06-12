---
title: "Broken Desktop after Kernel Upgrade"
date: 2007-04-20
forum: General Help
---

### Post by silverbolt027 on 2007-04-20
Hey Guys and Girls,

I recently upgraded my kernel to the newest 2.6.17-11-generic.

After I rebooted, it brings me to a root terminal...I have to type /etc/init.d/gdm to start the gdm.

Not only is that not secure, but it is annoying...any ideas?

Thanks!

---

### Post by silverbolt027 on 2007-04-20
Nevermind....when I updated the kernel I had to change the /boot/grub/menu.1st file.

I made the mistake of putting single on the end of the boot line, which puts the computer into single user mode!

OOPS!

Thanks anyways... :)

---

