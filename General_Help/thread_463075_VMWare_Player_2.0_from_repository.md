---
title: "VMWare Player 2.0 from repository?"
date: 2007-06-03
forum: General Help
---

### Post by Finch75 on 2007-06-03
Hello everybody,

VMWare released version 2.0 of its "VMware player" almost four weeks ago.

Will it show up in the Ubuntu repositories if I wait "a little longer"? Or does Ubuntu only add "minor updates" and I have to wait for 7.10?

I could probably get it installed from the rpm on the VMWare site, but I always prefer Synaptic if available ;-)

Is is worth waiting? Or hopeless?

---

### Post by veloce on 2007-06-04
> **Finch75 said:**
> Hello everybody,

VMWare released version 2.0 of its "VMware player" almost four weeks ago.

Will it show up in the Ubuntu repositories if I wait "a little longer"? Or does Ubuntu only add "minor updates" and I have to wait for 7.10?

I could probably get it installed from the rpm on the VMWare site, but I always prefer Synaptic if available ;-)

Is is worth waiting? Or hopeless?

What does this version do that the earlier doesn't?  VMWare server is available from the repositories now - do you have any reason not to switch to this?

---

### Post by Finch75 on 2007-06-04
> **veloce said:**
> What does this version do that the earlier doesn't?

Are you asking because you are curious or are you questioning my question?
Player 2.0 obviously has quite a few improvements over 1.0 or else it wouldn't be 2.0. I've read some info when it was released and don't remember most of it. Two points stand out: Better SMP support (I know about SMP support for the guest in Workstation 6, but don't know about Player 2) and USB 2.0 - support in Player.
I have suffered from an SMP bug in Player 1.0x (and it still annoys me quite a bit!), so I'd like to upgrade. Also, I tried running a certain USB device in a VM and it failed, so I'd like to upgrade.
Those bugs/problems are the main reason, but it also adds "shared folders", which should make my life a little easier...

> **veloce said:**
>  VMWare server is available from the repositories now - do you have any reason not to switch to this?

VMWare server is a different product. It does *not* replace Player. Both Server and Player have different strengths and weaknesses. I've been using player since it was released (back when Server was not free) and have never used Server. That's a good reason to stick with Player first, I really have enough new programs to learn in Linux... (yes, I'm a "power user" and there's a LOT that I don't find in a standard installation... and even more that is very different from Windows...)

Sooo... back to the question: Will a "major upgrade" (1.0.4 -> 2.0) be integrated into the Ubuntu repositories or will I have to wait for 7.10 or do a manual installation?

---

### Post by veloce on 2007-06-04
> **Finch75 said:**
> Are you asking because you are curious or are you questioning my question?


I was curious.  I'm using vmware server a lot and thought player was just a toy version (being the original freebie) but that maybe v2 had some new killer stuff.  

So there is at least one reason to keep after player 2:
Using SMP in vmware server is a real dog on a dual core host.  It is much better to let ubuntu use the two cores to run a single core windows vm.

Sorry I was ambiguous. (and that I'm no help with your actual question.)

---

