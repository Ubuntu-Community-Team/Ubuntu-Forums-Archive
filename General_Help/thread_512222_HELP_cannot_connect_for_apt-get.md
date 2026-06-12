---
title: "HELP cannot connect for apt-get"
date: 2007-07-28
forum: General Help
---

### Post by sarc on 2007-07-28
HP Compaq nc6400 notebook, with ATI x1300 video card, I followed Mike's advice to apt-get install xorg-driver-fgrlx and it worked fine to get gnome on the live CD working.  I intalled Ubuntu 7.04 and chose my locale as Taiwan.  On reboot X failed again and I followed the procedure again (using pppoeconfig from command line to access ADSL), however apt-get could not resolve some addresses that did not appear when using LiveCD: it complained could not resolve tw.security.ubuntu.org and some other tw address.  Obviously apt-get is going to the wrong place... how do I tell it to go to the right repository from command line? 

(If I try to run tle LiveCD again Ubuntu locks up... )

Thanks

---

### Post by Ptero-4 on 2007-07-28
from the command line type this:
```
sudo pico /etc/apt/sources.list
```
Remove the tw. from all the repository addresses, save (ctrl-o), exit (ctrl-x), type:
```
sudo aptitude update
``` and then you can install your stuff.

---

### Post by sarc on 2007-07-29
Thanks it worked fine - I am typing this in Feisty - although I have a sneaky suspicion the original problem was I typed the password wrong in pppoeconf!  Hope I wasn't that dumb....

---

