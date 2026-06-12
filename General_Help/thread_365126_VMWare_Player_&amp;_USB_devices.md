---
title: "VMWare Player &amp; USB devices"
date: 2007-02-19
forum: General Help
---

### Post by PaulFXH on 2007-02-19
I'm using vmware player with Edgy as host and Windows XP as guest OS. It really works extremely well and is so much more convenient than dual booting for short-term moves from Ubuntu into Windows.
However, I'm a little puzzled as to why there seems to be a shortage of information on how to configure the Guest OS .vmx file.
In particular, although all of my three connected usb devices are picked up and operate without problems, I cannot have more than two of them connected at any one time.
So, if my scanner and printer are connected and I want to access my usb hdd, one of the other devices automatically disconnects.
It's really no major inconvenience but I would like to know if this is configurable or is an innate  and untouchable feature of vmware player that no more than two usb devices can be connected at a time.
Anybody know?

---

### Post by capdog on 2007-02-20
Hmm I think info is scarce because the point of VMWare player is that it's meant to be simple. If you need to do that kind of config, you should be using VMWare workstation... it's their upgrade path that they try get you onto!

But as for your question about max number of USB drives, maybe ask on the VMWare support forums! :)

---

### Post by PaulFXH on 2007-02-20
Thanks for your reply.
Actually, vmplayer does everything I need right now and, besides, it's free!
The usb limitation thing is a very minor inconvenience but I'd like to know if it's real or have I messed up my configuration somehow.
Cheers
Paul

---

### Post by calagan on 2008-01-09
I'm not sure if this actually relates to your problem, but my WinXP VM had no USB ports whatsoever and I fixed it by opening the .vmx file in my VM's folder with a text editor and added the line below:
```
usb.present="TRUE"
```
I noticed however that the emulated USB controller was a 1.1, so maybe you're having this problem because your USB 2.0 devices are not backward compatible.

---

