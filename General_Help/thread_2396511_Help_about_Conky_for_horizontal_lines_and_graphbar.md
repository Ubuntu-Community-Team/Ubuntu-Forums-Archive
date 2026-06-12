---
title: "Help about Conky for horizontal lines and graph/bar fill color"
date: 2018-07-17
forum: General Help
---

### Post by requiem8 on 2018-07-17
Hi,

Here is my Conky; 

[IMG]https://s22.postimg.cc/656fwedgx/conky.png[/IMG]

Here is my config;

```
alignment top_right
background yes
border_width 2
cpu_avg_samples 0
default_color white
default_outline_color black
default_shade_color black
default_bar_size 0 5
double_buffer yes
draw_borders no
draw_graph_borders no
draw_outline no
draw_shades no
use_xft yes
xftfont terminus:size=9
gap_x 10
gap_y 35
minimum_size 200 100
maximum_width 185
net_avg_samples 2
no_buffers yes
out_to_console no
out_to_stderr no
extra_newline no
own_window yes
own_window_class Conky
own_window_transparent no
own_window_type override
own_window_colour 474747
stippled_borders 0
update_interval 1.0
uppercase no
use_spacer none
show_graph_scale no
show_graph_range no


TEXT
${font Terminus:style=bold:size=20}${color #d56002}${alignc} ${time %H:%M:%S}${color}${font}

${voffset -29}
${color #d56002}${hr 3,5}${color}
${voffset -10}
${color white}System:${color} Ubuntu 12.04 LTS
${color white}Kernel:${color} ${kernel}
${color white}Uptime:${color} ${uptime}

${voffset -29}
${color #d56002}${hr 3,5}${color}
${voffset -10}
${font Terminus:style=bold:size=9}Processors
${font}${color #d56002}${cpugraph cpu0}${color}
CPU1: ${cpu cpu1}% 
${color #d56002}${cpubar cpu1}${color}
CPU2: ${cpu cpu2}% 
${color #d56002}${cpubar cpu2}${color}

${voffset -29}
${color #d56002}${hr 3,5}${color}
${voffset -10}
${font Terminus:style=bold:size=9}Memory
${font}RAM ${alignc}    $mem/$memmax  $alignr $memperc%
${color #d56002}${membar}${color}

${voffset -29}
${color #d56002}${hr 3,5}${color}
${voffset -10}
${font Terminus:style=bold:size=9}Processes                    ${font Terminus:size=9}CPU%
${voffset -12}
${font}${top name 1}$alignr${top cpu 1}%
${top name 2}$alignr${top cpu 2}%
${top name 3}$alignr${top cpu 3}%
${top name 4}$alignr${top cpu 4}%
${top name 5}$alignr${top cpu 5}%
${top name 5}$alignr${top cpu 6}%
${top name 5}$alignr${top cpu 7}%

${voffset -29}
${color #d56002}${hr 3,5}${color}
${voffset -10}
${font Terminus:style=bold:size=9}Network
${font}IP Address: $alignr ${addr wlan0}
SSID: $alignr ${wireless_essid wlan0}
DLS: ${downspeed wlan0}/s $alignr ${totaldown wlan0}
${color #d56002}${downspeedgraph wlan0}${color}
ULS: ${upspeed wlan0}/s $alignr ${totalup wlan0}
${color #d56002}${upspeedgraph wlan0}${color}

${voffset -29}
${color #d56002}${hr 3,5}${color}
${voffset -10}
${font Terminus:style=bold:size=9}Hard drives
${font}${color white}root${color}${alignr}${fs_free /}/${fs_size /}
${color #d56002}${fs_bar 4,166 /}
${color white}/home${color}${alignr}${fs_free /home}/${fs_size /home}
${color #d56002}${fs_bar 4,166 /home}
```


I've been struggling since two days for finding how can I increase the length of hr lines until the border and how can I fill up the graph and bar background to black.

Here is a picture to help you understand what I mean:


[https://s22.postimg.cc/sjo4cgnwh/diehard4conky.png](https://s22.postimg.cc/sjo4cgnwh/diehard4conky.png)


Thanks.

---

### Post by ajgreeny on 2018-07-17
There are two very important points to make here.
[LIST=1]
[*]Ubuntu 12.04 has been out of support now for almost 18 months so you will find it very hard to get any support from anyone here; you really must update your OS to a fully supported version, either 16.04 or 18.04 would be my recommendation as 14.04 though still supported only has 8 months left. Using an unsupported version of Ubuntu is a serious security risk.
[*]The version of conky in 12.04 is now very old and the config file has changed hugely from what you are showing
[/LIST]
Please update the OS version and then come back if you can not sort out your conky difficulty.

---

