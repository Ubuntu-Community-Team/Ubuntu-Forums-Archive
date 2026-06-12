---
title: "[SOLVED] No internet connection in Ubuntu"
date: 2007-10-20
forum: General Help
---

### Post by eXeCuTeR+ on 2007-10-20
I'm going mad.
I installed UBUNTU yesterday, and now it doesn't let me get into the internet.
My question is:
W-H-Y-?!

BTW,
I got  NVIDIA nForce Networking Controller.

---

### Post by eXeCuTeR+ on 2007-10-22
Well,I fixed this internet bug, so here's my solution:

I added to '/etc/resolve.conf' 2 nameserver and delete the first one (10.0.0.138) - to sum it up, added 2 DNS addresses.
I also edited the '/etc/network/interfaces' and added the broadcast IP.

This worked for me :)

---

