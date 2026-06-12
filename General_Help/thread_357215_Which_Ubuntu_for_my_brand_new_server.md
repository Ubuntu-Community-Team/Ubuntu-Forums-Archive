---
title: "Which Ubuntu for my brand new server?"
date: 2007-02-09
forum: General Help
---

### Post by pebkac on 2007-02-09
Hi Ubuntu users,

I was reading about Xubuntu and tried to find more documentation, but maybe I'm "howto-illeterate".

Anyway, I have here a brand new, just out of the box this morning, IBM System X3400. 

I would like to find an appropriate OS to install that meets as many of the following criteria as possible, but I'm having some difficulty.

- 64-bit dual-core Xeon 5130 processor
- RAID setup (the kind where you have 2 drives and they are mirrors of each other)
- as small of a footprint/resources hog as possible - I liked the idea of Xubuntu, being a minimal installation as possible, and you just add whatever you need on top.
- ability to install packages or sources to do the following: burn DVD for backups, manage print queues, squid, squidGuard, file & app sharing (samba)

I am new to this kind of setup. 

I initially thought Xubuntu was just what I wanted, but I'm not sure if I can run it in 64-bit and in a RAID configuration.

Any insights would be appreciated, thanks!

---

### Post by Jussi Kukkonen on 2007-02-09
[http://www.ubuntu.com/server](http://www.ubuntu.com/server)

Supports AMD64, does not include a graphical desktop by default (at least didn't when I installed it) but you can install them later if you want to. Personally I just SSH into the server (with X forwarding) and run any applications --command line or GUI-- there.

---

### Post by pebkac on 2007-02-09
Thanks for the link, I took a look.

I don't have an AMD64 processor. It's Intel, Xeon, dual-core 64-bit.

Also, there is no information on whether or not that version supports RAID (at least not that I can find).

---

### Post by rich.bradshaw on 2007-02-09
Correct me if I'm wrong, but surely you can just apt-get dmraid to get raid support on any version?

---

### Post by cleentrax on 2007-02-09
Yes, Xubuntu will work just fine with RAID. In general, the parts of Linux that make it a good server have nothing to do with the graphical interface (gnome, xfce, kde, etc.) that sit on top of it.

I don't know whether Xubuntu works in 64bit, but it does very well with RAID 5 on my 32bit server.

---

### Post by MetalMusicAddict on 2007-02-09
I do currently run Xubuntu-Dapper on my server. Headless and controlled with VNC. I will most likely go with Fluxbuntu once its final is released. I like a light GUI on my server.

---

