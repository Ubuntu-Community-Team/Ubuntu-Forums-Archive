---
title: "Conky text overwriting itself on the desktop"
date: 2021-08-31
forum: General Help
---

### Post by fiscoking on 2021-08-31
Hi,

I installed Ubuntu Conky today (Aug 31 2021) but the text on the desktop seems to persist between overwriting. This leaves gibberish text on the desktop.

I see others have this issue and I've tried all published fixes, to no avail.

My config file is listed below. I cannot attach it to this post as the forum gives me  'The following errors occurred: .conkyrc: Invalid File' when trying to attach.

Can anyone see what's wrong?

Thanks.

----------------------

```
# Create own window instead of using desktop (required in nautilus)
own_window_class conky
own_window yes
own_window_hints undecorated,below,skip_taskbar,skip_pager
background yes
own_window_transparent yes

# If own_window is yes, you may use type normal, desktop or overide
own_window_type normal

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Don't count buffers as used memory
no_buffers

use_spacer right
use_xft yes
xftfont Terminus:size=10
xftalpha 1

# Update interval in seconds
update_interval 2.0

# Size of window
minimum_size 130
maximum_width 201

# Draw shades?
draw_shades no

# Text stuff
draw_outline yes
draw_borders no
draw_graph_borders yes
uppercase no

# border margins
border_margin 2
stippled_borders 0
border_width 1

# Default colors and also border colors
default_color FFFFFF
default_shade_color 5D009C
default_outline_color 000000

# Text alignment, other possible values are commented
alignment top_left
#alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 5
gap_y 0

override_utf8_locale yes

# stuff after 'TEXT' will be formatted on screen
TEXT
${color #A548CC}Date:${color}${font size=11}    ${time %a %e %b %G}${font}
${color #A548CC}Time:${color}${font size=11}      ${time %I:%M:%p}${font}
${color #A548CC}Uptime:${color}    ${uptime}
${color #A548CC}Kernel:${color}      ${exec uname -r|cut -b1-9}
${color #A548CC}Temp:${color}       ${acpitemp}C
${color #A548CC}CPU:${color}         ${freq_g}GHz  (${cpu}%)

${color #A548CC}Highest CPU:
${color red}${top name 1}${top_mem cpu 1}
${color}${top name 2}${top cpu 2}
${color}${top name 3}${top cpu 3}
${color}${top name 4}${top cpu 4}

${color #A548CC}Highest MEM:
${color red}${top_mem name 1}${top_mem mem 1}
${color}${top_mem name 2}${top_mem mem 2}
${color}${top_mem name 3}${top_mem mem 3}
${color}${top_mem name 4}${top_mem mem 4}

${color #A548CC}MEM:   ${membar 3,100}${alignr}(${memperc}%)
${color}${mem} / ${memmax}  
${color #A548CC}SWAP: ${swapbar 3,100}${alignr}(${swapperc}%)
${color}${swap} / ${swapmax}

${color #A548CC}ROOT:  ${fs_bar 3,100 /}${alignr}(${fs_free_perc /}%)
${color}${fs_used /}/ ${fs_size /}
${color #A548CC}HOME: ${fs_bar 3,100 /home}${alignr}(${fs_free_perc /home}%)
${color}${fs_used /home}/ ${fs_size /home}
${color #A548CC}BOOT:  ${fs_bar 3,100 /boot}${alignr}(${fs_free_perc /boot}%)
${color}${fs_used /boot}/ ${fs_size /boot}
```

---

### Post by fiscoking on 2021-08-31
Update; setting 'own_window_transparent no' has fixed the gibberish text, but now the background is black. Not a deal breaker. I think this might be a bug.

---

### Post by QIII on 2021-08-31
I suspect that you may have your conky running in more than one instance.  As soon as you changed the background, you covered on or the other up, so it looks "good" except for the black background.

You can use top or htop to see houw many instances you are running.  If more than one, issue

```
killall conky

```

to stop all instances and then run your script to start it.

---

### Post by fiscoking on 2021-08-31
Thanks for the tip.

I looked for another config file and the new file below seems to have fixed it. A lot more complicated, but it displays more detail. Screenshot attached. Config file below. I had to install vnstat, vnstati and net-tools. Then set vnstat to monitor my wifi connection (wlo1), then hack the conkyrc file network section to use wlo1.

