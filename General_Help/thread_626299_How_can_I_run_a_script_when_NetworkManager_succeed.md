---
title: "How can I run a script when NetworkManager succeeds?"
date: 2007-11-28
forum: General Help
---

### Post by ichudov on 2007-11-28
What I want is to run a shell script of my own making, as root, whenever a network connection is up (for example by Network Manager). I use Network Manager. 

Just to give you an idea, this script tries to figure out where I am (home or work) and takes action based on that, such as mounting NFS directories. 

I tried placing this script under /etc/network/if-up.d, but it did not seem to work. 

Any ideas?

---

