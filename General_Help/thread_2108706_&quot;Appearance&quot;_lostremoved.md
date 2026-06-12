---
title: "&quot;Appearance&quot; lost/removed"
date: 2013-01-25
forum: General Help
---

### Post by Laiquendi on 2013-01-25
Hey guys, I made a trivial/stupid error and I can't solve it, even google didn't help.

Accidentally, while playing with themes, windows etc. I removed the "Appearance" menu somehow. How to put it back/reinstall it? I can't find which app this was...
Now I can't even change my background settings :P

Unity on Ubuntu 12.10 x64.

Thanks

---

### Post by omeomi on 2013-01-25
what if you just reinstall the control center?
```
sudo apt-get install --reinstall gnome-control-center
```

---

### Post by Frogs Hair on 2013-01-25
Try system settings or the context menu found by right clicking the desktop. For additional settings install the Gnome Tweak Tool. 

The package that includes the defalt appearance setting is the gnome-control-center

---

### Post by Laiquendi on 2013-01-25
Nope, it didn't help.

Clicking "change desktop background" does not help either, cause it leads me to "system settings" menu... with "appearance" menu missing :P

---

### Post by Laiquendi on 2013-01-26
Damn, no one? :/

---

### Post by Laiquendi on 2013-01-26
Still? :P

---

### Post by steelhive on 2013-01-27
Try installing or reinstalling gnome-control-center-unity:

sudo apt-get install gnome-control-center-unity

or

sudo apt-get install --reinstall gnome-control-center-unity

---

### Post by Laiquendi on 2013-01-29
It worked! Thanks! :)

I had it removed, so installing it with proper app name helped ;)

---

### Post by Frogs Hair on 2013-01-29
> **Laiquendi said:**
> It worked! Thanks! :)

I had it removed, so installing it with proper app name helped ;)

Sorry, I have no such package on my 12.10 installation. 

gnome-control-center-unity is not listed in synaptic

---

### Post by mathematiker on 2013-04-18
> **Frogs Hair said:**
> Sorry, I have no such package on my 12.10 installation. 

gnome-control-center-unity is not listed in synaptic

you have to add* deb [http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu](http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu) quantal main *to your sources.list

---

