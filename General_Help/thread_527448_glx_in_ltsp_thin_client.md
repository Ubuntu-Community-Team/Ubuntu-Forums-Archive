---
title: "glx in ltsp thin client"
date: 2007-08-16
forum: General Help
---

### Post by clarknova on 2007-08-16
Is there any hope or theoretical possibility of running hardware-accelerated video in an Edubuntu/ltsp thin client?

I realise that one of the driving motivations for design and implementation of a thin client network is to facilitate the use of slow or old hardware, but I find it terribly convenient to be able to grab any computer at home and boot into a familiar environment. No extra drives or folders to share or sync; my bookmarks and browsing histories are always up to date and intact. So while my thin client machines are not entirely cutting edge, they do hold their own with some 3D applications such as Google Earth, Nexuiz, Quake 4 demo and such when running as an independent Ubuntu install.

However as an ltsp thin client running Ubuntu, the 3D performance is nonexistent. Google Earth runs in GL software emulation mode -- very choppy and usually crashes after a few seconds. Games are likewise effectively unresponsive.

So I'm wondering if there is any possible way to enable glx or open gl or whatever would be specifically necessary to get at least minimal 3D performance on a thin client, whether that would mean installing nvidia's or ati's proprietary drivers into the ltsp chroot environment or whatever.

Any feedback appreciated.

db

---

### Post by markking on 2008-04-03
Have the some problem installing 3D graphic card on ltsp client. Although I use the same graphic card as I use for server. Does anyone know how to solve this problem? installing graphic card such as ATI Radeon in client with ltsp environment.
Reagdrs:guitar:

---

