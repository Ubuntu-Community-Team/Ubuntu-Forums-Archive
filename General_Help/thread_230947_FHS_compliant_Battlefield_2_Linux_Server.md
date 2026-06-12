---
title: "FHS compliant Battlefield 2 Linux Server"
date: 2006-08-06
forum: General Help
---

### Post by kcy29581 on 2006-08-06
Hi all,

I am trying to be as FHS compliant as possible with Linux. I am now installing the Battlefield 2 Linux Server, and I need to choose the installation directory. Where do I install to be FHS compliant?
 - /home/<username>/bf2
 - /usr/local/bf2
 - /usr/local/games/bf2
 - /opt

I think it should be in /opt, but I'm not sure. If you can give some advice, please try and explain your reasoning.

I know the FHS isn't a rigid rule as such, but by being compliant, it would be easy to find all the applications I install. (such as knowing that applications install /Program Files in Windows)

NOTE: The installation of the Server seems to be possible for a user (i.e. root user priveleges not needed), unless someone can verify that you actually need to install as root. EA don't make any guide easily found!

---

### Post by kcy29581 on 2006-08-08
No ideas?

---

### Post by kcy29581 on 2006-08-09
Ok, even though no-one has replied yet, thought I'd put an update:

I realised that I should install the Server as a user; therefore I can only install it in /home/<username>/bf2, as I have no permissions in the other folders by default.

Still, if anyone can elighten me about FHS, let me know!

---

