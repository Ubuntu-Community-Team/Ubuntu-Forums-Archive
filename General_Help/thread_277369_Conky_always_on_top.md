---
title: "Conky always on top"
date: 2006-10-14
forum: General Help
---

### Post by m.musashi on 2006-10-14
I have conky more or less running okay along with beryl and xgl. However, it is always on top. Any app that is full screen or moved into the same space as conky will be under it. As much as I like conky, how do I get it to not stay on top? Here is my conky config:
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

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
own_window_transparent 1
own_window_hints undecorated,below,skip_taskbar
#background yes

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer yes
use_xft no

# Update interval in seconds
update_interval 3.0

# Minimum size of text area
minimum_size 400 5

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
default_color white

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
# replace below at bottow to include system log details
##SYSTEM LOG TAIL
##${execi 30 tail -n3 /var/log/messages | fold -w67}
##$color$stippled_hr
##${execi 120 fortune -s | fold -w67}
##${execi 15 wmctrl -R " - conky"}

TEXT
$nodename $sysname $kernel on $machine
$color$stippled_hr
CPU: ${freq}MHz   Load: ${loadavg}   Temp: ${acpitemp}
$cpubar
${cpugraph ff0000 ffffff}

NAME             PID       CPU%      MEM%
${top name 1} ${top pid 1}   ${top cpu 1}    ${top mem 1}
${top name 2} ${top pid 2}   ${top cpu 2}    ${top mem 2}
${top name 3} ${top pid 3}   ${top cpu 3}    ${top mem 3}
${top name 4} ${top pid 4}   ${top cpu 4}    ${top mem 4}
$color$stippled_hr
RAM:        $memperc%       ${membar 6}$color
Swap:       $swapperc%       ${swapbar 6}$color

Root:       ${fs_free_perc /}%        ${fs_bar 6 /}$color 
sda5:       ${fs_free_perc /dev/sda5}%        ${fs_bar 5 /dev/sda6}$color 
$color$stippled_hr
Internet/Networking Status (${addr eth1}):
Down: $color${downspeed eth1} k/s ${alignr}Up: ${upspeed eth1} k/s
${downspeedgraph eth1 25,190 ffffff ff0000} ${alignr}${upspeedgraph eth0 25,190 ffffff 00ff00}$color
Total: ${totaldown eth1} ${alignr}Total: ${totalup eth1}
Inbound: ${tcp_portmon 1 32767 count} Outbound: ${tcp_portmon 32768 61000 count}${alignr}Total: ${tcp_portmon 1 65535 count}
$color$stippled_hr
```

---

### Post by kerry_s on 2006-10-14
On mine i have " own_window_hints below " Here's my conkyrc->

```
# Conky sample configuration
#
# the list of variables has been removed from this file in favour
# of keeping the documentation more maintainable.
# Check http://conky.sf.net for an up-to-date-list.

# set to yes if you want Conky to be forked in the background
background yes

# X font when Xft is disabled, you can pick one with program xfontsel
#font 5x7
#font 6x10
#font 7x13
#font 8x13
#font 9x15
#font *mintsmild.se*
#font -*-*-*-*-*-*-34-*-*-*-*-*-*-*


# Use Xft?
use_xft yes

# Set conky on the bottom of all other applications
own_window_hints below

# Xft font when Xft is enabled
xftfont Sans:style=Bold:size=10

# Text alpha when using Xft
xftalpha 1

# Print everything to stdout?
# out_to_console no

# MPD host/port
# mpd_host localhost
# mpd_port 6600
# mpd_password tinker_bell

# Print everything to console?
# out_to_console no

# mail spool
#mail_spool $MAIL

# Update interval in seconds
update_interval 5

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_hints undecorated,below,skip_taskbar
own_window_type override

# Use pseudo transparency with own_window?
own_window_transparent yes

# If own_window_transparent is set to no, you can set the background colour here
#own_window_colour hotpink

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 280 5

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Stippled borders?
stippled_borders 8

# border margins
border_margin 5

# border width
border_width 10

# Default colors and also border colors
default_color white
default_shade_color black
default_outline_color black

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right
#alignment none

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 50
gap_y 12

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# number of cpu samples to average
# set to 1 to disable averaging
cpu_avg_samples 1

# number of net samples to average
# set to 1 to disable averaging
net_avg_samples 1

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale no


# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer yes

#   mldonkey_hostname     Hostname for mldonkey stuff, defaults to localhost
#   mldonkey_port         Mldonkey port, 4001 default
#   mldonkey_login        Mldonkey login, default none
#   mldonkey_password     Mldonkey password, default none

