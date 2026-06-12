---
title: "Conky absolute vertical alignment + exec"
date: 2014-09-25
forum: General Help
---

### Post by Drake.Tempestos on 2014-09-25
Errrrr... So guys. I'm trying to create a conf for Conky to see my week appointments using the fewest possible resources.

Basically multiple ${execpi rem -g} with ${goto} for column alignment, but as you can see from the image it generates a "staircase effect"...

I tried using ${voffset -x} for each rem, but as the rem output varies in number of rows it ends up being useless.

My question is... Is there an absolute vertical alignment similar to ${goto} in Conky?

Ah, here is my conf

```
# Color Picker
default_color 111111
default_shade_color 000000
default_outline_color 111111
own_window_colour 262524

# Minimum size of text area
minimum_size 830 350
# maximum_width 200

background yes

# Use Xft?
use_xft yes
xftfont PF Tempesta Seven Condensed:size=6
xftalpha 1

# Update interval in seconds
update_interval 1.0

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_class Background
own_window_argb_visual no
own_window_transparent no
own_window_type normal

own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Draw shades or outline?
draw_shades no
draw_outline no

# Borders
draw_borders yes
border_width 2
# border_margin 0
# border_outer_margin 1
border_inner_margin 15

# Bars
draw_graph_borders yes

# Text alignment, other possible values are commented
alignment middle_left

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 80
gap_y 0

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# number of cpu samples to average
# set to 1 to disable averaging
cpu_avg_samples 2

# number of net samples to average
# set to 1 to disable averaging
net_avg_samples 2

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale yes

# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer left

TEXT
${color EEE}${font PF Arma Five-6}${time %A, %d de %B}    ${goto 160}${execi 600 echo $(date +%A -d "+1 days")}, ${execi 600 echo $(date +%d -d "+1 days")} de ${execi 600 echo $(date +%B -d "+1 days")}    ${goto 300}${execi 600 echo $(date +%A -d "+2 days")}, ${execi 600 echo $(date +%d -d "+2 days")} de ${execi 600 echo $(date +%B -d "+2 days")}    ${goto 440}${execi 600 echo $(date +%A -d "+3 days")}, ${execi 600 echo $(date +%d -d "+3 days")} de ${execi 600 echo $(date +%B -d "+3 days")}    ${goto 580}${execi 600 echo $(date +%A -d "+4 days")}, ${execi 600 echo $(date +%d -d "+4 days")} de ${execi 600 echo $(date +%B -d "+4 days")}    ${goto 720}${execi 600 echo $(date +%A -d "+5 days")}, ${execi 600 echo $(date +%d -d "+5 days")} de ${execi 600 echo $(date +%B -d "+5 days")}${font}
${stippled_hr}

${execi 600 rem -g | sed -e '1d;2d'}
${execpi 600 rem -g $(date +%Y/%m/%d -d "+1 days") | sed 's/^/${goto 160} /' | sed -e '1d;2d'}
${execpi 600 rem -g $(date +%Y/%m/%d -d "+2 days") | sed 's/^/${goto 300} /' | sed -e '1d;2d'}
${execpi 600 rem -g $(date +%Y/%m/%d -d "+3 days") | sed 's/^/${goto 440} /' | sed -e '1d;2d'}
${execpi 600 rem -g $(date +%Y/%m/%d -d "+4 days") | sed 's/^/${goto 580} /' | sed -e '1d;2d'}
${execpi 600 rem -g $(date +%Y/%m/%d -d "+5 days") | sed 's/^/${goto 720} /' | sed -e '1d;2d'}
```

---

### Post by Drake.Tempestos on 2014-09-25
Bump

No one? :(

---

