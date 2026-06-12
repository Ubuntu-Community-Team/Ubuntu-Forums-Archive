---
title: "Adding a different clock."
date: 2017-03-05
forum: General Help
---

### Post by natesnape on 2017-03-05
Hello all, is there a way to add another clock alongside your default clock on Lubuntu, I'm residing in the Philippines and by default my time is set to PHST (Philippine standard time), however I want to add multiple timezone's mainly PST and EST time, is there a way to add more clock or timezone on the clock at the lower right of the screen, or to add different timezone's at all?

---

### Post by vasa1 on 2017-03-05
Would you consider using Conky?

I have a very boring one in the top left of my screen showing three time zones: local, UTC, and EST.
```
-- vim: ts=4 sw=4 noet ai cindent syntax=lua
--[[
# Conky, a system monitor, based on torsmo
# left out ${memperc}
]]

conky.config = {
alignment = 'top_left',
background = false,
default_color = '555555',
double_buffer = true,
draw_shades = false,
extra_newline = false,
font = 'Ubuntu Mono:bold:size=16',
gap_x = 3,
gap_y = 4,
minimum_height = 50,
minimum_width = 700,
out_to_console = false,
out_to_stderr = false,
own_window_class = 'Conky',
own_window_hints = 'undecorated,below,sticky,skip_taskbar,skip_pager',
own_window_transparent = true,
own_window = true,
own_window_type = 'override', 
short_units = true,
text_buffer_size = 256,
update_interval = 2.0,
uppercase = false,
use_spacer = 'right',
use_xft = true
}

conky.text = [[
 ${time %a %d %b} ${color 7D5126}${time %H:%M}$color/${utime %H:%M}/${tztime America/New_York %H:%M}  ${acpitemp} ${cpu}%  ${memperc}% ${goto 500} ${execpi 360 bash curl-aes} - ${execpi 300 bash curl-neg} 
]]

```

---

