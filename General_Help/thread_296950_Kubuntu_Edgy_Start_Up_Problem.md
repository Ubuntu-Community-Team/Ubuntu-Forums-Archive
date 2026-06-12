---
title: "Kubuntu Edgy Start Up Problem"
date: 2006-11-10
forum: General Help
---

### Post by landcross on 2006-11-10
When Kubuntu starts up since upgrading to Edgy  the sytem locks
 for 30 seconds and gives this message
"sound server fatal error, cpu overload aborting"

It is fine in Gnome it only occurs in KDE.

Please keep the solution simple I am new to Linux

Thanks

---

### Post by jimbren on 2006-11-10
Try this:
```
sudo apt-get install -f
```
that will look for and fix any broken packages.
Then I would do 
```
sudo apt-get install kubuntu-desktop
```
just to make sure you have all the Kubuntu packages properly installed.

I admin that my advice is kind of a stab in the dark.  Please let me know how it does...I'm curious.

jimbo

---

### Post by landcross on 2006-11-10
Hi
Thanks for trying but it is still the same. Odd that my sound and system are Ok after the error messsage and lockup. And that it is OK in Ubuntu with Gnome.

Can anyone help?

---

