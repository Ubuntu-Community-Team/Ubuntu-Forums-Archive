---
title: "Can't Login After Hardy Update"
date: 2008-04-24
forum: General Help
---

### Post by davidcaiazzo on 2008-04-24
I just ungraded  to Hardy today from Gutsy, the whole process seemed to go fine. When I restarted the login window pops up but after I type in my user name and hit enter gdm restarts and goes back to asking for my user name again. The only thing I can think of that is causing this problem is that I have my finger print reader enabled(not through think finger) but I am pretty sure the update process asked if I wanted to replace the file(which I most certainly said yes to). Does anyone have any idea how to fix this?

---

### Post by qwalton on 2008-04-24
I believe that this is caused by a problem with gdm and could be solved by rebuilding your xorg.conf. 

```
cp /etc/X11/xorg.conf /etc/X11/xorg.conf.old

sudo dpkg-reconfigure -phigh xserver-xorg
``` 

I struggeled with this same issue when I tried installing the hardy beta and I'm not entirely certain if this is what I did to fix the problem, but it is worth a try.

---

### Post by davidcaiazzo on 2008-04-24
Thanks for your replay, I just tried that and it didn't work unfortunately.

---