# boinc (seti) dir
# seti_dir /opt/seti

# Allow for the creation of at least this number of port monitors (if 0 or not set, default is 16) 
min_port_monitors 16

# Allow each port monitor to track at least this many connections (if 0 or not set, default is 256)
min_port_monitor_connections 256

# variable is given either in format $variable or in ${variable}. Latter
# allows characters right after the variable and must be used in network
# stuff because of an argument

# stuff after 'TEXT' will be formatted on screen

TEXT
 ${color white}           ${time %l:%M %a %b %d}
${color white}CPU:${color white} ${freq} ${color white}mhz / Temp:${color white}$acpitemp ${color white}C 
${color white}Disk I/O:${color white} ${diskio}    ${color white}Uptime:${color white} $uptime 
${color white}Processes:${color white} $processes  ${color white}Running:${color white} $running_processes
${color white}CPU Usage:${color white} $cpu% ${color white}${cpugraph  20, 125 ffffff 0000ff}

${color white}RAM Usage:${color white} $mem of $memmax ${color white}- ${color white}$memperc% 
${color white}Swap Usage:${color white} $swap of $swapmax ${color white}- ${color white}$swapperc% 
${color white}File systems: ${color white}${fs_used /} of ${fs_size /}

${color white}Name                     PID     CPU%   MEM%
${color white} ${top name 1}         ${top pid 1} ${top cpu 1} ${top mem 1}
${color white} ${top name 2}         ${top pid 2} ${top cpu 2} ${top mem 2}
${color white} ${top name 3}         ${top pid 3} ${top cpu 3} ${top mem 3}
${color white} ${top name 4}         ${top pid 4} ${top cpu 4} ${top mem 4}
${color white} ${top name 5}         ${top pid 5} ${top cpu 5} ${top mem 5}

${color white}IN:${downspeed eth0} k/s ${color white}${downspeedgraph eth0 20,125 ff0000 0000ff}
${color white}OUT:${upspeed eth0} k/s ${color white}${upspeedgraph eth0 20,125 0000ff ff0000}

${color white}Netstat
${color white}${execi 1 netstat -e -p -t | grep ESTABLISHED | cut -c45-68,80-86,102-140}

```

---

### Post by m.musashi on 2006-10-14
Thanks, that seemed to fix the problem. However, now I have a new problem - conky won't load on start up. I'm assuming one of the "own_window" options I removed might have had something to do with that. I'll play around a see. In the meantime, I can just launch it manually.

Thanks again.

---

### Post by kerry_s on 2006-10-14
Are you sure it's just not being covered by your background? I use sleep 5 to give the desktop a chance to load first. I just make a script and make it executable and point the startup to the script.You can adjust the time to how long your desktop takes to load.

#!/bin/sh

sleep 5
conky &

then just point put it in the startup
/home/(you)/.start-conky(or what ever you name it)

---

### Post by m.musashi on 2006-10-14
> **kerry_s said:**
> Are you sure it's just not being covered by your background? I use sleep 5 to give the desktop a chance to load first. I just make a script and make it executable and point the startup to the script.You can adjust the time to how long your desktop takes to load.

#!/bin/sh

sleep 5
conky &

then just point put it in the startup
/home/(you)/.start-conky(or what ever you name it)
I'm not sure if that was the problem but the script you gave me seems to work fine and solve the problem. In the sessions -> startup programs I added "sh .start-conky" without the quotes and seems to work fine. Is that the right way to start the script?

Thanks again.

I don't suppose you would know how to get conky to show both cpu cores on a core duo processor? I tried adding another line for CPU but it only shows the same data (i.e. the data for cpu0 twice).

---

### Post by kerry_s on 2006-10-14
>  I added "sh .start-conky" without the quotes and seems to work fine. Is that the right way to start the script?
 


I usally put the full path, but if it works for ya it should be fine.

> I don't suppose you would know how to get conky to show both cpu cores on a core duo processor? I tried adding another line for CPU but it only shows the same data (i.e. the data for cpu0 twice).

I haven't got a clue, "google" is your friend ;) 
Sorry i can't be of more help.

---

### Post by -=Ghostlike=- on 2006-11-04
you can get more info on your core's with ${cpu cpu1}= core 1 and cpu2 = core 2.

I keep having the on top problem, even when I did do the startup script and I have hints_below enabled.

Any more info about how to solve this? (I have got Edgy with fglrx, Beryl 0.1.1 and Conky 1.0RC2)

---

