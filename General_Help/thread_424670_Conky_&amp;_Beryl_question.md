---
title: "Conky &amp; Beryl question"
date: 2007-04-26
forum: General Help
---

### Post by matthinckley on 2007-04-26
OK I did search for this but couldn't find anything.  

I got conky working like I like it but the borders are shadowed.  Somebody said to make a sleeping script to rectify this but I don't know how to do that.  Some direction on that would be appreciated.

Also when I rotate my cube I have it set to be transparent, not completely but anyways the area behind conky is not transparent.

Thanks in advance!

Matt

---

### Post by m.musashi on 2007-04-27
You can make a script like this:
```
#!/bin/bash
sleep 10 && conky;
```
Save it as .conky_start.sh or similar and chmod it.
```
chmod a+x .conky_start.sh
```
and add it to the start up (use the full path to the command) system -> preferences -> sessions. Change the 10 for a longer or shorter delay in seconds.

---

### Post by spankymasterc on 2007-04-27
make it  15 seconds because somethimes it still conflicts and is still annoying......

---

### Post by matthinckley on 2007-04-27
Thanks! That fixed both problems!

---

### Post by n8bounds on 2007-05-05
Does this work for you in KDE?  It doesnt transparentify correctly for me there with Beryl/Emerald.  

Here's my .conkyrc
```

# Conky configuration
background yes
use_xft yes
xftfont Monospace:size=9
xftalpha 0.8
out_to_console no
update_interval 2
total_run_times 0
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders yes
stippled_borders 5
border_margin 4
border_width 1
default_color orange
default_shade_color black
default_outline_color black
alignment top_left
no_buffers no
uppercase no
cpu_avg_samples 2
net_avg_samples 2
override_utf8_locale yes
use_spacer no

TEXT
Load: ${color white}$loadavg ${color}-- CPU:${color white} ${cpu cpu1}% ${color}-- RAM:${color white} $memperc%  $mem/$memmax ${color}-- DISK:${color white} ${fs_used_perc /}% ${fs_used /}/${fs_size /}${color} -- NETWORK: ${color white}${addr wlan0} Down ${color green}${downspeed wlan0}k/s${color white} Up ${color red}${upspeed wlan0}k/s${color} -- BAT: ${color white}${battery BAT0}${color} -- UPTIME: ${color white}${uptime}  


```

(See screenshot)

---

