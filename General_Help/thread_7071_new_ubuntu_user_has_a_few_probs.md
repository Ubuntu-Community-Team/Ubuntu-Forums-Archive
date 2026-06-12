---
title: "new ubuntu user has a few probs"
date: 2004-12-03
forum: General Help
---

### Post by irish rebel on 2004-12-03
Guys heres the deal i have been using suse 9.2 and its predecessers for past 3 yrs I just installed ubuntu on my new pc have top stuff on the box and ubuntu picked them all up so no probs there connecting via netgear wireless , , heres my problems 
] I want mplayer  its not in universe  can i download a debian pkg? can i download the tar.gz 
2] i need dvd playing , where do i get libdvd.css for ubuntu?
3] root access whats the deal with this if i want to edit my /etc/apt/source list file i cant as it is 
4] also i havent used gnome in a few years  so how do i change the icons on gnome apps?

Thanks alot guys

---

### Post by poofyhairguy on 2004-12-03
[QUOTE=irish rebel]
] I want mplayer  its not in universe  can i download a debian pkg? can i download the tar.gz [/QUOTE]

Hello and welcome to the Ubuntu community.  For any questions, check out this page first:


[http://kitech.com.my/ubuntu/4.10/index.html](http://kitech.com.my/ubuntu/4.10/index.html) 


To add more packages to your synaptic and get a media player (I suggest the gxine over any mplayer), follow my instructions on this page.

[http://www.ubuntuforums.org/showthread.php?t=6485&highlight=xmms](http://www.ubuntuforums.org/showthread.php?t=6485&highlight=xmms)

These steps will add the Universe and Multiverse- all the packages you will ever need.

---

### Post by M@t on 2004-12-04
You don't need to be root to edit sources.list file. sudo command allows you to execute a command as a super user.
```
sudo gedit /etc/apt/sources.list
``` 
and then type _your_ password, and not the root one.

---

### Post by Marauder1 on 2004-12-04
[QUOTE=poofyhairguy]Hello and welcome to the Ubuntu community.  For any questions, check out this page first:


[http://kitech.com.my/ubuntu/4.10/index.html](http://kitech.com.my/ubuntu/4.10/index.html) 


To add more packages to your synaptic and get a media player (I suggest the gxine over any mplayer), follow my instructions on this page.

[http://www.ubuntuforums.org/showthread.php?t=6485&highlight=xmms](http://www.ubuntuforums.org/showthread.php?t=6485&highlight=xmms)

These steps will add the Universe and Multiverse- all the packages you will ever need.[/QUOTE]

Wow thanks a lot for these pages i grabed them right away !!!

---

### Post by poofyhairguy on 2004-12-04
[QUOTE=Marauder1]Wow thanks a lot for these pages i grabed them right away !!![/QUOTE]

no prob.

---

