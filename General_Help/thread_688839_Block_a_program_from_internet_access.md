---
title: "Block a program from internet access"
date: 2008-02-05
forum: General Help
---

### Post by cl_audio on 2008-02-05
Basically, I've been reading around and seem stuck. I've tried various things and all seem unreasonable or just unusable.

AppArmor - Can't seem to find a package for this. (maybe I havent looked enough)
TuxGuardian - Errors compiling (not the only one) and project seems dead.
Guard Dog - Can't just block one program without the risk of loosing functionality in others.
Firestarter - ...


Without sounding rude or ignorant, this is a problem that I see often in these forums and seems that no one has a good recommendation.

I hope bringing this up again will help us to finally bring this problem to an end.


Thanks in advanced!

---

### Post by Thyme on 2008-02-06
Those Firewalls restrict access based on ports. Try learning IP tables to block certain applications on the same port.

---

### Post by nemilar on 2008-02-06
I don't think there's any simple way to block a specific program from accessing the network, the way Windows does it.  Linux does its firewalling based on ports.  

If you give us more information on the program you're trying to block, and your general situation maybe we can find another way to do what you need?

---

### Post by cl_audio on 2008-02-06
It's not really any specific program I am trying to block. I was just searching the forum and noticed that there really is no easy way to do it, so I figured since so much time has passed since the last post I would repost it to see if anyone would have a solution.

An example would be Wine. How would I block any program running through wine? Would I go about blocking wine or a specific program within wine?


Thanks a lot folks, and once again no stress, I'm just trying to help as I can see from the number of posts requesting this is pretty high.

---

