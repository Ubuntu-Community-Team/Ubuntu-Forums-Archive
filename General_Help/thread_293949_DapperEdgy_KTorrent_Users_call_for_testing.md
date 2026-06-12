---
title: "Dapper/Edgy KTorrent Users: call for testing"
date: 2006-11-05
forum: General Help
---

### Post by jdong on 2006-11-05
REFERENCE:
[http://buntudot.org/people/~jdong/ktorrent/bug70529/](http://buntudot.org/people/~jdong/ktorrent/bug70529/)

bug ticket with technical details: [https://launchpad.net/products/edgy-backports/+bug/70529](https://launchpad.net/products/edgy-backports/+bug/70529)

I have ported some enhancements for KTorrent from 2.1's alpha branch to 2.0.3. They are:

 * DHT compatibility with uTorrent
 * Removal of no-longer-existent Fast Set extensions to Bittorrent protocol

These should allow you to find more DHT nodes and faster (and hence more peers via DHT), and also may allow you to connect to some peers that would refuse KTorrent before, due to an unknown extension to the protocol.

debs are available for Dapper and Edgy users. They work great for me on both, but I'd like to subject these packages to heavier testing. Eventually they will go into the Backports repositories of both distributions. If you have some time and are willing to subject your computer to this kind of testing, I'd appreciate it. Note the versions: one has 6.06 in it, the other has 6.10 in it. Pick the right one for your version of Ubuntu please!

**DISCLAIMER**: While the changes are minimal and these packages work fine for me, they are beta testing packages, and should not be used on systems with valuable data. If you do not feel comfortable testing other people's packages, you shouldn't download or install these packages!

---

### Post by cybrid on 2006-11-13
Hi, I just installed Ktorrent from [http://buntudot.org/people/~jdong/ktorrent/svn-edgy/]("http://buntudot.org/people/~jdong/ktorrent/svn-edgy/")

and seems to be doing way better than 2.0.3. It connects faster and to more peers, I should post a log of the program when I have the time. But seems to be doing better.

Greetings, and thanks to all the Ktorrent devs :)

---

### Post by Rulzern on 2006-11-23
Do you still need testers for this?

If so, could you release 64-bit packages, or source packages?

---

### Post by jdong on 2006-11-23
No, I think we're all set on this one. We might just jump the gun and go to KTorrent 2.1 beta :)

---

### Post by Junx on 2006-11-23
You got a Feisty version?

---

### Post by jdong on 2006-11-23
Ha! No, I don't have any feisty build environments but if you know how to use bzr and debuild, look on launchpad product ktorrent, I've got my debianization branch there. Check it out and it builds fine in bzr.

---

