---
title: "conky shows up every second login"
date: 2007-02-20
forum: General Help
---

### Post by seshomaru samma on 2007-02-20
here is a strange problem 
i installed conky following the instructions[ here]("http://ubuntuforums.org/showthread.php?t=205865&highlight=conky")
i added it to my session start-up programmes but it never showed up
i gave up on it ,but lately i changed my theme (from linsta to drak-grey) and it started showing up ,except it only shows up every second login . i log out it's gone.log out again it's back. i reverted back to my old theme (linsta) and sure enough it didn't come up. 
i guess it's theme related , but is there a fix for it?
here is my conkyrc:
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
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer yes
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
gap_y 10

# stuff after 'TEXT' will be formatted on screen

TEXT
$color
${color orange}SYSTEM ${hr 2}$color
$nodename $sysname $kernel on $machine

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

Root:  ${fs_free_perc /}%   ${fs_bar 6 /}$color 
hda1:  ${fs_free_perc /media/hda1}%   ${fs_bar 6 /media/hda1}$color
hdb3:  ${fs_free_perc /media/hdb3}%   ${fs_bar 6 /media/hdb3}

${color orange}NETWORK (${addr eth0}) ${hr 2}$color
Down: $color${downspeed eth0} k/s ${alignr}Up: ${upspeed eth0} k/s
${downspeedgraph eth0 25,140 000000 ff0000} ${alignr}${upspeedgraph eth0 
25,140 000000 00ff00}$color
Total: ${totaldown eth0} ${alignr}Total: ${totalup eth0}
Inbound: ${tcp_portmon 1 32767 count} Outbound: ${tcp_portmon 32768 
61000 count}${alignr}Total: ${tcp_portmon 1 65535 count}

${color orange}LOGGING ${hr 2}$color
${execi 30 tail -n3 /var/log/messages | fold -w50}

${color orange}FORTUNE ${hr 2}$color
${execi 120 fortune -s | fold -w50}
```

---

### Post by kerry_s on 2007-02-20
In some de/wm you have to launch conky after they finished loading. So just add a sleep line to it. Change your startup like this->

sleep 5 && conky

adjust the time accordingly, 5 means it waits 5 seconds to start.

---

### Post by seshomaru samma on 2007-02-21
Thanks but with the sleep command ,it doesn't come up at all!
The thing is that it's only in gnome sessions, in XFCE conky always shows. 
:confused: :confused: :confused:

---

### Post by kerry_s on 2007-02-21
Did you adjust the time?
Also i noticed your .conkyrc is incomplete, your missing the choose of font size,among other things.-> [http://conky.sourceforge.net/](http://conky.sourceforge.net/)

Here's what mine looks like->

```
# Conky sample configuration
#
# the list of variables has been removed from this file in favour
# of keeping the documentation more maintainable.
# Check http://conky.sf.net for an up-to-date-list.

# set to yes if you want Conky to be forked in the background
background true

# X font when Xft is disabled, you can pick one with program xfontsel
#font 5x7
#font 6x10
#font 7x13
#font 8x13
font 9x15
#font *mintsmild.se*
#font -*-*-*-*-*-*-34-*-*-*-*-*-*-*


# Use Xft?
use_xft yes

# Set conky on the bottom of all other applications
own_window_hints below

# Xft font when Xft is enabled
xftfont Sans-Serif:size=10

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
update_interval 3.0

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window true
#own_window_type override
own_window_type desktop

# Use pseudo transparency with own_window?
own_window_transparent true

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
border_margin 10

# border width
border_width 10

# Default colors and also border colors
default_color white
default_shade_color black
default_outline_color black

# Text alignment, other possible values are commented
alignment top_left
#alignment top_right
#alignment bottom_left
#alignment bottom_right
#alignment none

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 800
gap_y 50

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
${color white}              ${time %l:%M %a %b %d}
${hr}
${execi 300 fortune -a | fold -w50}
${hr}
CPU: ${freq_g}GHz / Clocked: ${freq_dyn}MHz / Temp: ${acpitemp}C 
Disk I/O:${diskio}    Uptime:$uptime 
Processes:$processes  Running:$running_processes
CPU Usage:$cpu% ${cpugraph  20, 125 ffffff 0000ff}

RAM Usage:$mem of $memmax - $memperc% 
Swap Usage:$swap of $swapmax - $swapperc% 
File systems: ${fs_used /} of ${fs_size /}

Name                     PID     CPU%   MEM%
${top name 1}         ${top pid 1} ${top cpu 1} ${top mem 1}
${top name 2}         ${top pid 2} ${top cpu 2} ${top mem 2}
${top name 3}         ${top pid 3} ${top cpu 3} ${top mem 3}
${top name 4}         ${top pid 4} ${top cpu 4} ${top mem 4}
${top name 5}         ${top pid 5} ${top cpu 5} ${top mem 5}

   IN:${downspeed eth0} k/s          OUT:${upspeed eth0} k/s 
${downspeedgraph eth0 20,125 ff0000 0000ff} ${upspeedgraph eth0 20,125 0000ff ff0000}

Connections: ${tcp_portmon 1 65535 count}
Netstat 
${execi 2 netstat -e -p -t | grep ESTABLISHED | cut -c45-68,80-86,102-140}


```

---

### Post by seshomaru samma on 2007-02-21
Thanks , it was a problem with the conkyrc 
now everything is cool...
:guitar:

---

