---
title: "fglrx or default driver?"
date: 2007-02-06
forum: General Help
---

### Post by DrAwesomePhD on 2007-02-06
Hi, sorry if this is a silly question but i've been googling and cant really find the answer :( anyway, a quick answer is appreciated ;)

So, I was wondering what driver I should use for ubuntu, i want to use Beryl and Wine/Steam (well) and have an X800 pro AGP 256mb.  I'm not sure what the fglrx driver is, but should i install it or stick with the default ati driver from dpkg-configure xserver-xorg ?

edit: running edgy

---

### Post by zero-9376 on 2007-02-06
fglrx is the proprietary ati driver and will give you better performance on that card than the open source radeon or ati drivers. if you want 3d effects use xgl as aiglx is not supported. 

cant comment on game performance as i havent played any using wine, my guess is that it would be better to use use normal x rather than xgl for that.

---

### Post by DrAwesomePhD on 2007-02-06
I was just following (another) tutorial on howto install drivers and it said "Make sure [fglrxinfo] says ATI and not Mesa" but mine is consistantly saying Mesa :-/ anyone know what i'm doing wrong?  The x800 is a popular card... i figure its relatively supported.

---

