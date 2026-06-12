---
title: "need some serious help."
date: 2008-06-07
forum: General Help
---

### Post by nghoongen on 2008-06-07
i just install compiz.. but where to open compiz ? 
and and ubuntu and xubuntu.. which one better ??
today just started using ubuntu 8.04(the one with orange colour):confused:

---

### Post by Forlong on 2008-06-07
> **nghoongen said:**
> i just install compiz.. but where to open compiz ?
Compiz should be installed by default.
Go to *System &#8594; Preferences &#8594; Appearance &#8594; Visual Effects* and enable it there. 
> **nghoongen said:**
> and and ubuntu and xubuntu.. which one better ??
You have to decide that yourself.
Xubuntu is just Ubuntu with another desktop environment called Xfce.
You can install it on your existing install by installing xubuntu-desktop:
```
sudo apt-get install xubuntu-desktop
```
It will automatically create a separate session in GDM (the login screen).

---

### Post by mick222 on 2008-06-07
look in synaptic you can install ccsm or simple ccsm you will then find it under system-preferences advanced desktop effects settings .simple cccsm gives you basic presets and a little customization.

---

### Post by chewearn on 2008-06-07
> **nghoongen said:**
> i just install compiz.. but where to open compiz ? 
and and ubuntu and xubuntu.. which one better ??
today just started using ubuntu 8.04(the one with orange colour):confused:

You don't install compiz with ubuntu 8.04, because it's already installed by default.  You just need to enable it, by enabling a graphics driver with 3D capabilities.

You might already broke something, since you install something that's already there.  Can you post how you install compiz?

Secondly, asking whether ubuntu or xubuntu is better is like asking whether orange or apple is better.  It's matter of personal preferences.  I use both (in separate systems).  I like simplicity of xubuntu, but I prefer the more features available in ubuntu gnome's desktop.

.

---

### Post by nghoongen on 2008-06-07
i install compiz on add/remove there... type compiz and auto search. check and apply.. thats all.. by the way, many thanks to all who help and teach me.
one more question, where u download other themes.. very cool one i saw on the internet.. and can change the desktop into a cube like thing and twist.????

---

### Post by Forlong on 2008-06-07
> **nghoongen said:**
> one more question, where u download other themes.. very cool one i saw on the internet..
[http://gnome-look.org](http://gnome-look.org)
> **nghoongen said:**
> and can change the desktop into a cube like thing and twist.???
See [here](http://forlong.blogage.de/article/2008/4/26/How-to-set-up-Compiz-Fusion-074) under "Getting the cube".

---

### Post by nghoongen on 2008-06-07
thanks all.. i now going to try it..

---

### Post by nghoongen on 2008-06-07
guys.. i just noticed on my computer at visual effect tab there dont have custom. only have none, normal and extra..

---

### Post by Forlong on 2008-06-07
You need to install Simple-CCSM to get that option on Hardy:
```
sudo apt-get install simple-ccsm
```

---

### Post by nghoongen on 2008-06-07
how to install???

---

### Post by Forlong on 2008-06-07
Either use the command I posted to install it via the terminal or open Synaptic (System &#8594; Administration) and search for **simple-ccsm**.

---

### Post by nghoongen on 2008-06-07
oh. done. can use it.

---

