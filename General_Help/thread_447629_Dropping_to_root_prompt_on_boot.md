---
title: "Dropping to root prompt on boot?"
date: 2007-05-18
forum: General Help
---

### Post by Carr0t on 2007-05-18
My Kubuntu 6.06 LTS has recently started doing.... strange things. Namely, whenever I reboot (rarely, but more frequently recently as i try to work out what is causing this) it starts up, appears to get to the end of runlevel 1, and then dumps me at a root prompt with no request for password or similar. This is what i'd normally expect the system to do in the case of some kind of major startup failure. However there is nothing to indicate a problem in /var/log/messages or dmesg, and if I just exit the root prompt the system enters runlevel 2 and continues booting as normal, giving me X and everything I would normally expect.

So what on earth is causing it to drop down to that root prompt in the first place? The only thing I could think of was that it was spawning the sulogin listed in inittab due to failing to start the init scripts properly or something, but that should respawn every time it gets exited, not allow the boot process to continue as normal, and I can't see how the other init scripts could be failing if all my expected services are running.

Any ideas?

---

### Post by vtel57 on 2007-05-18
Can we see a copy of you /boot/grub/menu.lst, please? Also, please post the contents of your /boot directory. This will give us a start at troubleshooting your problem.

---

