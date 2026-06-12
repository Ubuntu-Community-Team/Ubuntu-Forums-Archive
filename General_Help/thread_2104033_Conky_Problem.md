---
title: "Conky Problem"
date: 2013-01-11
forum: General Help
---

### Post by Tindo01 on 2013-01-11
Can someone please tell me how to make my conky window hight 1000 instead of the 600ish px its currently stuck at. I've tried changing own_window_type normal from normal to override to desktop but nothing seems to help. I've increased the text buffer size to 2048 but that didnt do anything. I've set the minimum_size 340 1600  ## width, height and maximum_width 400     ## width:  => minimum width from 340 800 to 340 1600 but that didnt help, i've killed conky and restarted it more times then i can count but i cant seem to get the window any larger then what is shown in this screenshot.[IMG]http://i28.photobucket.com/albums/c244/enul01/Screenshotfrom2013-01-11190422_zps77ab19d2.png[/IMG]

---

### Post by bfmetcalf on 2013-01-11
It would really help to see your entire config.

---

### Post by Tindo01 on 2013-01-12
background yes
use_xft yes
xftfont 123:size=8
xftalpha 0.1
update_interval 0.5
text_buffer_size 2048
total_run_times 0
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
minimum_size 340 1600  ## width, height
maximum_width 400     ## width:  => minimum width
minimum_size 250 5
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no
default_color 
default_shade_color red
default_outline_color green
alignment top_right
gap_x 10
gap_y 10
no_buffers yes
uppercase no
cpu_avg_samples 2
net_avg_samples 1
override_utf8_locale no
use_spacer yes

TEXT
${alignc 100}${color0}${font HandelGotD:size=44}${time %I:%M %P}${font}
${voffset 10}${offset 50}${color0}${font HandelGotD:size=18}${alignc}${time %d %B, %Y}${font}
#SYSTEM
${voffset 20}${offset 20}${color tan}${font HandelGgotD:size=12}System:${font}${color}${color0}
${font HandelGotD:size=10}${offset 50}Uptime $alignr ${uptime}
${offset 50}Ubuntu ${alignr} 12.10
${offset 50}$sysname $kernel $alignr $machine
${offset 50}Intel Pentium D $alignr ${freq_g cpu0}Ghz
#NETWORK
${voffset 20}${offset 20}${color tan}${font HandelGgotD:size=12}Network:${font}${color}${color0}${font HandelGotD:size=10}
${offset 50}Down $alignr ${downspeed eth0} kb/s
${offset 50}Up $alignr ${upspeed eth0} kb/s
${voffset 10}${offset 50}Downloaded: $alignr  ${totaldown eth0}
${offset 50}Uploaded: $alignr  ${totalup eth0}
#PROCESSOR
${voffset 20}${offset 20}${color tan}${font HandelGgotD:size=12}Processor:${font}${color}${color0}${font HandelGotD:size=10}
${offset 50}Core A ${alignr} ${cpu cpu1}%${cpugauge}
${offset 50}Core B ${alignr} ${cpu cpu2}%${cpugauge}
#MEMORY
${voffset 20}${offset 20}${color tan}${font HandelGgotD:size=12}Memory:${font}${color}${color0}${font HandelGotD:size=10}
${offset 50}$mem / $memmax $alignr ${alignr}$memperc% ${memgauge}
#PROCESSES
${voffset 20}${offset 20}${color tan}${font HandelGgotD:size=12}Top Processes:${font}${color}${color0}${font HandelGotD:size=10}
${offset 50}Total Running ${alignr}${processes}
${offset 50}${top_mem name 2}${alignr}${top mem 2} %
${offset 50}${top_mem name 3}${alignr}${top mem 3} %
${offset 50}${top_mem name 4}${alignr}${top mem 4} %
${offset 50}${top_mem name 5}${alignr}${top mem 5} %
#DRIVES
${voffset 20}${offset 20}${color tan}${font HandelGgotD:size=12}Drives:${font}${color}${color0}${font HandelGotD:size=10}
#Gmail
${voffset 20}${offset 20}${color tan}${font HandelGgotD:size=12}Gmail:${font}${color}${color0}${font HandelGotD:size=10}
${offset 50}You have ${texeci 60 perl ~/scripts/gmail.pl n} new gmail(s).${alignr}
${execi 60 perl ~/scripts/gmail.pl s}




sorry about that but here it is.

---

### Post by tomski on 2013-01-12
you have an extra minimum_size do this & restart:
```

minimum_size 340 1600 ## width, height
maximum_width 400 ## width: => minimum width
#minimum_size 250 5

```

---

### Post by Tindo01 on 2013-01-12
Wow i dont know how many times i must have looked at this conkyrc and never saw that. Thank you very much i was starting to pull my hair out lol :p

---

### Post by tomski on 2013-01-12
hehehe I know the feeling :)

don't forget to mark thread as SOLVED ;)

---

