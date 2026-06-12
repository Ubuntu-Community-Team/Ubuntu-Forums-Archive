---
title: "Conky, shell, clock disappear after clicking on desktop"
date: 2008-06-22
forum: General Help
---

### Post by Dhaun on 2008-06-22
Hello,

I'm having issues with conky, shell and cairo clock.
They always disappear at the same time when I click on free space on my desktop. In order to have them back I have to kill these processes and start them again.

Any idea what's wrong?

Here's my .conkyrc -->
```

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type desktop
own_window_transparent yes
own_window_hints undecorated,below,skip_taskbar

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer yes
use_xft yes

# Update interval in seconds
update_interval 1.0

# Minimum size of text area
minimum_size 10 5

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
default_color 75B6D1
default_shade_color black
default_outline_color white

own_window_colour transparent
own_window_transparent yes

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 5
gap_y 200

# stuff after 'TEXT' will be formatted on screen



override_utf8_locale no
xftfont Monospace:size=9
xftalpha 0.9
TEXT
${offset 0}${color #ffffff}Date: 
${offset 0}${color #ffffff} ${time %a, } ${color }${time %e %B %G}

${offset 0}${color #ffffff}System Info: 
${offset 0}${color #ffffff} UpTime: ${color }$uptime
${offset 0}${color #ffffff} Kern:${color }$kernel

${offset 0}${color #ffffff}CPU INFO: 
 ${color}Intel C2D E6550
 ${offset 0}${color #ffffff} Speed:     ${color }${freq_dyn} Mhz
 ${color}Core 1:$color ${alignc} ${cpu cpu1}% ${color}${cpubar cpu1}
 ${color}Core 2:$color ${alignc} ${cpu cpu2}% ${color}${cpubar cpu2}
 ${cpugraph 000000 DFEC88}

${offset 0}${color #ffffff}Highest CPU:
${offset 0}${color } ${top name 1}${top_mem cpu 1}
${offset 0}${color } ${top name 2}${top cpu 2}

${offset 0}${color #ffffff}Highest MEM:
${offset 0}${color } ${top_mem name 1}${top_mem mem 1}
${offset 0}${color } ${top_mem name 2}${top_mem mem 2}

${offset 0}${color #ffffff}Memory and Storage:

${offset 0}${color #ffffff}MEM:
${offset 0}${color }$memperc% $mem/$memmax
${offset 0}${membar 3,150}
${offset 0}${color #ffffff}Ubutun:
${offset 0}${color }${fs_used /}/${fs_size /}
${offset 0}${fs_bar 3,150 /}
${offset 0}${color #ffffff}Win XP C:
${offset 0}${color }${fs_used /media/sda1}/${fs_size /media/sda1}
${offset 0}${fs_bar 3,150 /media/sda1}

${offset 0}${color #ffffff}Win XP E:
${offset 0}${color }${fs_used /media/disk}/${fs_size /media/disk}
${offset 0}${fs_bar 3,150 /media/disk}

${color #ffffff}NETWORK
 ${color #ffffff}Int: ${color}${addr eth0}
 ${color #ffffff}Ext: ${color}${execi 600  ruby -e "require 'net/http';Net::HTTP.get_print URI.parse('http://briancarper.net/cgi-bin/ip.cgi')"} 
${color #ffffff}Down: $color${downspeed eth0} k/s 
${downspeedgraph eth0 25,150 000000 00ff00}
${color #ffffff}UP:   $color${upspeed eth0} k/s 
${upspeedgraph eth0 25,150 000000 ff0000}$color
${color #ffffff}Total Down: $color${totaldown eth0} 
${color #ffffff}Total Up:   $color${totalup eth0}

```

---

### Post by vishzilla on 2008-06-22
change the value of ```
own_window_type override
```
Kill conky and start it again
and use_spacer should have values none or left or right

---

### Post by Dhaun on 2008-06-22
Great! Now they all seem to stay on their place. 

Thank you :popcorn:

---

