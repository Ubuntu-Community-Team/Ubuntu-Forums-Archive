---
title: "Conky cutting off the bottom of display :("
date: 2008-06-11
forum: General Help
---

### Post by remicks916 on 2008-06-11
ok here is my .conkyrc:
-------------------------------------------------------------------

background yes
use_xft yes
xftfont HandelGotD:size=9
xftalpha 0.5
update_interval 1.0
total_run_times 0
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
minimum_size 700 150
maximum_width 200
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders yes
default_color white
default_shade_color red
default_outline_color green
alignment mr
gap_x 12
gap_y 48
no_buffers yes
uppercase no
cpu_avg_samples 2
override_utf8_locale no

TEXT
$alignc $sysname $kernel

uptime $alignr ${color 3676B2}$uptime${color}
load $alignr ${color 3DCC3D}$loadavg${color}

hostname $alignr ${color de0b0b}$nodename${color}
users $alignr ${color de0b0b}$user_number${color}

cpu ${font HandelGotD:size=7}$alignr ${cpu cpu0}%${font}
${cpubar cpu0}
ram ${font HandelGotD:size=7}$alignc $mem / $memmax $alignr $memperc%${font}
$membar
swap ${font HandelGotD:size=7}$alignc $swap / $swapmax $alignr $swapperc%${font}
${swapbar}
root ${font HandelGotD:size=7}$alignc ${fs_free /} / ${fs_size /} $alignr ${fs_free_perc /}%${font}
${fs_bar /}
storage ${font HandelGotD:size=7}$alignc ${fs_free /media/storage} / ${fs_size /media/storage} $alignr ${fs_free_perc /media/storage}%${font}
${fs_bar /media/storage}
xternal ${font HandelGotD:size=7}$alignc ${fs_free /media/external} / ${fs_size /media/external} $alignr ${fs_free_perc /media/external}%${font}
${fs_bar /media/external}

$alignc ${color 3676B2}$processes${color} processes (${color 3DCC3D}$running_processes ${color}running)

${color 3676B2}Highest CPU${color}:
${color de0b0b}${top name 1}${top_mem cpu 1}
${color white}${top name 2}${top cpu 2}
${top name 3}${top cpu 3}

${color 3DCC3D}Highest RAM${color}:
${color de0b0b}${top_mem name 1}${top_mem mem 1}
${color white}${top_mem name 2}${top_mem mem 2}
${top_mem name 3}${top_mem mem 3}

${color de0b0b}Networking${color}:
Down:${color} $alignr ${downspeed eth0} KB/s${color} ${offset 80}
$alignc ${downspeedgraph eth0 18,150 3DCC3D 3DCC3D}
Up:${color} $alignr ${upspeed eth0} KB/s ${offset 80}
$alignc ${upspeedgraph eth0 18,150 3676B2 3676B2}

-------------------------------------------------------------------

Now whenever I load conky (this didn't used to happen) it cuts off the bottom of its display window. I've tried reducing the size of some items just to have it cut off the same amount and make the window smaller... any help with this is greatly appreciated.

Cheers

[IMG]http://i170.photobucket.com/albums/u241/remicksdnb/Screenshot-3.png[/IMG]

---

### Post by Tom--d on 2008-06-11
minimum_size 700 150

There is your problem. change it to a smaller number :)

---

### Post by remicks916 on 2008-06-11
Thanks!

---

