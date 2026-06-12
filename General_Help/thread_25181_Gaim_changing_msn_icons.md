---
title: "Gaim changing msn icons"
date: 2005-04-09
forum: General Help
---

### Post by nickx on 2005-04-09
Hi Guys, 

I'm using Gaim and the software is very nice but I would really like to change the ugly green/blue MSN icons in front of the people name. Is this possible and if yes could you tell me how to do this.. thnx guys

---

### Post by npu on 2005-10-02
[QUOTE=nickx]Hi Guys, 
I'm using Gaim and the software is very nice but I would really like to change the ugly green/blue MSN icons in front of the people name. Is this possible and if yes could you tell me how to do this.. thnx guys[/QUOTE]Yes, download (here's a nice icon set: [http://www.gnome-look.org/content/show.php?content=22348](http://www.gnome-look.org/content/show.php?content=22348) ) or create the icons you want and then have a look in /usr/share/pixmaps/gaim/ (the icons for the different networks are placed in status/default/)
```
$ cd /my_new_icons/status/default/
$ sudo cp * /usr/share/pixmaps/gaim/status/default/
```

---

