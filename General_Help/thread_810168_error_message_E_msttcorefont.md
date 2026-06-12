---
title: "error message E: msttcorefont"
date: 2008-05-28
forum: General Help
---

### Post by bth73 on 2008-05-28
I've just finished a fresh 7.10 install w/repositories.
updated then added acid rip, dvd rip, dvd 95, vlc, gnome gppp.
I have this error every time I use Synaptic package mgr.
" E: msttcorefonts: subprocess post-installation script returned error exit status 1 "

I'm a newbee so please be patient with me.
Thanks, bt

---

### Post by Bigtime_Scrub on 2008-05-28
I did a little research on this and it looks like a known bug.
[https://bugs.launchpad.net/ubuntu/+source/msttcorefonts/+bug/147253](https://bugs.launchpad.net/ubuntu/+source/msttcorefonts/+bug/147253)

Try uninstalling the program and then reinstalling it.

sudo apt-get clean
sudo apt-get update
sudo apt-get purge msttcorefonts
sudo apt-get install msttcorefonts


I hope this helps you.

---

### Post by Cap'n Skyler on 2008-05-28
> **bth73 said:**
> I've just finished a fresh 7.10 install w/repositories.
updated then added acid rip, dvd rip, dvd 95, vlc, gnome gppp.
I have this error every time I use Synaptic package mgr.
" E: msttcorefonts: subprocess post-installation script returned error exit status 1 "

I'm a newbee so please be patient with me.
Thanks, bt
i got that in a SUSE 9.1 a few years back.turns out it is a font package and it has microsoft legal issues. mstt= microsoft true type core fonts i believe is what that really is.
i think one of your 5 packages needs that font package.can you try to install each package one at a time until you get the error again?
no idea where to get it from or how to work around it.some one here will for sure.

Moofs

---

### Post by bth73 on 2008-05-28
Thanks, Bigtime_Scrub, That worked. on to the next problem

---

