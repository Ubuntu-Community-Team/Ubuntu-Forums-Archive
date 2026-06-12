---
title: "Installing Ubuntu 7.10"
date: 2007-10-27
forum: General Help
---

### Post by LAF4SENS on 2007-10-27
Hi,

I'm a newbie. And I'm installing Ubuntu 7.10 on my OLD pc.

I have 2 HD's

1) 30 gig
2) 8 gig

I want to install the OS (ubuntu) on the 8 gig HD and make the 30 HD freespace.

How would I set up my partitions???

I'm trying everything, but ubuntu tells me that I need a ROOT files system .

Please Help,

Marc.

---

### Post by songshu on 2007-10-27
just place / on your 8g and /home on your 30g


the / is the root file system

---

### Post by LAF4SENS on 2007-10-27
Thanks,

And both would be ext3???

What about swap?

---

### Post by songshu on 2007-10-27
ext3 would be a good choice for both

SWAP needs its own partition as well indeed and i would just place it on the 8g disk if i were you

an old rule says you should look at the amount of RAM you have and then double that size for swap

so if you have 
128mb ram then 256 mb swap

i usually follow this rule to a maximum of 512MB

---

