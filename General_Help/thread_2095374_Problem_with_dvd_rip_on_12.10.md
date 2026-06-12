---
title: "Problem with dvd rip on 12.10"
date: 2012-12-16
forum: General Help
---

### Post by izombie666 on 2012-12-16
IS there a problem with 12.10 and the dvd rip app's?

The can't find my DVD drive so I have to manual enter dev/sr0/.  It will then pick up the DVD but it will not copy.

I did not have a problem with the system reading the drive in past releases.  I have tried a number of things but no luck.

Any suggestions?

---

### Post by izombie666 on 2012-12-17
I think is solved it.   I had to load 
sudo apt-get install libdvdread4

and then

sudo /usr/share/doc/libdvdread4/install-css.sh

I am copying a CD through K3b.  I have tried Acid rip yet, But if it works with K3n that good enough.

I'll try acid rip later\\:D/

---

### Post by izombie666 on 2012-12-19
Acid rip is also working now.  I just have to enter the path to the DVD manually (/dev/sr0)

---

