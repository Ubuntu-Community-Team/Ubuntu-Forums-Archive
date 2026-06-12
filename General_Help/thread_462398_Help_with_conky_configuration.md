---
title: "Help with conky configuration"
date: 2007-06-02
forum: General Help
---

### Post by kr0w on 2007-06-02
Hi there!

I want to know how can I make the output of the memory and disk usage look in the format {M,G} (for megs o gigs) instead of the default {MiB,GiB}.

Thanks...

---

### Post by mrcbrown on 2007-06-02
Where are you wanting to see this" - Would be my first question, if your using command line tools like du you can append -h for human readable out-put. Post what app in particular your wanting MB/GB sizes listed.

---

### Post by kr0w on 2007-06-02
It's for the conky output.
I've seen screenshots with the M,G format, so I know it's possible, but I couldn't find any config example...

---

### Post by kr0w on 2007-06-03
Ok, found a way...

In other configs, people just use the commands of the conky config (like fs_free for file system free space), but what I've done is use bash commands, combined with grep and cut so I could output their formats...
Thus...

```
${color}/dev/sda2 (${exec df -h / /home /media/hda1 /media/hda2 | grep sda2 | cut -c35-38}) ${color}${fs_bar 3,000 /}
```

...will use the df output instead of fs_free's.
(the -h, as a df option, stands for human readable)

