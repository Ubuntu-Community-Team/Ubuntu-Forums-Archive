---
title: "Conky covers other windows?"
date: 2008-05-21
forum: General Help
---

### Post by chunchengch on 2008-05-21
[ATTACH]70949[/ATTACH]

I am new to conky, and face a problem as screenshot shows, the conky covers other windows, need help to solve it, thanks a lot!

BTW, as you can see in the screenshot, the information of running processes are not aligned in order, how can I modify the conkyrc to fix it? thanks!

here is the content of conkyrc:

[COLOR="SeaGreen"]# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
own_window_hints undecorated,below,sticky,skip_taskbar,skip_taskbar
background no

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer right
use_xft yes

# Update interval in seconds
update_interval 3.0

# Minimum size of text area
minimum_size 250 5

# Draw shades?
draw_shades yes

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no

uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 8

# border margins
border_margin 4

# border width
border_width 1

# Default colors and also border colors, grey90 == #e5e5e5
default_color white
default_shade_color black
default_outline_color white

own_window_color transparent
own_window_transparent yes

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 20
gap_y 50

# stuff after 'TEXT' will be formatted on screen

#override_utf8_locale no
#xftfont Terminus:size=8
#xftalpha 0.8


TEXT
$nodename - $sysname $kernel on $machine
$hr
${color grey}Uptime:$color $uptime
${color grey}Frequency (in MHz):$color $freq
${color grey}Frequency (in GHz):$color $freq_g
${color grey}RAM Usage:$color $mem/$memmax - $memperc% ${membar 4}
${color grey}Swap Usage:$color $swap/$swapmax - $swapperc% ${swapbar 4}
${color grey}CPU Usage:$color $cpu% ${cpubar 4}
${color grey}Processes:$color $processes  ${color grey}Running:$color $running_processes
$hr
${color grey}File systems (Free/Total):
 / $color${fs_free /}/${fs_size /} ${fs_bar 6 /}
${color grey}Networking (Wired eth0):
Up:$color ${upspeed eth0} k/s${color grey} - Down:$color ${downspeed eth0} k/s
${color grey}Networking (Wireless wlan0):
Up:$color ${upspeed wlan0} k/s${color grey} - Down:$color ${downspeed wlan0} k/s
$hr
${color grey}Name                  PID   CPU%   MEM%
${color lightgrey} ${top name 1} ${top pid 1} ${top cpu 1} ${top mem 1}
${color lightgrey} ${top name 2} ${top pid 2} ${top cpu 2} ${top mem 2}
${color lightgrey} ${top name 3} ${top pid 3} ${top cpu 3} ${top mem 3}
${color lightgrey} ${top name 4} ${top pid 4} ${top cpu 4} ${top mem 4}[/COLOR]

---

### Post by ad_267 on 2008-05-21
I think you want to remove this line:
```
own_window_type override
```

---

### Post by chunchengch on 2008-05-21
> **ad_267 said:**
> I think you want to remove this line:
```
own_window_type override
```

Thanks! it does the trick.

---

### Post by Espeeko on 2010-04-27
Thanks a lot this worked great

---

