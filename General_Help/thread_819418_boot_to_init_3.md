---
title: "boot to init 3"
date: 2008-06-05
forum: General Help
---

### Post by destructchaos on 2008-06-05
is there a way to boot to init 3 instead of init 5?

thanks.

---

### Post by spiderbatdad on 2008-06-05
Ubuntu uses upstart. There is no /etc/inittab by default. You  have to create it. 
[http://www.linux.com/feature/125977](http://www.linux.com/feature/125977)

---

### Post by phidia on 2008-06-05
I'm not at my linux computer right now but I believe the file you want to edit is /etc/init.d 
the runlevels are set there.

---

### Post by bingoUV on 2008-06-05
Why do you want to boot to init 3? It won't make any difference. 

If you don't want X server/gdm/graphical login to start, you will have to remove the link to gdm from /etc/rc3.d. Then booting to runlevel 3 will not start X server on its own.

---

### Post by spiderbatdad on 2008-06-05
:popcorn:
See the readme file in that directory: /etc/rc3.d

---

