---
title: "[SOLVED] Conky doesn't obey update interval setting in .conkyrc"
date: 2008-06-17
forum: General Help
---

### Post by plamen_todoroff on 2008-06-17
Title says pretty much all. Conky is updating as it wishes, sometimes the update interval is 10 seconds, sometimes 20 seconds, and rarely 2.0 seconds as configured in .conkyrc. It changes all the time while conky is runing.

What could be the reason?

I don't know if the following is somehow connected to the problem but conky starts as a black thick line when I boot my Ubuntu 8.04, and after about 10 seconds it becomes what it should be. I hope you understand me...

---

### Post by easybake on 2008-06-17
Post your conkyrc

---

### Post by plamen_todoroff on 2008-06-17
# Conky sample configuration
#
# the list of variables has been removed from this file in favour
# of keeping the documentation more maintainable.
# Check [http://conky.sf.net](http://conky.sf.net) for an up-to-date-list.

# set to yes if you want Conky to be forked in the background
background no

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

# Xft font when Xft is enabled
#xftfont Bitstream Vera Sans Mono:size=8:style=bold
xftfont Devroye:size=6:style=normal

# Text alpha when using Xft
xftalpha 0.8

# Print everything to stdout?
# out_to_console no

# MPD host/port
# mpd_host localhost
# mpd_port 6600
# mpd_password tinker_bell

# Print everything to console?
# out_to_console no

# mail spool
mail_spool $MAIL

# Update interval in seconds
update_interval 2.0

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window yes

# If own_window is yes, you may use type normal, desktop or override
own_window_type override

# Use pseudo transparency with own_window?
own_window_transparent yes

# If own_window_transparent is set to no, you can set the background colour here
own_window_colour black

# If own_window is yes, these window manager hints may be used
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

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

# Draw borders around graphs
draw_graph_borders yes

# Stippled borders?
stippled_borders 2

# border margins
border_margin 4

# border width
border_width 1

# Default colors and also border colors
default_color white
default_shade_color white
default_outline_color white

dexter_client no
dexter_server no
# config file for libdexter (default search path: $HOME/.dexterrc; /etc/libdexter/dexter.conf)
dexter_config

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right
#alignment none

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 32
gap_y 76
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

# Force UTF8? Note that UTF8 support requires XFT.
override_utf8_locale no

# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer yes

# Allow each port monitor to track at most this many connections (if 0 or not set, default is 256)
#max_port_monitor_connections 256

# Maximum number of special things, e.g. fonts, offsets, aligns, etc.
#max_specials 512

# Maximum size of buffer for user text, i.e. below TEXT line.
#max_user_text 16384

# variable is given either in format $variable or in ${variable}. Latter
# allows characters right after the variable and must be used in network
# stuff because of an argument

# stuff after 'TEXT' will be formatted on screen...
#MY STUFF!
# ${diskiograph_read /dev/sda 14,180} ${alignc} ${diskiograph_write /dev/sda 14,180to}
#end of MY STUFF!

TEXT
 $nodename: $sysname $kernel on $machine
$stippled_hr
${color} SYSTEM UPTIME:${color} $uptime ${color} ${alignr} SYSTEM LOAD:${color} $loadavg
  ${color} CPU1 USAGE: ${color} ${cpu cpu1}% ${color} ${cpubar cpu1}
  ${color} CPU2 USAGE: ${color} ${cpu cpu2}% ${color} ${cpubar cpu2}
${color} ${cpugraph cpu1 24,260}          CPU1@${freq_g 1}GHz
${color} ${cpugraph cpu2 24,260}          CPU2@${freq_g 2}GHz
${color} RAM USAGE:${color} $mem/$memmax $memperc% ${membar}
${color} SWAP USAGE:${color} $swap/$swapmax $swapperc% ${swapbar}
${color} PROCESSES:${color} $processes ${color} ${alignr} ${color} RUNNING:${color} $running_processes ${color}
$stippled_hr
${color} NETWORKING:
   DOWNLOAD_ETH0: ${color} ${downspeedf eth0}  kb/s ${color} ${alignr} UPLOAD_ETH0: ${color} ${upspeedf eth0} kb/s ${color}
${color} ${downspeedgraph eth0 24,190} ${alignc} ${color} ${upspeedgraph eth0 24,170}
   DOWNLOAD_WLAN0: ${color} ${downspeedf wlan0} kb/s ${color} ${alignr} UPLOAD_WLAN0: ${color} ${upspeedf wlan0} kb/s ${color}
${color} ${downspeedgraph wlan0 24,190} ${alignc} ${color} ${upspeedgraph wlan0 24,170}
   TOTAL DOWN: ${totaldown eth0} ${alignr} TOTAL UP: ${totalup eth0}
