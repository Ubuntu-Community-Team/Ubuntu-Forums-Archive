---
title: "Some easy way to go back, please"
date: 2008-04-09
forum: General Help
---

### Post by Bartender on 2008-04-09
I pushed the "off" button for 5 seconds to kill Ubuntu cause I was in a hurry.  Ubuntu desktop refused to come up after that.  This is the second time that a simple mistake led to no desktop, just a command line interface that I couldn't make sense of.

Dammit, it's taken a lot of work to get the thing where I wanted it.

Is there some straightforward way to fix or restore or go back when Ubuntu seizes up?

---

### Post by Rocket2DMn on 2008-04-09
You can try the autoreconfiguration of X:
```
sudo dpkg-reconfigure xserver-xorg -phigh
```
then
```
startx
```
Otherwise you may need to post some logs for us.

---

