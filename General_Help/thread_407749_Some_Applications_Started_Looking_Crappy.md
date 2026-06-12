---
title: "Some Applications Started Looking Crappy"
date: 2007-04-12
forum: General Help
---

### Post by OffHand on 2007-04-12
Hi guys,

I must have messed up some settings because some applications look like crap now (gtk1?).

Check the screenshots please.

Anyone know how to fix this?

---

### Post by Rui Pais on 2007-04-12
that looks like gnome-settings-daemon didn't start or failed...

try to start manually from a terminal and check if it get back the normal look and/or if it gives any error or warning messages.

---

### Post by OffHand on 2007-04-12
> **Rui Pais said:**
> that looks like gnome-settings-daemon didn't start or failed...

try to start manually from a terminal and check if it get back the normal look and/or if it gives any error or warning messages.

$ gnome-settings-daemon
You can only run one xsettings manager at a time; exiting

---

### Post by Rui Pais on 2007-04-12
> **OffHand said:**
> $ gnome-settings-daemon
You can only run one xsettings manager at a time; exiting

So it's loaded... weird...

Try to kill it first and then restart:
```
sudo killall -9 gnome-settings-daemon
```
and then
```
gnome-settings-daemon
```

---

### Post by OffHand on 2007-04-12
> **Rui Pais said:**
> So it's loaded... weird...

Try to kill it first and then restart:
```
sudo killall -9 gnome-settings-daemon
```
and then
```
gnome-settings-daemon
```

That didn't work. It's just a few applications (Firestarter, Synaptic among a few others). Actually, it only seems to happen with applications that use sudo.

---

### Post by Rui Pais on 2007-04-12
> **OffHand said:**
> That didn't work. It's just a few applications (Firestarter, Synaptic among a few others). Actually, it only seems to happen with applications that use sudo.

Ohh!!

thats a different issue.

That's not a problem. that's because you are starting graphical apps as root but from a normal user perfil (so root don't have definitions/perfil started... or something like) 

You should start gui apps as root with gksudo instead of sudo 
(besides it maybe be safer too)

---

### Post by daveisadork on 2007-04-12
> **OffHand said:**
> Hi guys,

I must have messed up some settings because some applications look like crap now (gtk1?).

Check the screenshots please.

Anyone know how to fix this?

Most likely you've installed a GTK theme to ~/.themes instead of /usr/share/themes. When you use sudo, the applications (like Firestarter, Synaptic, etc) run as root and can't find the theme you've specified and revert to the (rather ugly) default.

---

### Post by Seq on 2007-04-12
It looks like all those applications are running with sudo? Did you install this theme yourself?

Anyway, try the following:

```
sudo ln -s /home/username/.themes /root/.themes
```

---

### Post by OffHand on 2007-04-12
> **daveisadork said:**
> Most likely you've installed a GTK theme to ~/.themes instead of /usr/share/themes. When you use sudo, the applications (like Firestarter, Synaptic, etc) run as root and can't find the theme you've specified and revert to the (rather ugly) default.

Thanks, right on the spot. Copying my themes in .themes to /usr/share/themes solved my problem  

:guitar: 

> **Rui Pais said:**
> 
You should start gui apps as root with gksudo instead of sudo 
(besides it maybe be safer too)

That doesn't really matter. Thanks for helping me too  :D

---

