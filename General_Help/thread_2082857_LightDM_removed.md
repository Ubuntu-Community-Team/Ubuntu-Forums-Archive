---
title: "LightDM removed"
date: 2012-11-10
forum: General Help
---

### Post by Linux_junkie on 2012-11-10
I have Ubuntu 12.04 LTS with Unity, Gnome-Shell and K desktops installed.  I decided to remove Unity as I have Gnome-Shell and didn't feel the need to have two desktops that were similar.

I selected all Unity desktop packages to be removed, however, when rebooting I noticed that LightDM was also removed.

Why is LightDM part of Unity?

---

### Post by ibjsb4 on 2012-11-10
yep, its part of the desktop package

[http://packages.ubuntu.com/precise/ubuntu-desktop](http://packages.ubuntu.com/precise/ubuntu-desktop)

Reinstall it if you want

sudo apt-get install lightdm

---

### Post by El Tito on 2012-11-10
I suppose it's as good as other login managers. Don't really know.

---

### Post by ibjsb4 on 2012-11-10
> **El Tito said:**
> I suppose it's as good as other login managers. Don't really know.

Its the lightest at 432kB, gdm weights in at 6800kB.  NoDM is 120kB.

---

### Post by Linux_junkie on 2012-11-11
Having looked in Muon Package Manager I have discovered that lightDM is still installed, but Plymouth is being used in its place.

Now I need to work out how to swap Plymouth with LightDM.

---

