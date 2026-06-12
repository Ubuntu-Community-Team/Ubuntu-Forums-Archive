---
title: "Conky annoyance..."
date: 2014-04-26
forum: General Help
---

### Post by timgood on 2014-04-26
Have elegant conky running on Kubuntu 14.04 64 bit and everything is working fine apart from one niggling annoyance: the numbers in the CPU percentage overwrite each other with the bottom one visible as in the attached picture. 

.conkyrc as follows:

```
# Elegant Conky settings #
background no
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
own_window_type override
own_window_argb_visual yes
own_window_argb_value 0
own_window_type normal
own_window_hints undecorate,sticky,skip_taskbar,skip_pager,below

border_inner_margin 0
border_outer_margin 0

minimum_size 200 250
maximum_width 200

alignment tr
gap_x 35
gap_y 50

# Graphics settings #
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no

# Text settings #
use_xft yes
xftfont Sans Serif:size=9
xftalpha 0.8
text_buffer_size 2048

uppercase no

temperature_unit celsius


default_color FFFFFF

# Lua Load  #
lua_load ~/.conky/clock_rings.lua
lua_draw_hook_pre clock_rings

TEXT
${voffset 8}${color FF6600}${font Sans Serif:size=16}${time %A}${font}${voffset -8}${alignr 50}${color FFFFFF}${font Sans Serif:size=38}${time %e}${font}
${color FFFFFF}${voffset -30}${color FFFFFF}${font Sans Serif:size=18}${time %b}${font}${voffset -3} ${color FFFFFF}${font Sans Serif:size=20}${time %Y}${font}${color FF6600}${hr}
${voffset 140}${font Sans Serif:size=10}${alignr}${time %H:%M}${font}${color}

${pre_exec lsb_release -ircs} ${color FF6600}${hr}${color}

Kernel: ${alignr}${kernel}
Uptime: ${alignr}${uptime}
Temperature: ${alignr}${execi 8 sensors atk0110-acpi-0 | grep CPU\ Temperature:\ | cut -c 22-25}°C
CPU1: ${cpu cpu1}% ${alignr}${color FF6600}${cpugraph cpu1 8,60 FF6600 FFFFFF}${color}
CPU2: ${cpu cpu2}% ${alignr}${color FF6600}${cpugraph cpu2 8,60 FF6600 FFFFFF}${color}
CPU3: ${cpu cpu3}% ${alignr}${color FF6600}${cpugraph cpu3 8,60 FF6600 FFFFFF}${color}
CPU4: ${cpu cpu4}% ${alignr}${color FF6600}${cpugraph cpu4 8,60 FF6600 FFFFFF}${color}
CPU5: ${cpu cpu5}% ${alignr}${color FF6600}${cpugraph cpu5 8,60 FF6600 FFFFFF}${color}
CPU6: ${cpu cpu6}% ${alignr}${color FF6600}${cpugraph cpu6 8,60 FF6600 FFFFFF}${color}
CPU7: ${cpu cpu7}% ${alignr}${color FF6600}${cpugraph cpu7 8,60 FF6600 FFFFFF}${color}
CPU8: ${cpu cpu8}% ${alignr}${color FF6600}${cpugraph cpu8 8,60 FF6600 FFFFFF}${color}
RAM: $memperc% ${alignr}${color FF6600}${memgraph 8,60 FF6600 FFFFFF}${color}

Top Processes ${color FF6600}${hr}${color}

${top_mem name 1}$alignr${color FF6600}${top_mem cpu 1}${color}${top_mem mem 1}
${top_mem name 2}$alignr${color FF6600}${top_mem cpu 2}${color}${top_mem mem 2}
${top_mem name 3}$alignr${color FF6600}${top_mem cpu 3}${color}${top_mem mem 3}

Network Statistics ${color FF6600}${hr}${color}
${if_existing /proc/net/route wlan0}
Up: ${upspeed wlan0} kb/s ${alignr}${upspeedgraph wlan0 8,60 FF6600 FFFFFF}
Down: ${downspeed wlan0} kb/s ${alignr}${downspeedgraph wlan0 8,60 FF6600 FFFFFF}
Upload: ${alignr}${totalup wlan0}
Download: ${alignr}${totaldown wlan0}
Signal: ${wireless_link_qual wlan0}% ${alignr}${wireless_link_bar 8,60 wlan0}
IP Address: ${alignr}${addr wlan0}
${else}${if_existing /proc/net/route eth0}
Up: ${upspeed eth0} kb/s ${alignr}${upspeedgraph eth0 8,60 FF6600 FFFFFF}
Down: ${downspeed eth0} kb/s ${alignr}${downspeedgraph eth0 8,60 FF6600 FFFFFF}
Upload: ${alignr}${totalup eth0}
Download: ${alignr}${totaldown eth0}
IP Address: ${alignr}${addr eth0}
${else}${if_existing /proc/net/route eth1}
Up: ${upspeed eth1} kb/s ${alignr}${upspeedgraph eth1 8,60 FF6600 FFFFFF}
Down: ${downspeed eth1} kb/s ${alignr}${downspeedgraph eth1 8,60 FF6600 FFFFFF}
Upload: ${alignr}${totalup eth1}
Download: ${alignr}${totaldown eth1}
IP Address: ${alignr}${addr eth1}
${else}
Network Unavailable${endif}${endif}${endif}

```

Any ideas as to how I can fix it?

---

### Post by QIII on 2014-04-26
Hello!

Obviously we can't see the whole thing, but it almost looks to me as though you have a second instance of your conky running and the slight difference in the exact start of the execution means that each is getting slightly different values at the time they refresh.  Some things that don't change quickly are just matching and overlaying each other without being noticed.

Are you sure you only have one instance of your conky running at a time?

When you shut down, do you have it set to restart a new session when rebooted?  Are you running the script at startup?  If you are restoring a previous session and also running the script at startup each time, you can build up a big pile of conky windows.

Go to the terminal and killall conky.  Then start a single instance and see if it looks that way.

---

### Post by ajgreeny on 2014-04-26
> **QIII said:**
> Hello!

Obviously we can't see the whole thing, but it almost looks to me as though you have a second instance of your conky running and the slight difference in the exact start of the execution means that each is getting slightly different values at the time they refresh.  Some things that don't change quickly are just matching and overlaying each other without being noticed.

Are you sure you only have one instance of your conky running at a time?

When you shut down, do you have it set to restart a new session when rebooted?  Are you running the script at startup?  If you are restoring a previous session and also running the script at startup each time, you can build up a big pile of conky windows.

Go to the terminal and killall conky.  Then start a single instance and see if it looks that way.
I had this problem using Xubuntu 14.04 and found exactly the problem mentioned by QIII.

In spite of not saving sessions at logout, they did seem to be saved and some applications running at logout would restart.  I solved it with a complex command in the startup applications listing, which checks for conky running and if so does not spawn another instance.
Enter ```
bash -c "sleep 15; if pgrep conky; then exit; else conky; fi"
```in the command box for your KDE startup apps and it may solve the problem, or just set KDE to not restore your session when logging out and in again.

---

### Post by timgood on 2014-04-26
Thanks guys! There were indeed 2 instances of conky running. I will use your command ajgreeny, thank a lot.

---

