---
title: "Compiz running in kde3.5! - but how to change settings?"
date: 2008-05-18
forum: General Help
---

### Post by oconnor663 on 2008-05-18
I am running Hardy Kubuntu, and I've installed compiz via apt-get. I've used the program "desktop-effects-kde4" (despite mine being kde3.5) and selected the "tons of effects" option. Now, compiz runs by default and I have things like pretty window/desktop switching. Sweet!

What I'm looking for, though, is a way to configure compiz manually to enable more effects (the cube, naturally). I've installed just about every compiz-related package, but nothing like Gnome's "Advanced Desktop Settings" is showing up in kde's System Settings panel. Is there a package designed to do that? Thanks for your help.

---

### Post by .nedberg on 2008-05-18
Try this package:
compizconfig-settings-manager
```

sudo apt-get install compizconfig-settings-manager

```

---

### Post by oconnor663 on 2008-05-18
I have installed that package already. Nothing new shows up in my System Settings window. (Unless it integrates itself into some other part of the window?) Is there some other interface I'm supposed to use? Is there a way to invoke it from the command line?

---

### Post by oconnor663 on 2008-05-18
> **oconnor663 said:**
> I have installed that package already. Nothing new shows up in my System Settings window. (Unless it integrates itself into some other part of the window?) Is there some other interface I'm supposed to use? Is there a way to invoke it from the command line?


SUCCESS!!! Found it in another post somewhere.

The command line invocation for the config window is "ccsm".

---

### Post by robertsaron on 2008-05-27
I am using KDE4 Hhardy 8.04 Kubuntu, and when doing ccsm, i dont get any options. How do I get the 3d cube rotation? Anyone have any ideas?

This is the 2-3rd post I have asked for help on this. But no one seems to care to respond, they just tell me its built in. If it is built in where and how do I enable the 3D rotating cube like in gnome?

---

### Post by Forlong on 2008-05-28
Post the output of ```
dpkg -l | grep compiz
``` and use the forum's [noparse][CODE][/noparse] tag please (# button)

---

### Post by robertsaron on 2008-05-29
Here is the output settings you requested:

```
ii  compizconfig-settings-manager              0.7.4-0ubuntu2                      Compiz configuration settings manager
ii  libcompizconfig0                           0.7.4-0ubuntu1                      Settings library for plugins - OpenCompositi
ii  python-compizconfig                        0.7.4-0ubuntu1                      Compiz configuration system bindings
```

---

### Post by Forlong on 2008-05-30
Compiz is not installed on your system at all.

You can do it by installing the following packages:
```
sudo apt-get install compiz-kde compiz-fusion-plugins-main compiz-fusion-plugins-extra
```

---

### Post by robertsaron on 2008-06-01
Ok its all installed. I am using Kubuntu 8.04 KDE4. How do i change to using compiz, instead of KDE4's effects.

---

### Post by Forlong on 2008-06-01
Simply run ```
compiz
``` in a terminal.

If it works, you can save your session when logging out to use it permanently.

---

### Post by robertsaron on 2008-06-02
that worked. Thanks so much for the help. Couple more questions:

is there a way to have/add compiz as a service, so when the computer reboots, it will auto load? 

And I am trying to remember how to add in emerald as the theme manager for compiz.

---

