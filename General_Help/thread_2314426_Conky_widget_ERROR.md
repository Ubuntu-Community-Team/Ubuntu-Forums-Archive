---
title: "Conky widget ERROR"
date: 2016-02-21
forum: General Help
---

### Post by harsha8 on 2016-02-21
Hi,

I have installed above Conky widget. Everything works but, Month and Week day doesn't display (screenshot attached). Please help

---

### Post by coffeecat on 2016-02-21
*Thread moved to **General Help**.*

---

### Post by QIII on 2016-02-21
Hello!

Without seeing the text of the script, any attempt to solve this might be no better than a guess.

Can you post the script?

---

### Post by harsha8 on 2016-02-21
> **QIII said:**
> Hello!

Without seeing the text of the script, any attempt to solve this might be no better than a guess.

Can you post the script?

```

# Conky settings #
background yes
update_interval 1

cpu_avg_samples 2
net_avg_samples 2

override_utf8_locale yes

double_buffer yes
no_buffers yes

text_buffer_size 2048
#imlib_cache_size 0

temperature_unit fahrenheit

# Window specifications #

own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorate,sticky,skip_taskbar,skip_pager,below

border_inner_margin 0
border_outer_margin 0

minimum_size 200 250
maximum_width 200

alignment tr
gap_x 35
gap_y 55

# Graphics settings #
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no

# Text settings #
use_xft yes
override_utf8_locale yes
xftfont Neuropolitical:size=8
xftalpha 0.8
uppercase no

temperature_unit celsius

default_color FFFFFF

# Lua Load  #
lua_load ./clock_rings.lua
lua_draw_hook_pre clock_rings

own_window_argb_value 0
own_window_argb_visual yes
own_window_colour 000000
TEXT
${font Neuropolitical:size=42}${time %e}
${goto 100}${font Neuropolitical:size=18}${color FF3300}${voffset -75}${time %b}
${font Neuropolitical:size=10}${color FF3300}${voffset 15}${time %A}${color FF3300}${hr}
${goto 100}${font Neuropolitical:size=15}${color FFFFFF}${voffset -35}${time %Y}
${font Neuropolitical:size=30}${voffset 40}${alignc}${time %H}:${time %M}
${goto 175}${voffset -30}${font Neuropolitical:size=10}${time %S}
${voffset 10}${font Neuropolitical:size=11}${color FF3300}${alignr}HOME${font}
${font Neuropolitical:size=13}${color FFFFFF}${alignr}temp: ${weather http://weather.noaa.gov/pub/data/observations/metar/stations/ LQBK temperature temperature 30} °C${font}
${hr}
${image ./logo.png -p 165,10 -s 35x35}
${color FFFFFF}${font Neuropolitical:size=8}Uptime: ${uptime_short}
${color FFFFFF}${font Neuropolitical:size=8}Processes: ${processes}
${color FFFFFF}${font Neuropolitical:size=8}Running: ${running_processes}

${color FF3300}${goto 125}${voffset 40}CPU
${color FFFFFF}${goto 125}${cpu cpu0}%
${color FF3300}${goto 125}${voffset 55}RAM
${color FFFFFF}${goto 125}${memperc}%
${color FF3300}${goto 125}${voffset 50}Root
${color FFFFFF}${goto 125}${fs_used_perc /}%
${color FF3300}${goto 125}${voffset 55}Home
${color FFFFFF}${goto 125}${fs_used_perc /home}%
${color FF3300}${goto 130}${voffset 50}Net
${color FFFFFF}${goto 130}${downspeed eth0}
${color FFFFFF}${goto 130}${upspeed eth0}

${color FF3300}${font Neuropolitical:size=8}${alignr}${nodename}
${color FF3300}${font Neuropolitical:size=8}${alignr}${pre_exec cat /etc/issue.net}  $machine
${color FF3300}${font Neuropolitical:size=8}${alignr}Kernel: ${kernel}
${hr}

```

---

### Post by harsha8 on 2016-02-21
Dear All,

Changed regional format to English. Everything works fine now. Thanks for help

---

### Post by QIII on 2016-02-21
Odd.

This section

```
${font Neuropolitical:size=42}${time %e}
${goto 100}${font Neuropolitical:size=18}${color FF3300}${voffset -75}${time %b}
${font Neuropolitical:size=10}${color FF3300}${voffset 15}${time %A}${color FF3300}${hr}
${goto 100}${font Neuropolitical:size=15}${color FFFFFF}${voffset -35}${time %Y}
```

which is where your problem is appearing, works fine for me.  I'm scratching my head a bit.

(Not the problem, but arranging the vertical offsets that way seems a bit odd.  There are better ways of doing that part.)

---

### Post by QIII on 2016-02-21
Ah.  OK.  I must have been composing as you made your final post!

---

