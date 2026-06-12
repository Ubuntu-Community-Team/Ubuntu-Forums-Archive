---
title: "Conky disappears when I click"
date: 2007-05-14
forum: General Help
---

### Post by jordon on 2007-05-14
I have Conky running on my desktop, but whenever I left-click or right-click anywhere on the desktop, the Conky window disappears (though the program still runs). I'm using Feisty with desktop effects (Compiz) enabled. Here are the relevant values in my .conkyrc file:

```

background no
cpu_avg_samples 2
net_avg_samples 2
out_to_console no
own_window yes
own_window_type desktop
own_window_transparent no
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
own_window_colour ffb18e
font Inconsolata
use_xft yes
xftfont Inconsolata:size=8.5
xftalpha 0.8
on_bottom yes
mail_spool $MAIL
update_interval 1
double_buffer no
draw_shades no
draw_outline no
draw_borders no
stippled_borders 10
border_margin 4
border_width 1
default_color 0e0063
default_shade_color black
default_outline_color black
gap_x 13
gap_y 13
alignment top_right
use_spacer no
no_buffers yes
uppercase no

```

---

### Post by m.musashi on 2007-05-14
Try changing
```
own_window_type desktop
```
to
```
own_window_type override
```
I'm on windows at the moment so I can't veryify that but I think it's right.

---

### Post by jordon on 2007-05-14
Thanks. That fixes the problem, but now the Conky window (which I have in the upper right corner) is partially obscured by the top panel.

---

### Post by orb9220 on 2007-05-14
You will have to edit the x and y positions to have x position 20-30 less so the top is not touching the panel.

---

### Post by jordon on 2007-05-14
Thanks! That did the trick.

---

