---
title: "AWN not working"
date: 2008-06-07
forum: General Help
---

### Post by jalvarez53 on 2008-06-07
I'm running 8.04
I recently installed avant-window-navigator and the manager. the awn manager works but awn isn't. I've also noticed when I enable the desktop cube it doesn't work either. I have suspicions that its compizfuzion but I don't know how to detect that kind of issue. Any help?

---

### Post by chunchengch on 2008-06-07
There are two options to activate AWN:

1. open a terminal and type command [COLOR="Red"]avant-window-navigator[/COLOR]

2. go to Applications > Accessories, then you will find the launcher


if you want AWN to be loaded automatically when you boot Ubuntu, open System > Preferences > Session and create a new session

Name: [COLOR="Red"]Avant-Window-Navigator[/COLOR]
Command: [COLOR="Red"]avant-window-navigator[/COLOR]

---

### Post by jalvarez53 on 2008-06-07
No when I load the window-navigator A popup comes up in the upper left of my screen and it just dissapears.

---

### Post by fidamehran on 2008-06-11
I have similar kind of problem. I installed AWN. But it happened to give some trouble. Every time I started it, it started okay, then it hid from eye's view. That's okay if I can roll over the mouse to the bottom to make it re-emerge. But, No. It doesn't come up. Re-running the app from menu starts another instance of AWN and that also in due course vanishes.
I can see the tip of AWN at the bottom of my desktop, but it doesn't come up.
I tried to elevate the position of the AWN dock through its preferences, but still no effect.
I think I'll stop using AWN for now and head for Cairo (Cairo-Dock). Haven't tried that yet.

---

### Post by moonbeam on 2008-06-11
> **jalvarez53 said:**
> No when I load the window-navigator A popup comes up in the upper left of my screen and it just dissapears.

Almost certainly means there is no compositor available.  In this case probably meaning the desktop effects cannot be enabled.

You might want to enable to composite support in metacity instead.

---

### Post by moonbeam on 2008-06-11
> **fidamehran said:**
> I have similar kind of problem. I installed AWN. But it happened to give some trouble. Every time I started it, it started okay, then it hid from eye's view. That's okay if I can roll over the mouse to the bottom to make it re-emerge. But, No. It doesn't come up. Re-running the app from menu starts another instance of AWN and that also in due course vanishes.
I can see the tip of AWN at the bottom of my desktop, but it doesn't come up.
I tried to elevate the position of the AWN dock through its preferences, but still no effect.
I think I'll stop using AWN for now and head for Cairo (Cairo-Dock). Haven't tried that yet.

Do you have auto hide enabled in awn-manager?

---

### Post by Scunizi on 2008-06-11
I hadn't run AWN since upgrading to Hardy from Gutsy.  I typically keep effects off so there's no compositing.  Being brain dead this morning it took me a while to realize I needed compositing turned on to activate AWN.  When I did I found the 5 attempts to load AWN without compositing suddenly loaded.. all at once.. giving very slow performance to AWN and some strange effects with the awn icons s.l.o.w.l.y. crawling onto the Awn bar.  I had to kill 4 of the processes to get back it's snappy-ness and proper operation.

---