$stippled_hr
${color} FILE SYSTEMS:
   /root $color ${fs_used /}FREE: ${fs_free /} ${fs_bar /}
   /home $color ${fs_used /home}FREE: ${fs_free /home} ${fs_bar /home}
 HDD READ: ${diskio_read /dev/sda} ${alignr} HDD WRITE: ${diskio_write /dev/sda}
$stippled_hr
${alignr}  PID        TIME        CPU%        MEM%
${color} TOP CPU EATERS
   ${color} ${top name 1} ${alignr} ${top pid 1}        ${top time 1}        ${top cpu 1}        ${top mem 1}
   ${color} ${top name 2} ${alignr} ${top pid 2}        ${top time 2}        ${top cpu 2}        ${top mem 2}
   ${color} ${top name 3} ${alignr} ${top pid 3}        ${top time 3}        ${top cpu 3}        ${top mem 3}
   ${color} ${top name 4} ${alignr} ${top pid 4}        ${top time 4}        ${top cpu 4}        ${top mem 4}
${color} TOP MEMORY EATERS
   ${color} ${top_mem name 1} ${alignr} ${top_mem pid 1}        ${top_mem time 1}        ${top_mem cpu 1}        ${top_mem mem 1}
   ${color} ${top_mem name 2} ${alignr} ${top_mem pid 2}        ${top_mem time 2}        ${top_mem cpu 2}        ${top_mem mem 2}
   ${color} ${top_mem name 3} ${alignr} ${top_mem pid 3}        ${top_mem time 3}        ${top_mem cpu 3}        ${top_mem mem 3}
   ${color} ${top_mem name 4} ${alignr} ${top_mem pid 4}        ${top_mem time 4}        ${top_mem cpu 4}        ${top_mem mem 4}
$stippled_hr
${color} CONNECTION(s) ${alignr} PORT(s)
${color} OUTBOUND: ${tcp_portmon 32768 61000 count}    INBOUND: ${tcp_portmon 1 32767 count} ${alignr} ALL: ${tcp_portmon 1 65535 count}
${color} OUTBOUND CONNECTION ${alignr} REMOTE SERVICE/PORT ${color}
   ${tcp_portmon 32768 61000 rhost 0} ${alignr} ${tcp_portmon 32768 61000 rservice 0}
   ${tcp_portmon 32768 61000 rhost 1} ${alignr} ${tcp_portmon 32768 61000 rservice 1}
   ${tcp_portmon 32768 61000 rhost 2} ${alignr} ${tcp_portmon 32768 61000 rservice 2}
   ${tcp_portmon 32768 61000 rhost 3} ${alignr} ${tcp_portmon 32768 61000 rservice 3}
${color} INBOUND CONNECTION ${alignr} LOCAL SERVICE/PORT ${color}
   ${tcp_portmon 1 32767 rhost 0} ${alignr} ${tcp_portmon 1 32767 lservice 0}
   ${tcp_portmon 1 32767 rhost 1} ${alignr} ${tcp_portmon 1 32767 lservice 1}
   ${tcp_portmon 1 32767 rhost 2} ${alignr} ${tcp_portmon 1 32767 lservice 2}
   ${tcp_portmon 1 32767 rhost 3} ${alignr} ${tcp_portmon 1 32767 lservice 3}

---

### Post by easybake on 2008-06-17
I checked your rc and the portmons are really killing your update times. You could simply launch 2 conkys at once. One just for port monitoring and the other for everything else.

Edit: If you don't know how to do that read this [here]("http://ubuntuforums.org/showthread.php?p=4041023&highlight=launch+multiple+conkys#post4041023")

But I've only had luck getting that to work by creating mulitiple conkystart files.

---

### Post by plamen_todoroff on 2008-06-17
I've been using this .conkyrc since Gutsy and the problem occured about a month ago, it was working pretty well right after i installed Hardy, but after sometime the problem occured. The portmons have never been a problem before, the only thing that (I guess) could be connected to the problem is that I changed the fonts sometimes. Could this really be it?

---

### Post by easybake on 2008-06-17
I don't think its the fonts. Using your rc on my system the pormon really slowed down the updates. a simple way to test for yourself of whats effecting your update times is to add a time monitor to your rc ```
${time %I:%M%S}
```

If you use all of your rc but remove the portmon section, it can easily update every second. 

If you remove all of your rc but leave the portmon section, i could only get updates every 5 seconds.

---

### Post by plamen_todoroff on 2008-06-17
Thank you for staying with me on this, but I guess now it's up to me to decide whether to keep my .conkyrc as it is and have this update problem, I really like my portmon section of it :).

---

