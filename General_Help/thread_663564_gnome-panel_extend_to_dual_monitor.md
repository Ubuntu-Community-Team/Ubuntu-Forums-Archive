---
title: "gnome-panel extend to dual monitor"
date: 2008-01-10
forum: General Help
---

### Post by pinoyskull on 2008-01-10
How do i extend gnome-panel on dual-monitors?

im using bigdesktop setup on 2 17" LCDs with resolution of 2560x1024.

---

### Post by codesplice on 2008-01-10
What graphics card?  For nVidia, try enabling TwinView for the monitors from the nvidia-settings utility.

---

### Post by pinoyskull on 2008-01-10
im using ATI and configured my desktop with this commands
> aticonfig --initial=dual-head
aticonfig --dtop=horizontal --overlay-on=1

---

### Post by codesplice on 2008-01-10
Ahh, it's been a while since I've dealt with ATI, so I don't know how much help I'll be :-/

---

### Post by pinoyskull on 2008-01-10
anybody?

---

### Post by criskat777 on 2008-01-10
> **pinoyskull said:**
> How do i extend gnome-panel on dual-monitors?

im using bigdesktop setup on 2 17" LCDs with resolution of 2560x1024.

It sounds like you have dual mons working and you want the Gnome bar across both screens. Corect me if i am wrong but if that is what you want (right click on the panel and click on new panel after you get the new panel just add the apps you want on it. i hope thats what you wanted to know if not try to  be a little more specific:)

---

### Post by criskat777 on 2008-01-10
If you don't have Dual Mon working let me know so i can help you set it up with xrandr or aticonf. what ever works on your sys first:)

---

### Post by pinoyskull on 2008-01-10
what i want is to have a single gnome-panel across 2 monitors

---

### Post by Tenken on 2008-01-10
Criskat777's first suggestion should work. It won't actually be one single panel but that is how it will appear. You can add whatever you need to second panel, like the window list. With this setup any windows on the second monitor will appear only on the window list of the secondary panel. I actually like the two panel setup better, it keeps me more organized.

---

