---
title: "Intel537EP Install Issues"
date: 2005-11-02
forum: General Help
---

### Post by bobthebiscuit on 2005-11-02
I'm a little newer to linux/Ubuntu, but I've generall done pretty well with all the boxes I've set up. This time, though, I need to get a winmodem (Intel 537EP chip) working, and for once I just can't figure it out. I have followed the instructions in this thread: [http://ubuntuforums.org/showthread.php?t=36762&highlight=Intel+537](http://ubuntuforums.org/showthread.php?t=36762&highlight=Intel+537)

but the modem driver refuses to install. I don't have a choice, I have to get this modem working. But the final error message I'm getting is: error loading Intel537
ERROR: Module Intel537 does not exist in /proc/modules

There were various errors and warnings throughout the "Make 537" part of the plan, but I can't figure them out. I have installed gcc 3.4 and the kernel headers and the linux headers and my headers is achin'.

Can someone go through this, if it makes sense to you, and maybe help me out?

---

### Post by bobthebiscuit on 2005-11-03
bump?

---

### Post by az on 2005-11-03
I would tell you to use and intel or a lucent modem.  What do I know?  I used winmodems with linux back when the connexant drivers were free and I used to reccomend that.

These devices have proprietary drivers and that is the problem.  I have not used my modems in over a year....


Any hardware modem should work, be it internal or external.  Beware, there is no such thing as a semi-hardware modem.  It is just a software modem with an extra chip.  It still requires proprietary drivers.

---

### Post by Swab on 2005-12-03
[QUOTE=bobthebiscuit]
ERROR: Module Intel537 does not exist in /proc/modules
[/QUOTE]

Same problem here... anyone know whats going on?

Edit: Actually I hadn't installed the patch... However now I cant install that..  it just hangs doing no thing after I "patch -p0 ... "

---

### Post by the_pc_dude on 2005-12-12
try patch -p1 it might not work,but give it an shot.

---

