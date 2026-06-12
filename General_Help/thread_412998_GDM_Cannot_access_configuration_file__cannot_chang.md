---
title: "GDM Cannot access configuration file / cannot change login screen"
date: 2007-04-18
forum: General Help
---

### Post by benjaminmorris on 2007-04-18
I am unable to change the login screen. The first time i noticed this was when I installed kde via ```
sudo apt-get install kubuntu-desktop
```

That changed my login to I guess the default Kubuntu login which I don't like. When I tried to change it, it gives me the "Cannot connect to socket" and "Cannot access gdm configuration file" errors.

I then did ```
sudo apt-get install xubuntu-desktop
``` to see if that would either fix the problem or at least put a different one on, but to no avail. Finally, I tried ```
sudo apt-get install ubuntu-desktop
``` to see if that would fix anything, but it didn't.

One final note is that when I logged into kde, i was able to open the login manager. It gives me the list of login screens to choose from, and i chose the ubuntu CE login. What's interesting is that the kubuntu screen is NOT an option. It's not even on the list, but IT'S STILL BEING USED.

I'm totally confused by all this. Any ideas?

---

### Post by zvacet on 2007-04-18
I don´t belive you need more than one desktop enviroment,so choose wich one you want and remove others.You will find informations on 
[http://www.psychocats.net/ubuntu/]("http://www.psychocats.net/ubuntu/")

---

### Post by bwhite82 on 2007-04-18
I agree with zgacet, which that said though, even though you can use gnome's login manager (GDM) it is generally best to stick with the login manager for the desktop that you use most, in your case KDM.

---

### Post by benjaminmorris on 2007-04-19
Ok, granted. But how do you change it? When I try to do it through the menus, i get the same error. Any idea as to how to access the KDM login manager? I can't seem to find it. BTW, what's the easiest way to install KDE (just in case I'm undecided) without installing the whole kubuntu-desktop? Is there a meta-package or something? Thanks.

---

### Post by zvacet on 2007-04-19
[http://www.psychocats.net/ubuntu/kde]("http://www.psychocats.net/ubuntu/kde")

---

### Post by scxtt on 2007-04-19
put the FULL path to the DM you want to use in **/etc/X11/default-display-manager** ...

---

### Post by benjaminmorris on 2007-04-19
Got it. Thanks!

---

