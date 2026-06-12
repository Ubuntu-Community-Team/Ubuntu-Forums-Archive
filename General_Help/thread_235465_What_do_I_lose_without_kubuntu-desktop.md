---
title: "What do I lose without kubuntu-desktop"
date: 2006-08-13
forum: General Help
---

### Post by Jucato on 2006-08-13
I'm planning to do a server install (minimal install from the Alternate Install CD), and then just install kde-core, instead of kubuntu-desktop. 

My question would be what do I lose by not installing kubuntu-desktop? I know that I will not be getting the kubuntu default settings, for one. But are there other side effects that I might encounter? Will I have problems upgrading packages? Or will I have dependency problems?

A side/related question would be, if I did a server (minimal) install and then installed kubuntu-desktop, would I end up with a smaller, lighter system or will it be exactly, as in exactly the same if I did a normal Kubuntu install?

Thanks!

---

### Post by PriceChild on 2006-08-13
installing kubuntu-desktop will give you the same system as a normal install.

As i understand it, installing kde-core will install all its dependencies (use aptitude) and should allow you to boot into a graphical environment.

All the necessary applications will be installed, however i can't see it being any faster than a kubuntu-desktop install. It just won't have as much functionality.

Pricey

(mostly guessing)

---

### Post by Ramses de Norre on 2006-08-13
kde-core just installs the kde environment without all the other applications in kubuntu-desktop. So basically I think you get kde and then have to install only the applications you use.

---

### Post by Jucato on 2006-08-13
Well, I was hoping that doing a minimal install, installing only the stuff I need/use, will probably make a faster system.

There are many things installed by default in Kubuntu that I don't need. If I remove them, kubuntu-desktop is also removed. So I thought about starting with no kubuntu-desktop anyway, so that I could pick and choose.

Any adverse effects on upgrading? for example, will I still be able to receive notifications from Adept Notifier and still upgrade without problems?

Thanks a bunch!

---

### Post by Ramses de Norre on 2006-08-13
The programs you have will be upgraded as usual, the only thing you'll miss are things added later on to kubuntu-desktop, but I don't think you'll want them anyway since your purpose is to make your system lightweight.

---

### Post by kinematic on 2006-08-13
i setup my box exactly the way you discribe.....server install and added kde-core and customized it further from there and it's running very nicely and updates heve never been a problem.
i'd say go for it ;)
(btw...don't forget to install xserver-xorg,that doesn't get installed along with it).

---

