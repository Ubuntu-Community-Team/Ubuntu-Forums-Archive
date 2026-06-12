---
title: "conky help"
date: 2008-05-09
forum: General Help
---

### Post by Greenducky on 2008-05-09
Hey everyone,

i am kind of new to conky. i would like it to be able to tell me my cpu temps. i donot know how.
i have got a theme that i like and i have pasted it in the .conkyrc file in my home folder and it works fine. well
kind of. for my IP address it just says 0.0.0.0 and for traffic it just says up 0 down 0 it never changes.

if anyone has any good answers that would be cool.

hear is a copy of my .conkyrc file.



background yes
use_xft yes
xftfont DejaVu Sans Mono:size=8
xftalpha 0.8
out_to_console no
update_interval 5.0
total_run_times 0
draw_shades no
own_window yes
own_window_colour 303030
own_window_type desktop
double_buffer yes
default_color 555753
color1 grey
alignment top_left
gap_x 2
gap_y 2
#no_buffers yes
use_spacer yes

TEXT
$nodename ${color1}$kernel ${color}up ${color1}$uptime ${color}cpu1 ${color1}${cpu cpu1}% ${cpubar 6,40 cpu1} ${freq cpu1}MHz ${color}cpu2 ${color1}${cpu cpu2}% ${cpubar 6,40 cpu2} ${freq cpu2}MHz ${color}mem ${color1}$memperc% ${membar 6,40} ${color}disk ${color1}${fs_used /}/${fs_size /} ${fs_bar 6,40 /} ${color}load ${color1}$loadavg ${color}ip ${color1}${addr ath0} ${color}traffic ${color1}${downspeed ath0}/ ${upspeed ath0}Kb/s ${color}battery ${color1}$battery

---

### Post by oyvindaa on 2008-05-09
For CPU temp you could try ${acpitemp}C

Have you tried eth0 instead of ath0?

See other .conkyrc configurations [here]("http://ubuntuforums.org/showthread.php?t=281865&highlight=conky")

---

### Post by SkonesMickLoud on 2008-05-11
And if you prefer Farenheit, use ${acpitempf} F

---

