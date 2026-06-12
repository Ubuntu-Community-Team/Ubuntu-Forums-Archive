---
title: "[SOLVED] Volume control works in tray, but not by using keys"
date: 2008-05-17
forum: General Help
---

### Post by twoseids on 2008-05-17
My volume controls used to work perfectly. I could control the volume with the icon in my "systray" (upper right panel) or by using the Function key plus End, Page Up or Page Down (mute, volume up, volume down respectively).

A few weeks ago (while still using Gutsy), the function keys stopped doing the trick. I now have to use the panel icon, which is a pain when I'm in full screen mode on a movie, for example.

How can I figure out what's wrong? I'm using a Dell Latitude D520.

Thanks!

---

### Post by joshsmith on 2008-05-17
hey

system>preferences>sound
"default mixer tracks" will tell you the thing your keyboard shortcuts will change, make sure it is what you want, ie probably alsa

also check in system>preferences>keyboard shortcuts of course to check the shortcuts are still bound to what you want them to be bound to

---

### Post by Gunman1982 on 2008-05-17
If I remember right there is a package available throught synaptic (or apt-get if you want) which provides functionality for Dell special function keys. Search in synaptic for dell and check if a fitting package is installed.

---

### Post by twoseids on 2008-05-18
> **Gunman1982 said:**
> If I remember right there is a package available throught synaptic (or apt-get if you want) which provides functionality for Dell special function keys. Search in synaptic for dell and check if a fitting package is installed.
Yes, I found it: i8kutils. I have no idea how to run it but I'm googling...

---

### Post by twoseids on 2008-05-19
> **joshsmith said:**
> hey

system>preferences>sound
"default mixer tracks" will tell you the thing your keyboard shortcuts will change, make sure it is what you want, ie probably alsa

also check in system>preferences>keyboard shortcuts of course to check the shortcuts are still bound to what you want them to be bound to
Well this did the trick. I think. I selected something other than ALSA, saw that it didn't work, then went back and selected ALSA again, and everything seemed to work just fine.

Good thing, I never did seem to be able to get that i8kutils working...

Thanks for your help!

---

