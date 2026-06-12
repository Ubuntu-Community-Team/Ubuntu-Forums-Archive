---
title: "GNOME theme"
date: 2006-12-27
forum: General Help
---

### Post by hokah on 2006-12-27
Hi
I have strange felling that everything on my gnome desktop has been ment to work on higher resolution:
GAIM icons look too big 
Icons are big too
Firefox menu bar is too large as well
My resolution is 1024 x 768

What should I change ?

---

### Post by taurus on 2006-12-27
What size monitor do you have?  You can always increase it up to something like "1280x1024".

---

### Post by flsantos on 2006-12-27
Try theme manager. Change font size. It should do it.

---

### Post by stalker145 on 2006-12-27
> **hokah said:**
> Hi
I have strange felling that everything on my gnome desktop has been ment to work on higher resolution:
GAIM icons look too big 
Icons are big too
Firefox menu bar is too large as well
My resolution is 1024 x 768

What should I change ?

You could try running > gconf-editor in the terminal. From there go to **apps -> nautilus -> icon_view** and select **default_zoom_level**. Change the string to small, smaller, smallest, whatever works for you. I used small and my icons are a much more acceptable size at 1024x768.

---

### Post by Cable on 2006-12-27
If you want to go to a higher resolution and you have a 4:3 monitor, I would suggest using 1280x960 as that is a 4:3 ratio.  1280x1024 is 5:4 and will look a bit off if you aren't using on a 5:4 monitor.

---

