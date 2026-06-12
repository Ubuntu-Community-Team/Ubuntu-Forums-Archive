---
title: "nVidia Drivers + Xorg = Freeze :\ !!"
date: 2005-04-27
forum: General Help
---

### Post by MarioFuentes on 2005-04-27
After the last upgrade from Hoary-beta to Hoary, my system began to undergo freezing after random times  :-x. Investigating the problem  ](*,) , I concluded that the cause has relation with nVidia's drivers, because replacing the configuration of the Xorg with "nv" driver, the system works stable.
When the system is congealed, I can accede to from another machine using ssh, and then I can appreciate that the process of the X is consuming all the processor (99% cpu usage) :-?.
I don't know if this is a know bug, but is very disagreeable lose the confidence in my machine.

Friends, help me!! I need GLX acceleration! :)

---

### Post by nocturn on 2005-04-28
There are multiple threads about this on the forum.  It is related to the 7174 version of the Nvidia drivers.

Here is the bugid:
[https://bugzilla.ubuntu.com/show_bug.cgi?id=7183](https://bugzilla.ubuntu.com/show_bug.cgi?id=7183)

Basicly, you coult try reverting to the old version.  Or install it from the Nvidia installer (you will need kernel-headers and build-essentials).

I'm still working on this on my own system, but there are many, many users plagued by it.

---

