---
title: "Linux 12.10 bug"
date: 2012-10-20
forum: General Help
---

### Post by pterpan on 2012-10-20
When starting up my computer while having an external monitor connected - it reacts like this: [http://imgur.com/a/PPOIM]("http://imgur.com/a/PPOIM")

I have a Dell XPS M1530, and installed ubuntu 12.10 yesterday. Now during startup this is happening and I have no Idea why.
During this instable state I can login, but I am logged out just as fast.

If I boot up the pc, and then connect the monitor it works just fine. The monitor is a hp 1902.

Thank you!

---

### Post by grahammechanical on 2012-10-20
Are you using a proprietary video driver? Have you tried using the proprietary driver's settings utility to set a profile for that monitor? Or something like that.

I have a desktop. So, our setups are not the same. But during development of 12.10 there were many issues with the Nvidia driver, including the messed up screen images that you show. This was happening both at the log in screen and the desktop.

Have you tried Recovery mode>Resume? You may need to de-activate the proprietary video driver and use Noveau.

You will find an Additional Drivers tab in the Software Sources utility. We do not have a separate Additional Drivers utility any more in 12.10

Regards.

---

### Post by pterpan on 2012-10-20
Hey! Thanks for the quick answer, really! Though I have to say, since I'm neither English or very good with linux, I don't completely understand your response. Hehe, sorry. ^^'

But if I understand it somewhat correct, It could be enough to switch drivers? This is my current setup of "additional drivers": [http://i.imgur.com/00dQ2.png]("http://i.imgur.com/00dQ2.png")

Again, thanks a lot!

---

### Post by sandyd on 2012-10-20
Try selecting either the first option or the second (in the above screenshot) and applying it.

---

