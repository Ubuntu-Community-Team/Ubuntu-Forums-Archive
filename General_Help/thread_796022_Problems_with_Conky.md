---
title: "Problems with Conky"
date: 2008-05-16
forum: General Help
---

### Post by Esahp on 2008-05-16
I am using Openbox with fbpanel. Theres one fbpanel at the top of the screen that is centered and auto adjusted (so there is visible desktop on either side of the centered fbpanel.)

I want to get conky to display a simple one liner at the very top on the same row as the fbpanel, but I can't get it up there. It sits just below the fbpanel line, as opposed to next to fbpanel.

Any ideas?

Thanks.

My .conkyrc:
> 
background yes
use_xft yes
xftfont Monospace:size=11
xftalpha 0.8
out_to_console no
update_interval 2
total_run_times 0
own_window no
own_window_type override
own_window_transparent yes
#own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
draw_shades yes
draw_outline no
draw_borders no
default_color white
default_shade_color black
default_outline_color black
alignment top_right
no_buffers no
override_utf8_locale no

TEXT
$sysname $kernel on $machine

The actual line it displays will change (from what it is now (the $sysname, etc -- that's just for testing purposes to get it working right everywhere else)

---

### Post by kerry_s on 2008-05-16
your missing,taken from mine:

minimum_size 160 5  <- sets the size of the space around the text
gap_x 5  <- gap from the right side                  
gap_y 5   <- gap from the top

that's all i notice

edit: adjusted to more in the corner.

---

### Post by Esahp on 2008-05-16
> **kerry_s said:**
> your missing,taken from mine:

minimum_size 160 5  <- sets the size of the space around the text
gap_x 5  <- gap from the right side                  
gap_y 5   <- gap from the top

that's all i notice

edit: adjusted to more in the corner.

Setting gap_y worked. Thanks :)

---