[ [IMG]http://www.imagehosting.com/out.php/i726059_screenshot2.png[/IMG]](http://www.imagehosting.com)

Here's my conky config...

```
# Conky configuration
background yes
use_xft yes
xftfont Monospace:size=9
xftalpha 0.8
out_to_console no
update_interval 1
total_run_times 0
own_window yes
own_window_type override
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
default_color white
default_shade_color black
default_outline_color black
alignment top_right
gap_x 10
gap_y 40
no_buffers yes
uppercase no
cpu_avg_samples 2
net_avg_samples 2
override_utf8_locale yes
use_spacer no

TEXT
${color}$nodename - $alignc$sysname $kernel on $machine
Logged in as: ${exec whoami}
$color$stippled_hr
${color}Date: ${color}${time %A, %d %B}
${color}Time: ${color}${time %k:%M:%S}${alignr}${color}Uptime: ${color}$uptime
$color$stippled_hr
${alignc}${color orange}Temperatures
${alignc}${color}CPU: ${color}${i2c 9191-0290 temp 2}°C${color} - ${color}MB: ${color}${i2c 9191-0290 temp 1}°C - ${color}HDD Temp: ${execi 5 nc localhost 7634 | cut -c54-55 ;}°C
$color$stippled_hr
${color}CPU:${color}  ${cpu cpu1}% ${cpubar 3,000 cpu1}
${cpugraph 20,0 ffffff ffffff}
${color}RAM: $memperc% ${color}${exec free -m | grep s/c | cut -c27-29}M/${exec free -m | grep Mem | cut -c15-18}M ${membar 3,000}
${color}Swap: $swapperc% ${color}${exec free -m | grep Swap | cut -c27-29}M/${exec free -m | grep Swap | cut -c16-18}M  ${swapbar 3,000}
$color$stippled_hr
${alignc}${color orange}Network
${alignc}${color}eth0: ${color}${addr eth0}${color}
${color}Up:   ${color}${upspeed eth0}kb/s${color}${alignr}${color}Down: ${color}${downspeed eth0}kb/s${color}
${upspeedgraph eth0 20,140 ff0000 ff0000} ${alignr}${downspeedgraph eth0 20,140 00ff00 00ff00}$color
$color$stippled_hr
${alignc}${color orange}File systems
${color}Device    Free:  Usage:
${color}/dev/sda2 (${exec df -h / /home /media/hda1 /media/hda2 | grep sda2 | cut -c35-38}) ${color}${fs_bar 3,000 /}
${color}/dev/sda3 (${exec df -h / /home /media/hda1 /media/hda2 | grep sda3 | cut -c36-38})  ${color}${fs_bar 3,000 /home}
${color}/dev/hda1 (${exec df -h / /home /media/hda1 /media/hda2 | grep hda1 | cut -c35-38}) ${color}${fs_bar 3,000 /media/hda1}
${color}/dev/hda2 (${exec df -h / /home /media/hda1 /media/hda2 | grep hda2 | cut -c36-38})  ${color}${fs_bar 3,000 /media/hda2}
```

---

### Post by herbster on 2007-06-14
> **kr0w said:**
> Ok, found a way...

In other configs, people just use the commands of the conky config (like fs_free for file system free space), but what I've done is use bash commands, combined with grep and cut so I could output their formats...
Thus...

```
${color}/dev/sda2 (${exec df -h / /home /media/hda1 /media/hda2 | grep sda2 | cut -c35-38}) ${color}${fs_bar 3,000 /}
```

...will use the df output instead of fs_free's.
(the -h, as a df option, stands for human readable)

[ [IMG]http://www.imagehosting.com/out.php/i726059_screenshot2.png[/IMG]](http://www.imagehosting.com)

Here's my conky config...

```
# Conky configuration
background yes
use_xft yes
xftfont Monospace:size=9
xftalpha 0.8
out_to_console no
update_interval 1
total_run_times 0
own_window yes
own_window_type override
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
default_color white
default_shade_color black
default_outline_color black
alignment top_right
gap_x 10
gap_y 40
no_buffers yes
uppercase no
cpu_avg_samples 2
net_avg_samples 2
override_utf8_locale yes
use_spacer no

TEXT
${color}$nodename - $alignc$sysname $kernel on $machine
Logged in as: ${exec whoami}
$color$stippled_hr
${color}Date: ${color}${time %A, %d %B}
${color}Time: ${color}${time %k:%M:%S}${alignr}${color}Uptime: ${color}$uptime
$color$stippled_hr
${alignc}${color orange}Temperatures
${alignc}${color}CPU: ${color}${i2c 9191-0290 temp 2}°C${color} - ${color}MB: ${color}${i2c 9191-0290 temp 1}°C - ${color}HDD Temp: ${execi 5 nc localhost 7634 | cut -c54-55 ;}°C
$color$stippled_hr
${color}CPU:${color}  ${cpu cpu1}% ${cpubar 3,000 cpu1}
${cpugraph 20,0 ffffff ffffff}
${color}RAM: $memperc% ${color}${exec free -m | grep s/c | cut -c27-29}M/${exec free -m | grep Mem | cut -c15-18}M ${membar 3,000}
${color}Swap: $swapperc% ${color}${exec free -m | grep Swap | cut -c27-29}M/${exec free -m | grep Swap | cut -c16-18}M  ${swapbar 3,000}
$color$stippled_hr
${alignc}${color orange}Network
${alignc}${color}eth0: ${color}${addr eth0}${color}
${color}Up:   ${color}${upspeed eth0}kb/s${color}${alignr}${color}Down: ${color}${downspeed eth0}kb/s${color}
${upspeedgraph eth0 20,140 ff0000 ff0000} ${alignr}${downspeedgraph eth0 20,140 00ff00 00ff00}$color
$color$stippled_hr
${alignc}${color orange}File systems
${color}Device    Free:  Usage:
${color}/dev/sda2 (${exec df -h / /home /media/hda1 /media/hda2 | grep sda2 | cut -c35-38}) ${color}${fs_bar 3,000 /}
${color}/dev/sda3 (${exec df -h / /home /media/hda1 /media/hda2 | grep sda3 | cut -c36-38})  ${color}${fs_bar 3,000 /home}
${color}/dev/hda1 (${exec df -h / /home /media/hda1 /media/hda2 | grep hda1 | cut -c35-38}) ${color}${fs_bar 3,000 /media/hda1}
${color}/dev/hda2 (${exec df -h / /home /media/hda1 /media/hda2 | grep hda2 | cut -c36-38})  ${color}${fs_bar 3,000 /media/hda2}
```

Wow, after searching for a few days I finally used your commands to get my doggone CPU & mobo temps to work in conky!!!

Man thanks again.. I'm curious though, how did you discover or know that it's i2c 9191-0290 ??

---

