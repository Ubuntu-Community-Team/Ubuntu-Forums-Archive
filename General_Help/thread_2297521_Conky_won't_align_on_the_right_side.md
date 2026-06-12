---
title: "Conky won't align on the right side"
date: 2015-10-04
forum: General Help
---

### Post by cody27 on 2015-10-04
I've used Ubuntu for a long time, but I've never tried using Conky.

Well today I've jumped into it and found a Conky script that I like and can learn from. The first learning point is the fact that it will only align to the left side of the screen.

I'm assuming the "alignment top_right" has something to do with it, but I'm not sure what's going wrong or if my assumption is wrong.

I'm assuming that the first part of it, before the output is the windows it's showing and their properties.

```

# conky configuration#
##############################################
# Settings
##############################################
background yes
use_xft yes
xftfont Liberation Sans:size=9
xftalpha 1
update_interval 1.0
total_run_times 0
own_window yes
own_window_type dock
own_window_argb_visual yes
own_window_argb_value 0
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
minimum_size 200 200
maximum_width 240
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no
default_color ffffff
default_shade_color 000000
default_outline_color 828282
alignment top_right
gap_x 1700
gap_y 56
no_buffers yes
uppercase no
cpu_avg_samples 2
override_utf8_locale no
##############################################
#  Output
##############################################
TEXT
SYSTEM INFO
${hr}
Host:$alignr$nodename
Uptime:$alignr$uptime
RAM:$alignr$mem/$memmax
Swap usage:$alignr$swap/$swapmax
Disk usage:$alignr${fs_used /}/${fs_size /}
CPU usage:$alignr${cpu cpu0}%
Temperature: $alignr${acpitemp} F


PROCESSOR
${HR}
CPU 1: ${cpu cpu1}% ${cpubar cpu1}
CPU 2: ${cpu cpu2}% ${cpubar cpu2}


MEMORY
${hr}
RAM $alignc $mem / $memmax $alignr $memperc%
$membar


HARD DRIVE
${hr}
$alignc ${fs_used /} / ${fs_size /} $alignr ${fs_used_perc /}%
${fs_bar /}


TOP PROCESSES
${hr}
${top_mem name 1}${alignr}${top mem 1} %
${top_mem name 2}${alignr}${top mem 2} %
$font${top_mem name 3}${alignr}${top mem 3} %
$font${top_mem name 4}${alignr}${top mem 4} %
$font${top_mem name 5}${alignr}${top mem 5} %

```

---

### Post by deadflowr on 2015-10-04
It's the gap x setting.
now imagine how far over from the right 1700 pixels is.

Set it lower to something like 0 or 5 or 10 or 20 or something like that.
See how that works.

---

### Post by cody27 on 2015-10-04
The gap x setting isn't changing anything. 
Is there something I have to do besides just changing the number and saving the file?

---

### Post by deadflowr on 2015-10-04
Oh, try changing own_window type to normal instead of dock.
Looks like dock places it over on the left regardless.

---

### Post by cody27 on 2015-10-04
Perfect! Thank you! 
Do you know why dock places it left like that?

---