```
override_utf8_locale yes
use_xft yes
xftfont ubuntu:size=10.5
xftalpha 0.5
uppercase no
no_buffers yes              # Subtract cached and buffered ram from memory usage.
short_units yes             # Use "G" instead of "GiB"

text_buffer_size 2048
update_interval 2.5          # change to .001 for 1000 times per second stress test
own_window_class Conky
own_window yes
own_window_type dock
own_window_transparent no
own_window_argb_visual yes
own_window_argb_value 145  # semi-transparent
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
minimum_size 400
maximum_width 400
alignment top_right

draw_shades yes
# off-white
default_color ECEAE4
# blue
color1 1EB5FF
# light blue
color2 30DDFB
# dark blue
color3 0090ff
# lime
color4 98FF76
default_shade_color 000000

draw_outline no
draw_borders no
stippled_borders 0

TEXT
#------------+
# Distro     |
#------------+
${color}Today is:${color green}$alignr${time %A,}$alignr ${time %e %B %G}
${color}Distribution:${color green}$alignr ${execi 6300 cat /etc/issue.net} $machine
${color}Kernel:$alignr${color green} $kernel
${color orange}${voffset 2}${hr 1}
#------------+
# i5 CPU|
#------------+
${color2}${voffset 5}Intel® i-5 8365U 4100MHz: ${color1}@  ${color green}${freq} MHz
${color}${goto 13}CPU 0 ${goto 81}${color green}${cpu cpu1}% ${goto 131}${color3}${cpubar cpu1 18}
#${cpugauge cpu1 20,40}
#${cpugraph 1 15,200 555555 AAAAAA -l}
${color}${goto 13}CPU 1 ${goto 81}${color green}${cpu cpu2}% ${goto 131}${color3}${cpubar cpu2 18}
${color}${goto 13}CPU 2 ${goto 81}${color green}${cpu cpu3}% ${goto 131}${color3}${cpubar cpu3 18}
${color}${goto 13}CPU 3 ${goto 81}${color green}${cpu cpu4}% ${goto 131}${color3}${cpubar cpu4 18}
${color}${goto 13}CPU 4 ${goto 81}${color green}${cpu cpu5}% ${goto 131}${color3}${cpubar cpu5 18}
${color}${goto 13}CPU 5 ${goto 81}${color green}${cpu cpu6}% ${goto 131}${color3}${cpubar cpu6 18}
${color}${goto 13}CPU 6 ${goto 81}${color green}${cpu cpu7}% ${goto 131}${color3}${cpubar cpu7 18}
${color}${goto 13}CPU 7 ${goto 81}${color green}${cpu cpu8}% ${goto 131}${color3}${cpubar cpu8 18}
#------------+
# Temperature|
#------------+
#${color1}All CPUs ${color green}${cpu}% ${goto 131}${color1}Temp: ${color green}${execpi .001 cat /sys/class/thermal/thermal_zone7/temp | cut -c1-2}°C ${alignr}${color1}Up: ${color green}$uptime
# Next line is for kernel >= 4.13.0-36-generic
${color1}All CPUs ${color green}${cpu}% ${goto 131}${color1}Temp: ${color green}${hwmon 1 temp 1}°C ${alignr}${color1}Up: ${color green}$uptime
# Next line is for temperature with Kerenel 4.4
#${color1}All CPUs ${color green}${cpu}% ${goto 131}${color1}Temp: ${color green}${hwmon 0 temp 1}°C ${alignr}${color1}Up: ${color green}$uptime
${color green}$running_processes ${color1}running of ${color green}$processes ${color1}loaded processes.
${color1}Load Average 1-5-15 minutes: ${alignr}${color green}${execpi .001 (awk '{printf "%s/", $1}' /proc/loadavg; grep -c processor /proc/cpuinfo;) | bc -l | cut -c1-4} ${execpi .001 (awk '{printf "%s/", $2}' /proc/loadavg; grep -c processor /proc/cpuinfo;) | bc -l | cut -c1-4} ${execpi .001 (awk '{printf "%s/", $3}' /proc/loadavg; grep -c processor /proc/cpuinfo;) | bc -l | cut -c1-4}

#------------+
# Prcoesses  |
#------------+
${color1}${voffset 5}Process Name: ${goto 200}PID ${goto 265}CPU% ${alignr}Mem%
${color}${goto 13}${top name 1} ${goto 190}${top pid 1} ${goto 270}${color green}${top cpu 1} ${alignr}${top mem 1}
${color}${goto 13}${top name 2} ${goto 190}${top pid 2} ${goto 270}${color green}${top cpu 2} ${alignr}${top mem 2}
${color}${goto 13}${top name 3} ${goto 190}${top pid 3} ${goto 270}${color green}${top cpu 3} ${alignr}${top mem 3}
${color}${goto 13}${top name 4} ${goto 190}${top pid 4} ${goto 270}${color green}${top cpu 4} ${alignr}${top mem 4}
${color}${goto 13}${top name 5} ${goto 190}${top pid 5} ${goto 270}${color green}${top cpu 5} ${alignr}${top mem 5}
${color}${goto 13}${top name 6} ${goto 190}${top pid 6} ${goto 270}${color green}${top cpu 6} ${alignr}${top mem 6}
${color}${goto 13}${top name 7} ${goto 190}${top pid 7} ${goto 270}${color green}${top cpu 7} ${alignr}${top mem 7}
${color}${goto 13}${top name 8} ${goto 190}${top pid 8} ${goto 270}${color green}${top cpu 8} ${alignr}${top mem 8}
${color}${goto 13}${top name 9} ${goto 190}${top pid 9} ${goto 270}${color green}${top cpu 9} ${alignr}${top mem 9}
${color orange}${voffset 2}${hr 1}
#------------+
# Storage    |
#------------+
${color1}RAM Use/Free:${goto 148}${color red}$mem ${color red} ${goto 220}${membar 15,100} $alignr${color}${memeasyfree}
${color1}Linux Root:${goto 148}${color red}${fs_used /} ${color red} ${goto 220}${fs_bar 15,100 /} $alignr${color}${fs_free /}
${color1}${if_mounted /mnt/old}Broken 16.04:${goto 148}${color red} ${fs_used /mnt/old} ${color red} ${goto 220}${fs_bar 15,100 /mnt/old} $alignr${color}${fs_free /mnt/old}${else}Cache RAM:${goto 148}${color green}${cached} ${color1} ${alignr}Buffers: ${color green} ${buffers}${endif}
${color1}${if_mounted /mnt/e}WSL+Linux:${goto 148}${color red}${fs_used /mnt/e} ${color red} ${goto 220}${fs_bar 15,100 /mnt/e} $alignr${color}${fs_free /mnt/e}${else}Swap:${goto 148}${color green}${swap} / ${swapmax} $alignr${color green}${swapperc}%${endif}
#${color}NVMe Win 10:${goto 148}${if_mounted /mnt/c}${color green} ${fs_used /mnt/c} / ${fs_size /mnt/c} $alignr${color green}${fs_used_perc /mnt/c}%${else}${color yellow}/mnt/c${endif}
#${color}${if_mounted /mnt/d}HGST_Win10:${goto 148}${color red} ${fs_used /mnt/d} / ${fs_size /mnt/d} $alignr${color green}${fs_used_perc /mnt/d}%${else}Cache RAM:${goto 148}${color green}${cached} ${color} Buffers: ${color green} ${buffers}${endif}
#${color}${if_mounted /mnt/e}WSL+Linux:${goto 148}${color red}${fs_used /mnt/e} / ${fs_size /mnt/e} $alignr${color red}${fs_used_perc /mnt/e}%${else}Swap:${goto 148}${color green}${swap} / ${swapmax} $alignr${color green}${swapperc}%${endif}
${color orange}${voffset 2}${hr 1}
#------------+
# Network    |
#------------+
#${color1}Network using vnStat "-i", "-w" and "-m"
${color}${goto 5}Today ${goto 100}Yesterday ${goto 225}Week ${goto 325}Month ${color green}
# vnstatd updates database every five minutes
${execi 300 vnstat -i wlo1 | grep "today" | awk '{print $8" "substr ($9, 1, 1)}'} ${goto 110}${execi 300 vnstat -i wlo1 | grep "yesterday" | awk '{print $8" "substr ($9, 1, 1)}'} ${goto 220}${execi 300 vnstat -i wlo1 -w | grep "current week" | awk '{print $9" "substr ($10, 1, 1)}'} ${goto 315}${execi 300 vnstat -i wlo1 -m | grep "`date +"%b '%y"`" | awk '{print $9" "substr ($10, 1, 1)}'}
${color}Down: ${color green}${downspeed wlo1}/s ${color}${goto 220}Up: ${color green}${upspeed wlo1}/s
${downspeedgraph wlo1 25,190 000000 ff0000} ${alignr}${upspeedgraph wlo1 25,190 000000 00ff00}$color
Total: ${color green}${totaldown wlo1} $color${alignr}Total: ${color green}${totalup wlo1}
#Bit Rate:$color ${wireless_bitrate wlo1}
```

[IMG]https://images2.imgbox.com/60/c2/oMQL0CWU_o.jpg[/IMG]

Regards.

---

