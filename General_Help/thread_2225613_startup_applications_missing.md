---
title: "startup applications missing"
date: 2014-05-22
forum: General Help
---

### Post by Jacob-Gates on 2014-05-22
Hey guys. I just updated to ubuntu 14.04 with gnome 3.12 Apparently the startup applications menu has been removed or something (read that in my searches trying to fix my problem, not sure if true or not). I am trying to set a few applications to open at login but I have no idea how to do that without that nice little program that I had until 14.04. So is there a way I could either get that program itself or is there even a more difficult way I can set applications to run at login? I am not afraid to get into terminal/text files/whatever. Just not sure how to do it.

---

### Post by caver12 on 2014-05-22
Did you go to Dash and type in startup? It's there on my system.

---

### Post by Jacob-Gates on 2014-05-22
> **caver12 said:**
> Did you go to Dash and type in startup? It's there on my system.
really? hmm, I wonder mine isn't there. I am using gnome not unity but it doesn't appear in the searches in gnome. I wonder if it got removed in the install of gnome and remove of unity.

---

### Post by Jacob-Gates on 2014-05-22
Oh wait, I found it in the gnome tweak application. it's on a tab on the left for anyone trying to find it.

---

### Post by I_ated_it on 2014-06-06
> **Jacob-Gates said:**
> Oh wait, I found it in the gnome tweak application. it's on a tab on the left for anyone trying to find it.

Did this work for you?  My tweak tool either crashes or just doesnt respond when I click the "+" button to add startup applications.  I just recently switched from Xubuntu to gnome, Xubuntu had a feature that automatically started all applications from my previous session(KDE has the same feature fwiw), a feature that I really liked, but I cant find how to get it to with gnome.  Any ideas?  An alternative would obviously be just to have all the applications I normally use launch on startup but I cant seem to get that to work either.

---

### Post by Jacob-Gates on 2014-06-06
> **I_ated_it said:**
> Did this work for you?  My tweak tool either crashes or just doesnt respond when I click the "+" button to add startup applications.  I just recently switched from Xubuntu to gnome, Xubuntu had a feature that automatically started all applications from my previous session(KDE has the same feature fwiw), a feature that I really liked, but I cant find how to get it to with gnome.  Any ideas?  An alternative would obviously be just to have all the applications I normally use launch on startup but I cant seem to get that to work either.
I don't know how to start application from a previous session. But yes just adding my chosen applications to the startup in the tweak tool works for me. I did have to start it from terminal though. For some reason it won't work by just clicking the launcher.

---

### Post by tacopy on 2014-11-07
> **Jacob-Gates said:**
> Hey guys. I just updated to ubuntu 14.04 with gnome 3.12 Apparently the startup applications menu has been removed or something (read that in my searches trying to fix my problem, not sure if true or not). I am trying to set a few applications to open at login but I have no idea how to do that without that nice little program that I had until 14.04. So is there a way I could either get that program itself or is there even a more difficult way I can set applications to run at login? I am not afraid to get into terminal/text files/whatever. Just not sure how to do it.

I had a similar problem and it was because i added the gnome3-team/gnome3 PPA.  After purging the PPA and rebooting, it was fixed.

Just enter:

sudo ppa-purge ppa:gnome3-team/gnome3

and reboot.  You should be able to access "Startup Applications" after that.  Please note that this will purge that PPA and replace all the applications that the PPA added with the ubuntu defaults!

---

### Post by rickyseltzer on 2015-03-14
Jacob Gates solution worked fine for me on Ubuntu 14.10:[CENTER][B][COLOR=#000000]sudo ppa-purge ppa:gnome3-team/gnome3

[/COLOR][/B][/CENTER]

---

