---
title: "Is there a way to just log into the terminal at boot?"
date: 2007-11-05
forum: General Help
---

### Post by ticopelp on 2007-11-05
I searched for some threads on this, but they all involved people *not* wanting to log into the terminal. I do. :KS

Is there any way to just have a terminal on boot, with no GUI? 

Thanks!

---

### Post by knightzor on 2007-11-05
I believe you need to edit:

/etc/event.d/rc-default (as sudo)

and change the:

telinit x

to a non GUI runlevel e.g 1

i haven't tried this before on ubuntu normally its /etc/inittab on other distro's. I'll give it a go on my laptop now

---

### Post by knightzor on 2007-11-05
hmm scratch that, doesn't work for me.

you can stop gnome from loading though by doing the below

cd /etc/rc2.d

sudo mv S30gdm K30gdm

then restart and it will boot you into the terminal interface.

to get into gnome from there run sudo /etc/init.d/gdm start

---

