---
title: "128 character limit in conky"
date: 2008-04-28
forum: General Help
---

### Post by SecondTwo on 2008-04-28
Hi all,
    After upgrading to Hardy, I've noticed that conky only displays the first 128 characters of any text I ask it to show (see screenshot).  Is there any way to get around this?  I feel like this wasn't an issue in Gutsy, although as I only discovered conky about 3 weeks ago I can't be sure on that.

Also, my battery seems to skip from 98% -> 99% -> 185% charged.  From the terminal, acpi caps at 100%.  Thoughts?

Thanks, Nick

My .conkyrc:
```
# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer right 
use_xft no

# Update interval in seconds
update_interval 3.0

# Minimum size of text area
# minimum_size 250 5

# Draw shades?
draw_shades no

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no
font arial
uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 3

# border margins
border_margin 9

# border width
border_width 10

# Default colors and also border colors, grey90 == #e5e5e5
default_color grey

own_window_colour brown
own_window_transparent yes

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 10
gap_y 15

# stuff after 'TEXT' will be formatted on screen

#${color orange}SYSTEM ${hr 2}$color
#$nodename $sysname $kernel on $machine

TEXT
$color
${color orange}CPU ${hr 2}$color
${freq}MHz   Load: ${loadavg}   Temp: ${acpitemp}
$cpubar
${cpugraph 000000 ffffff}
NAME             PID       CPU%      MEM%
${top name 1} ${top pid 1}   ${top cpu 1}    ${top mem 1}
${top name 2} ${top pid 2}   ${top cpu 2}    ${top mem 2}
${top name 3} ${top pid 3}   ${top cpu 3}    ${top mem 3}
${top name 4} ${top pid 4}   ${top cpu 4}    ${top mem 4}

${color orange}MEMORY / DISK ${hr 2}$color
RAM:   $memperc%   ${membar 6}$color
Swap:  $swapperc%   ${swapbar 6}$color

Root:  ${fs_free_perc /}%    ${fs_bar 6 /}$color 
Home:  ${fs_free_perc /home}%    ${fs_bar 6 /home}$color 
Windows:  ${fs_free_perc /windows}%  ${fs_bar 6 /windows}$color
${if_mounted /media/MAXTOR}MAXTOR:  ${fs_free_perc /media/MAXTOR}%  ${fs_bar 6 /media/MAXTOR}$color ${endif}

Battery:  ${battery_percent BAT0}%   ${battery_bar BAT0}

${color orange}WIRELESS NETWORK (${addr eth1}) ${hr 2}$color
Down: $color${downspeed eth1} k/s ${alignr}Up: ${upspeed eth1} k/s
${downspeedgraph eth1 25,140 000000 ff0000} ${alignr}${upspeedgraph eth1 
25,140 000000 00ff00}$color
Total: ${totaldown eth1} ${alignr}Total: ${totalup eth1}
Inbound: ${tcp_portmon 1 32767 count} Outbound: ${tcp_portmon 32768 
61000 count}${alignr}Total: ${tcp_portmon 1 65535 count}

${color orange}CALENDAR ${hr 2}$color
${execi 600 less /home/nick/testdoc}

${color orange}TO DO ${hr 2}$color

${execi 300 python /home/nick/Stuff/Source/bin/t -nc ls}
```

---

### Post by SecondTwo on 2008-04-28
Why is it that despite what seemed like a fairly extensive Googling for the answer before I post, I discover the solution immediately afterwards?  Great job.

text_buffer_size 256

---

### Post by finer recliner on 2008-11-11
i cannot find the button to thank you...but thanks :)

---

