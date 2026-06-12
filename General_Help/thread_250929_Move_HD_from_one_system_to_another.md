---
title: "Move HD from one system to another"
date: 2006-09-04
forum: General Help
---

### Post by pwrstick on 2006-09-04
Howdy,

I'm thinking about moving a hard drive from one computer to another without any preparation.  Should I stop thinking about it or will Ubuntu redetect everything OK?

(It's actually a Breezy Server install).

---

### Post by tkiesel on 2006-09-04
From my experience, Linux handles this sort of thing very gracefully.

Only things to look out for:

1. Is the HD in question the primary master? If so, make sure it's the primary master in the computer you install it into.  (If you're not doing some exotic multiple hard drive dual-booting, then you don't have to worry about this one)

2. You may (only may.. low probability here) have X break on the first boot in the new computer. You say it's a server, so this issue could indeed be utterly moot for you. This happened to me when I bought a new motherboard because the PCI address of the wideo card was different on the my new Abit AN7 than on most other motherboards. I just needed to do a 

```
sudo dpkg-reconfigure xserver-xorg
``` to fix it.

3. Once you get booted up and logged in, you may need to re-enter your network settings and/or activate network interfaces in System-->Administration-->Networking (or the command line equivalents)  Just depends on how different the networking hardware is in the new server.

4. If you're using one of the specialized kernels, make sure that continuing to use it jibes with the hardware you're moving to. If it doesn't, go back to stock 386 kernel for the transition.

Good luck!!

---

