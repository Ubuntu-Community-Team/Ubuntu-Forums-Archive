---
title: "Cannot login using Xorg"
date: 2019-12-07
forum: General Help
---

### Post by hellocatfood on 2019-12-07
I'm using Ubuntu 19.10 on a Dell XPS 13 laptop. Since I upgraded to 19.10 I haven't been able to log in using an Xorg session. When I type my password in the proces just gets stuck on the purple screen and the Desktop never loads. I don't have this problem with Wayland, but some of the software I use doesn't work with Wayland.

I have no idea where to begin to diagnose this problem so any help is appreciated.

---

### Post by dragonfly41 on 2019-12-07
Possibly try installing [gnome-flashback]("https://www.debugpoint.com/2018/05/how-to-install-classic-gnome-flashback-in-ubuntu-18-04-lts/") for login session until you can pin down the problem?

---

### Post by deadflowr on 2019-12-07
> some of the software I use doesn't work with Wayland.
Do any of these require authentication, or are they just more or less random apps?
BTW, this all seems backwards to common Wayland/Xorg issues..

---

### Post by hellocatfood on 2019-12-08
> **deadflowr said:**
> Do any of these require authentication, or are they just more or less random apps?
BTW, this all seems backwards to common Wayland/Xorg issues..

More or less random apps. I'm having problems with Helm (synthesiser), Peek (screen capture), Pure Data (visual programming language), Zim (desktop wiki), and sometimes copy/paste doesn't work.

Basically Wayland isn't good and I want to use Xorg which I know works.

---

### Post by hellocatfood on 2020-04-23
Just upgraded to Ubuntu 20.04 and logging in via X still isn't working...

I want to be able to report a bug about this but don't know where to look for error messages.

---

