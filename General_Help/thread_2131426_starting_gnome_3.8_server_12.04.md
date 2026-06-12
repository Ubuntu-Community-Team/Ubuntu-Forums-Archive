---
title: "starting gnome 3.8 server 12.04?"
date: 2013-04-01
forum: General Help
---

### Post by conradin on 2013-04-01
I am trying to install gnome3.8 on ubuntu server 12.04.
So i looked at this page:
[http://askubuntu.com/questions/276646/gnome-3-8-on-ubuntu-12-04-2-lts](http://askubuntu.com/questions/276646/gnome-3-8-on-ubuntu-12-04-2-lts)
which reffers to this:
[http://www.ubuntukiller.com/2013/03/how-to-installupgrade-gnome-38-in.html](http://www.ubuntukiller.com/2013/03/how-to-installupgrade-gnome-38-in.html)

so I installed the gnome3 ppa. But it doesnt launch on boot. So then I tried $startx
and that told me I need to install xinit so I did. But I still cant get into the gnome3 environment.
what should I do?

---

### Post by conradin on 2013-04-01
So then i tried:
```

sudo apt-get install gnome-desktop-enviornment

```
and that worked. But it installed a bunch of other junk I didnt want, and It's evidently Gnome3.4, where I was hoping for gnome 3.8.
I tried
```

sudo apt-get install --no-recommends gnome-desktop-enviornment

``` 

but that was invalid
what is the best way to get gnome3.8 on a 12.04 server install?

---

