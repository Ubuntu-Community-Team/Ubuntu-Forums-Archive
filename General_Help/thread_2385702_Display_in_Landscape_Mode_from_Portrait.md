---
title: "Display in Landscape Mode from Portrait"
date: 2018-02-23
forum: General Help
---

### Post by nisargmehta1 on 2018-02-23
Hi

When I run Lubuntu on my Lenovo Miix 320 Netbook the display automatically appears in portrait mode that is 800x1280.

Is there a simple way in Lubuntu where I can bring it to Landscape Mode by default i.e. 1280x800?

I am unable to do that in monitor settings.

Also I am a noob with coding, so if your answers can be more detailed it will be appreciated.

Thanks

---

### Post by #&amp;thj^% on 2018-02-23
Powerful xrandr command-line tool might work better.

xrandr shows you the names of different outputs available on your system (LVDS, VGA-0, etc.) and resolutions available on each: 

So to set yours as you wanted "1280x800" 
Open your terminal and paste this in there:
```
xrandr
```
Copy and paste back here the return.
We can see there what lubuntu thinks it can show you.

---

