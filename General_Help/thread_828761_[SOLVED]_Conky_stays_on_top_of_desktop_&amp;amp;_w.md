---
title: "[SOLVED] Conky stays on top of desktop &amp;amp; windows"
date: 2008-06-14
forum: General Help
---

### Post by laffinet on 2008-06-14
Hi !

I can't get my conky to stay on the bottom of other applications.

When I boot up my conky stays on top of all applications and also shows a border (which is actually too big)

If I then kill conky and restart from terminal everything is fine and I get a beautiful conky the way I want it and it stays on the bottom of everything else plus it doesn't have a border

Help !

Here's my .conkyrc

```
# UBUNTU-CONKY
# A comprehensive conky script, configured for use on
# Ubuntu / Debian Gnome, without the need for any external scripts.
#
# Based on conky-jc and the default .conkyrc.
# INCLUDES:
# - tail of /var/log/messages 
# - netstat connections to your computer
#
# -- Pengo (conky@pengo.us)
#

# set to yes if you want Conky to be forked in the background
background yes

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer yes
use_xft yes

# Update interval in seconds
update_interval 3.0

# Minimum size of text area
minimum_size 400 5

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

own_window_colour brown
own_window_transparent yes

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 10
gap_y 10

# stuff after 'TEXT' will be formatted on screen

override_utf8_locale no
xftfont Terminus:size=8
xftalpha 0.8

TEXT

${offset 240}${color slate grey}${time %a, } ${color }${time %e %B %G}
${offset 240}${color slate grey}${time %Z,    }${color }${time %H:%M:%S}
${offset 240}${color slate grey}UpTime: ${color }$uptime
${offset 240}${color slate grey}Kern:${color }$kernel
${offset 240}${color slate grey}Batt:${color }${battery}
${offset 240}${color slate grey}Batt:${color }${battery_time}
${offset 240}${color slate grey}CPU:${color } $cpu% ${acpitemp}C
${offset 240}${cpugraph 20,130 000000 ffffff}
${offset 240}${color slate grey}Load: ${color }$loadavg
${offset 240}${color slate grey}Processes: ${color }$processes  
${offset 240}${color slate grey}Running:   ${color }$running_processes

${offset 240}${color slate grey}Highest CPU:
${offset 240}${color #ddaa00} ${top name 1}${top_mem cpu 1}
${offset 240}${color lightgrey} ${top name 2}${top cpu 2}
${offset 240}${color lightgrey} ${top name 3}${top cpu 3}
${offset 240}${color lightgrey} ${top name 4}${top cpu 4}

${offset 240}${color slate grey}Highest MEM:
${offset 240}${color #ddaa00} ${top_mem name 1}${top_mem mem 1}
${offset 240}${color lightgrey} ${top_mem name 2}${top_mem mem 2}
${offset 240}${color lightgrey} ${top_mem name 3}${top_mem mem 3}
${offset 240}${color lightgrey} ${top_mem name 4}${top_mem mem 4}

${offset 240}${color slate grey}MEM:  ${color } $memperc% $mem/$memmax
${offset 240}${membar 3,100}
${offset 240}${color slate grey}SWAP: ${color }$swapperc% $swap/$swapmax
${offset 240}${swapbar 3,100}

${offset 240}${color slate grey}ROOT:    ${color }${fs_free /}/${fs_size /}
${offset 240}${fs_bar 3,100 /}
${offset 240}${color slate grey}HOME:  ${color }${fs_free /home}/${fs_size /home}
${offset 240}${fs_bar 3,100 /home}
${offset 240}${color slate grey}SLACK:  ${color }${fs_free /mnt/slack}/${fs_size /mnt/slack}
${offset 240}${fs_bar 3,100 /mnt/slack}
${offset 240}${color slate grey}NET: 
${offset 240}${color}Up: ${color }${upspeed wlan0} k/s
${offset 240}${upspeedgraph wlan0 20,130 000000 ffffff}
${offset 240}${color}Down: ${color }${downspeed wlan0}k/s${color}
${offset 240}${downspeedgraph wlan0 20,130 000000 ffffff}
```

---

