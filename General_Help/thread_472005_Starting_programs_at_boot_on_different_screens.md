---
title: "Starting programs at boot on different screens"
date: 2007-06-12
forum: General Help
---

### Post by Pixel on 2007-06-12
I'm trying to figure out how I can go about start irssi, htop, and rtorrent in the background of different screens (tty4,5,6 respectively), while gdm loads on tty7,

I would like to have all this happens after I log into gdm...

Any help? Thanks.

Edit:

I'm also wondering if it's possible to automatically log into these screens when I log into GDM, so that I don't have to login to each one seperately...

---

### Post by dannyboy79 on 2007-06-13
this has to do with getty's. they used to be laucnhed from inittab but there's no inittab in feisty anymore, I know it'll be possible to start a program within the different getty's but I don't know about auto logging in, but I would say, probably.

---

### Post by dannyboy79 on 2007-06-13
post number 4 seems to be a great post, look at the bottom and you'll see the autologin, I would imagine you would just add your command at the end, using 
&&
which means to run that command if the first one works. ensure that the commmands you want to run don't require to be run within X.

---

