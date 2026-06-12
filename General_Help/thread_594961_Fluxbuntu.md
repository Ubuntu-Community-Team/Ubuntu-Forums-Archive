---
title: "Fluxbuntu?"
date: 2007-10-28
forum: General Help
---

### Post by whayong on 2007-10-28
I don't know where to post this and where to get help, so here's a stab in the dark...

I just installed fluxbuntu this morning, install was fairly easy.  Problem is, my resolutio and screen orientation.  Resolution options are only 800X600 and 640X480.  This means I have about a 1 inch border all around my scree.  Another problem is that my mouse pointer is not lining up with the desktop (if that makes any sense).  For example, if I right click on the desktop, the menu pops up about an inch lower and a bit to the right of where I right clicked.  I cannot select any of the icons because when I put the pointer over them it doesn't select it.

I'm running it on a Sony Vaio PCG-srx77.  PIIIM 800 mhz, 384 MB of RAM.  This sytem runs Ubuntu Fiesty and Gutsy quite well, just need it to work with fluxbuntu now.  BTW, I did a fresh install.  One curious thing, when I booted from the LiveCD, I was not given the option to run the liveCD, instead, it was just install and the other options (check CD, memory, etc...)

Thanks!

---

### Post by por100pre1 on 2007-10-28
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```

```
sudo nano -w /etc/X11/xorg.conf
```

Try adding your system resolution. Let me know it this works in Fluxbuntu. :-k

---

### Post by whayong on 2007-10-28
Well, thanks for the reply, believe me it is much appreciated!

I actually tried to follow the ubuntu wiki for fixing screen resolutions by doing 

```
sudo dpkg-reconfigure xserver-xorg
```

and much to my surprise, it fixed it!  Yes!  

Again, thanks for your reply buddy!

---