### Post by easybake on 2008-06-14
You probably need to add a sleep command to start up conky. Do this:

in terminal
```
gedit .conky_start.sh
```

add this to the text editor.
```
#!/bin/bash
sleep 20 && conky;
```

save it.

In terminal
```
sudo chmod a+x .conky_start.sh
```

Go into System>Preferences>Sessions and add the command. But replace with your USERNAME.
```
/home/USERNAME/.conky_start.sh
```

Remove any other conky from the Sessions menu.

---

### Post by easybake on 2008-06-14
I noticed you had a lot of offsets in your conkyrc. You can fix that by having a single maximum_width value above the TEXT. You can also use $alignr and $alignc to keep things in line. I was bored so I took the liberty to change up your conky to give you an example. Try it out.

```
# UBUNTU-CONKY
# A comprehensive conky script, configured for use on
# Ubuntu / Debian Gnome, without the need for any external scripts.
#
# Based on conky-jc and the default .conkyrc.
# INCLUDES:
# - tail of /var/log/messages 
# - netstat connections to your computer
#
# -- Pengo (conky@pengo.us)
#

# set to yes if you want Conky to be forked in the background
background yes

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer yes
use_xft yes

# Update interval in seconds
update_interval 3.0

# Minimum size of text area
minimum_size 400 5
maximum_width 170
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

own_window_colour brown
own_window_transparent yes

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 10
gap_y 10

# stuff after 'TEXT' will be formatted on screen

override_utf8_locale no
xftfont Terminus:size=8
xftalpha 0.8

TEXT

${color slate grey}${time %a,}$alignc${color }${time %e %B %G}
${color slate grey}${time %Z,} $alignc${color }${time %H:%M:%S}
${color slate grey}UpTime: $alignc${color }$uptime
${color slate grey}Kern:$alignc${color }$kernel
${color slate grey}Batt: $alignc${color }${battery}
${color slate grey}Batt: $alignc${color }${battery_time}
${color slate grey}CPU: $alignc${color } $cpu% ${acpitemp}C
${cpugraph 20,170 000000 ffffff}
${color slate grey}Load:$alignc${color }$loadavg
${color slate grey}Processes:$alignc${color }$processes  
${color slate grey}Running:$alignc${color }$running_processes

${color slate grey}Highest CPU:
${color #ddaa00} ${top name 1}$alignr${top_mem cpu 1}
${color lightgrey} ${top name 2}$alignr${top cpu 2}
${color lightgrey} ${top name 3}$alignr${top cpu 3}
${color lightgrey} ${top name 4}$alignr${top cpu 4}

${color slate grey}Highest MEM:
${color #ddaa00} ${top_mem name 1}$alignr${top_mem mem 1}
${color lightgrey} ${top_mem name 2}$alignr${top_mem mem 2}
${color lightgrey} ${top_mem name 3}$alignr${top_mem mem 3}
${color lightgrey} ${top_mem name 4}$alignr${top_mem mem 4}

${color slate grey}MEM: ${color }$memperc%$alignr$mem/$memmax
${membar 3,170}
${color slate grey}SWAP: ${color }$swapperc%$alignr$swap/$swapmax
${swapbar 3,170}

${color slate grey}ROOT:$alignr${color }${fs_free /}/${fs_size /}
${fs_bar 3,170 /}
${color slate grey}HOME:$alignr${color }${fs_free /home}/${fs_size /home}
${fs_bar 3,170 /home}
${color slate grey}SLACK: ${color }${fs_free /mnt/slack}/${fs_size /mnt/slack}
${fs_bar 3,170 /mnt/slack}
${color slate grey}NET: 
${color}Up: ${color }${upspeed wlan0} k/s
${upspeedgraph wlan0 20,170 000000 ffffff}
${color}Down: ${color }${downspeed wlan0}k/s${color}
${downspeedgraph wlan0 20,170 000000 ffffff}
```

---

### Post by laffinet on 2008-06-14
Thank you ! Worked like a charm. I had used a start up script before but only set the the delay to 5 or 8 sec, so I guess it wasn't enough to make sure conky starts last. Your 20 sec seem to do the trick.

---

