---
title: "How to Change the System Tray Color?"
date: 2015-12-28
forum: General Help
---

### Post by kkk5 on 2015-12-28
The clock is too bright at the down-right corner of the screen, I want to change the color of the bottom panel. How do I do this?

---

### Post by v3.xx on 2015-12-28
Tell us what your running

[https://wiki.ubuntu.com/UbuntuFlavors](https://wiki.ubuntu.com/UbuntuFlavors)

---

### Post by vasa1 on 2015-12-28
If you find the clock too bright, why do you want to change the system tray color or the bottom panel color?

And your image doesn't illustrate the issue too clearly. Include more of the surrounding area.

If the clock text is the issue, your particular panel (insert name here!) should have settings to use another color.

For example, if you use tint2, the code for clock settings looks like this:```
# Clock
time1_format = %H:%M
time1_font = sans 8
time2_format = %a %d %b
time2_font = sans 8
clock_font_color = #FFFFFF 74
clock_padding = 1 0
clock_background_id = 0
clock_rclick_command = orage

```tint2 allows the user to set the color of clock text as well as the opacity. I'm pretty sure just about any other user-friendly panel will allow adequate customization.

---

