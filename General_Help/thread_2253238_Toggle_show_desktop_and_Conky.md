---
title: "Toggle show desktop and Conky"
date: 2014-11-18
forum: General Help
---

### Post by vasa1 on 2014-11-18
When I press the keys to trigger "show desktop", all open windows are minimized and Conky becomes invisible. When I press the same keys again all the minimized windows open again and Conky is visible. Is there some way to prevent Conky from being made invisible?

My .conkyrc```
# Conky, a system monitor, based on torsmo

use_spacer right
double_buffer yes
alignment top_left
background no
default_color 666666
use_xft yes
xftfont Ubuntu Mono:bold:size=16
gap_x 3
gap_y 4
minimum_size 700 18
no_buffers yes
out_to_console no
out_to_stderr no
extra_newline no
own_window yes
own_window_class Conky
own_window_type normal 
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager  
own_window_transparent yes
update_interval 2.0
uppercase no
draw_shades no ### gets rid of text shadow (seen when desktop background is light)!
short_units yes

TEXT
${time %a, %d %b} ${color B3492B}${time %H:%M}$color ${utime (%H:%M)}  ${acpitemp} ${color 006000}${cpu}%$color ${goto 450} ${mem}
```

---

### Post by ajgreeny on 2014-11-18
Try changing the window line in your conky configuration file, usually ~/conkyrc to 
own_window_type** override**

If that does not do the trick I do not know why your conky is disappearing; it doesn't on my Xubuntu 12.04 system.

---

### Post by vasa1 on 2014-11-18
Solved! Thank you :)

---

### Post by ajgreeny on 2014-11-18
Great!
Can you mark the thread as **Solved** from Thread Tools at the top.

---

### Post by vasa1 on 2014-11-18
> **ajgreeny said:**
> Great!
Can you mark the thread as **Solved** from Thread Tools at the top.I did so immediately after posting that it worked. It's showing [SOLVED] for me now. Maybe there was some delay somewhere?

---

