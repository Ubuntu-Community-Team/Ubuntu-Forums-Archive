---
title: "Tor does not work"
date: 2007-09-01
forum: General Help
---

### Post by PomJuice on 2007-09-01
Hey guys noob here :)

I installed Tor & Privoxy using 

[PHP]sudo apt-get install tor[/PHP]
[PHP]sudo apt-get install privoxy[/PHP]

Everything installed correctly it seems -- as I got no error.

However I don't know how to run Tor, or see its GUI (like Windows). When I run Tor in terminal I get this problem:

[PHP]root@TOS-A:/home/julie# tor
Sep 01 16:37:26.692 [notice] Tor v0.1.1.26. This is experimental software. Do not rely on it for strong anonymity.
Sep 01 16:37:26.779 [notice] Initialized libevent version 1.1a using method epoll. Good.
Sep 01 16:37:26.780 [warn] /var/lib/tor is not owned by this user (root, 0) but by debian-tor (110). Perhaps you are running Tor as the wrong user?
Sep 01 16:37:26.780 [warn] Failed to parse/validate config: Couldn't access/create private data directory "/var/lib/tor"
Sep 01 16:37:26.780 [err] tor_init(): Reading config failed--see warnings above. For usage, try -h.
root@TOS-A:/home/julie# 
[/PHP]

I'd love you guys so much if I could get some hints!
~J

---

### Post by Seisen on 2007-09-01
Try running tor as a regular user instead of root.

---

### Post by julian67 on 2007-09-01
A good howto [http://ubuntu-tutorials.com/2006/11/02/how-to-install-tor-privoxy-kubuntu-606-610/]("http://ubuntu-tutorials.com/2006/11/02/how-to-install-tor-privoxy-kubuntu-606-610/")

It applies to Ubuntu Kubuntu and Xubuntu and is fine for Feisty.

---

### Post by PomJuice on 2007-09-03
> **Seisen said:**
> Try running tor as a regular user instead of root.

I sign into Ubuntu using root --- I have no other users --- do I need to create another account login??

---

### Post by Lord Illidan on 2007-09-03
Yes, it is very unsafe to run as root, even more so if using tor while using root!

---

### Post by PomJuice on 2007-09-03
Not safe in the sense that I might mess something up as root (being a noob and all)

or,

from the sense that I could be hacked, and because I'm logged in as root, they can do more damage?

This is all very interesting to me!

-J

---

### Post by yabbadabbadont on 2007-09-03
Both.

---

### Post by bikeboy on 2007-09-03
Beaten :(

---

### Post by PomJuice on 2007-09-03
> **yabbadabbadont said:**
> Both.

Thanks :)

I created another account. My root & regular user login now use different passwords & are each 11 characters in length. I hope this is enough to better protect my Ubuntu laptop. :popcorn:

---

