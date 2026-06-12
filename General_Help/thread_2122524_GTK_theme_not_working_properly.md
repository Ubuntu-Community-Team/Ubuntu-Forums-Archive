---
title: "GTK theme not working properly"
date: 2013-03-05
forum: General Help
---

### Post by X D face me on 2013-03-05
hi everyone

After i tried to change the background of some eclipse tooltips by editing /usr/share/themes/Ambiance/gtk-2.0/gtkrc"' and changing "ntooltip_bg_color:#000000" to "ntooltip_bg_color:#f5f5b5". the theme of a couple of guis changed from the standard ambiance to a much uglier theme. it also moves the dropdown menus (i dont know how to call them) of eclipse to the top of the window where they used to be at the very top of the screen. I changed the file back but that didn't fixed the problem. Does anyone know a solution?

[[IMG]http://s24.postimage.org/n10s8x3z5/Screenshot_from_2013_03_05_22_40_18.jpg[/IMG]]("http://postimage.org/image/n10s8x3z5/")
gimp and eclipse are both messed up with this change

X D face me

---

### Post by mc4man on 2013-03-05
check that you didn't inadvertently mess up that gtkrc file somehow (or re-install light-themes or restore orig from the gtkrc~ if you only made 1 change

Don't see that your edit does anything bad other than make for hard to see tooltips (yellow background with white text
(screen is gimp with your background & black text instead

---

### Post by X D face me on 2013-03-06
reinstalling the light-theme worked, thanks dude!!!

thread can be closed

---

