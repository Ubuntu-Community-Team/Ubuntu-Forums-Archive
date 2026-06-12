---
title: "amarok and kaffine will not start"
date: 2006-10-31
forum: General Help
---

### Post by cptjaben on 2006-10-31
When I try to run Amarok or Kaffine, they simply do not run. When I look at the gnome system monitor, I see that by clicking them it will start them but nothing happens and then after about 20 seconds they are removed from the processes list. I tried reinstalling them with synaptic, but it had no effect. I'm running them both with Xine which may have something do to with it but i don't know. Does anyone know how to fix it or more importantly how one could make the work again be it complete uninstallation and reinstallation. Thanks

---

### Post by elettronicha on 2006-11-01
Please, report the output you get launching the programs by a terminal window.

PS: look at our two avatars! :D

---

### Post by cptjaben on 2006-11-02
when i try and run amarok in the terminal i get: Floating point exception (core dumped)


When I type kaffeine in the terminal, I get

Floating point exception (core dumped)

DCOPClient::attachInternal. Attach failed Could not open network socket
DCOPClient::attachInternal. Attach failed Could not open network socket
Link points to "/tmp/ksocket-john"
Link points to "/tmp/kde-john"
DCOP aborting call from 'anonymous-7730' to 'kded'
kded: ERROR: Communication problem with kded, it probably crashed.
DCOP aborting call from 'anonymous-7711' to 'kaffeine'
ERROR: Communication problem with kaffeine, it probably crashed.

Anyone know what this means? In addition k3b will not start, but i doubt it is related.

---

### Post by Polygon on 2006-11-02
that might be a memory or processor error, maybe trying running the programs from a earlier kernel and see if you get the same error, and maybe try running the memtest86 test that comes with ubuntu (select it via grub and try two or more tests to see if it generates any errors)

I've googled this and there does not seem to be a definite cause

---

