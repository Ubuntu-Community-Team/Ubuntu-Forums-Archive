---
title: "Websites load slow from inside network, fine from outside"
date: 2007-02-24
forum: General Help
---

### Post by illiterate_light on 2007-02-24
I'm guessing this is a router problem and not an Ubuntu problem, but here goes:

I have several websites running on apache2 on Ubuntu 6.06.1.  They load quickly from outside my network, and quickly from within the network if I access them using internal network addresses.  But if I use their full domain names from within the network, they load painfully slowly.  I have a basic Netgear router, and my guess is that the request is going outside to try to find the site, and somehow gets confused when it's directed back to the same network for the content, and bounces off itself or something like that.  It eventually loads, but is incredibly slow, like several minutes to load a couple of small images (which are instantaneous using internal addresses).

Any clues?

---

