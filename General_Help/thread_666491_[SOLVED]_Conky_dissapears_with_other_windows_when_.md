---
title: "[SOLVED] Conky dissapears with other windows when I got to desktop?"
date: 2008-01-13
forum: General Help
---

### Post by Eax.exe on 2008-01-13
Hi :)

After a long fight with Conky I finally got it working :D
EXCEPT! When I in my lower left corner click on the button "Click here to hide all windows and show the desktop." It disappear to?
What do I have to in order for it NOT to disappear with the rest of my stuff?

Thanks in advance :D

My .conkyrc:

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
# -- Edited by Eax / 13/01/2008 - 19:10 --

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_hints undecorated,below,skip_taskbar
background yes

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer yes
use_xft yes

# Update interval in seconds
update_interval 3.0

# Minimum size of text area
minimum_size 160 5

# Maximum width
#maximum_width 160

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

# own_window_colour brown
own_window_transparent yes

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 0
gap_y 0

# stuff after 'TEXT' will be formatted on screen

override_utf8_locale no
xftfont Terminus:size=8
xftalpha 0.8

TEXT

$nodename $sysname
$kernel on $machine

**** KERNEFAMILIEN!

${color slate grey}${time %a, } ${color }${time %e %B %G}
${color slate grey}${time %Z,    }${color }${time %H:%M:%S}
${color slate grey}UpTime: ${color }$uptime
${color slate grey}Kern:${color }$kernel
${color slate grey}CPU:${color } $cpu% ${acpitemp}C
${cpugraph 20,130 000000 ffffff}
${color slate grey}Load: ${color }$loadavg
${color slate grey}Processes: ${color }$processes  
${color slate grey}Running:   ${color }$running_processes

${color slate grey}Highest CPU:
${color #ddaa00} ${top name 1}${top_mem cpu 1}
${color lightgrey} ${top name 2}${top cpu 2}
${color lightgrey} ${top name 3}${top cpu 3}
${color lightgrey} ${top name 4}${top cpu 4}

${color slate grey}Highest MEM:
${color #ddaa00} ${top_mem name 1}${top_mem mem 1}
${color lightgrey} ${top_mem name 2}${top_mem mem 2}
${color lightgrey} ${top_mem name 3}${top_mem mem 3}
${color lightgrey} ${top_mem name 4}${top_mem mem 4}

${color slate grey}MEM:  ${color } $memperc% $mem/$memmax
${membar 3,100}
${color slate grey}SWAP: ${color }$swapperc% $swap/$swapmax
${swapbar 3,100}

${color slate grey}ROOT:    ${color }${fs_free /}/${fs_size /}
${fs_bar 3,100 /}
${color slate grey}HOME:  ${color }${fs_free /home}/${fs_size /home}
${fs_bar 3,100 /home}
${color slate grey}NET: 
${color}Up: ${color }${upspeed wlan0} k/s
${upspeedgraph wlan0 20,130 000000 ffffff}
${color}Down: ${color }${downspeed wlan0}k/s${color}
${downspeedgraph wlan0 20,130 000000 ffffff}

```

---

### Post by kjbuente on 2008-01-13
Try setting background to no. This works for me and it does not do a vanishing act. I can post my file as well for you to look at if you want.

---

### Post by Eax.exe on 2008-01-13
Doesn't work :(

Would be great if you posted it :D

Thanks for the help :)

---

### Post by kjbuente on 2008-01-13
Well, never said I was perfect... :)

Here is my file so you can look off of it and see what is diff...

```
# Conky sample configuration
#
# the list of variables has been removed from this file in favour
# of keeping the documentation more maintainable.
# Check http://conky.sf.net for an up-to-date-list.

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
xftfont Bitstream Vera Sans Mono:size=8

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
#mail_spool $MAIL

# Update interval in seconds
update_interval 1.0

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
stippled_borders 8

# border margins
border_margin 4

# border width
border_width 1

# Default colors and also border colors
default_color white
default_shade_color black
default_outline_color black

#dexter_client no
#dexter_server no
#config file for libdexter (default search path: $HOME/.dexterrc; /etc/libdexter/dexter.conf)
#dexter_config

# Text alignment, other possible values are commented
#alignment top_left
#alignment top_right
#alignment bottom_left
alignment bottom_right
#alignment none

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 12
gap_y 12

# Subtract file system buffers from used memory?
no_buffers no

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
use_spacer no

# Allow each port monitor to track at most this many connections (if 0 or not set, default is 256)
#max_port_monitor_connections 0

# Maximum number of special things, e.g. fonts, offsets, aligns, etc.
#max_specials 512

# Maximum size of buffer for user text, i.e. below TEXT line.
#max_user_text 16384

# variable is given either in format $variable or in ${variable}. Latter
# allows characters right after the variable and must be used in network
# stuff because of an argument

# stuff after 'TEXT' will be formatted on screen

TEXT

NC8000 - $sysname $kernel on $machine
${color lightgrey}AC Power:$color $acpiacadapter
${color lightgrey}Battery 1 Status:$color ${battery C137}  ${battery_time C137}
${color lightgrey}Battery 2 Status:$color ${battery C136}  ${battery_time C136}
$stippled_hr
${color lightgrey}Uptime:$color $uptime ${color lightgrey}- Load:$color $loadavg
${color lightgrey}CPU Usage:${color #cc2222} $cpu% ${cpubar}
${color} ${cpugraph}
${color lightgrey}CPU Speed:$color $freq_dyn Mhz ${color lightgrey}CPU Temp:$color $acpitempf Degrees
${color lightgrey}Processes:$color $processes  ${color grey}Running:$color $running_processes
${color}Name              PID     CPU%   MEM%
${color #ddaa00} ${top name 1} ${top pid 1} ${top cpu 1} ${top mem 1}
${color lightgrey} ${top name 2} ${top pid 2} ${top cpu 2} ${top mem 2}
${color lightgrey} ${top name 3} ${top pid 3} ${top cpu 3} ${top mem 3}
${color lightgrey} ${top name 4} ${top pid 4} ${top cpu 4} ${top mem 4}
$color$stippled_hr
${color lightgrey}File Systems:
${color lightgrey} Root   $color${fs_free /}/${fs_size /}   ${fs_bar /}
${color lightgrey} Home   $color${fs_free /home}/${fs_size /home}   ${fs_bar /home}${if_mounted /media/disk}
${color lightgrey} MS    ${color} ${fs_free /media/disk}/${fs_size /media/disk}   ${fs_bar /media/disk}${endif}
${color lightgrey} RAM    $color $mem/$memmax    ${membar}
${color lightgrey} Swap  $color $swap/$swapmax    ${swapbar}
${color lightgrey}Disk Read-Write IO$color	          $diskio_read - $diskio_write
$stippled_hr
${color lightgrey}Wireless Mode: $color ${wireless_mode ath0}
${if_existing /sys/devices/pci0000:00/0000:00:1e.0/0000:02:04.0/net:ath0/operstate up}${color lightgrey}Wireless Rate:$color ${wireless_bitrate ath0} ${color lightgrey}Link Quality: $color ${wireless_link_qual_perc ath0}
${color lightgrey}IP Address:$color ${addr ath0} ${color lightgrey}Associated With:$color ${wireless_essid ath0}
 Down:${color #8844ee} ${downspeed ath0} k/s${color lightgrey} ${offset 80}Up:${color #22ccff} ${upspeed ath0} k/s
${color #000000}${downspeedgraph ath0 32,150 ffffff ffffff} ${color #000000}${upspeedgraph ath0 32,150 ffffff ffffff}${endif}
${if_existing /sys/devices/pci0000:00/0000:00:1e.0/0000:02:0e.0/net:eth0/operstate up}${color lightgrey}Wired IP Address: $color${addr eth0}
 Down:${color #8844ee} ${downspeed eth0} k/s${color lightgrey} ${offset 80}Up:${color #22ccff} ${upspeed eth0} k/s
${color #000000}${downspeedgraph eth0 32,150 ffffff ffffff} ${color #000000}${upspeedgraph eth0 32,150 ffffff ffffff}${endif}
```

Have fun!

---

### Post by Eax.exe on 2008-01-14
> **kjbuente said:**
> Well, never said I was perfect... :)

Here is my file so you can look off of it and see what is diff...

```
# Conky sample configuration
#
# the list of variables has been removed from this file in favour
# of keeping the documentation more maintainable.
# Check http://conky.sf.net for an up-to-date-list.

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
xftfont Bitstream Vera Sans Mono:size=8

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
#mail_spool $MAIL

# Update interval in seconds
update_interval 1.0

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
stippled_borders 8

# border margins
border_margin 4

# border width
border_width 1

# Default colors and also border colors
default_color white
default_shade_color black
default_outline_color black

#dexter_client no
#dexter_server no
#config file for libdexter (default search path: $HOME/.dexterrc; /etc/libdexter/dexter.conf)
#dexter_config

# Text alignment, other possible values are commented
#alignment top_left
#alignment top_right
#alignment bottom_left
alignment bottom_right
#alignment none

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 12
gap_y 12

# Subtract file system buffers from used memory?
no_buffers no

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
use_spacer no

# Allow each port monitor to track at most this many connections (if 0 or not set, default is 256)
#max_port_monitor_connections 0

# Maximum number of special things, e.g. fonts, offsets, aligns, etc.
#max_specials 512

# Maximum size of buffer for user text, i.e. below TEXT line.
#max_user_text 16384

# variable is given either in format $variable or in ${variable}. Latter
# allows characters right after the variable and must be used in network
# stuff because of an argument

# stuff after 'TEXT' will be formatted on screen

TEXT

NC8000 - $sysname $kernel on $machine
${color lightgrey}AC Power:$color $acpiacadapter
${color lightgrey}Battery 1 Status:$color ${battery C137}  ${battery_time C137}
${color lightgrey}Battery 2 Status:$color ${battery C136}  ${battery_time C136}
$stippled_hr
${color lightgrey}Uptime:$color $uptime ${color lightgrey}- Load:$color $loadavg
${color lightgrey}CPU Usage:${color #cc2222} $cpu% ${cpubar}
${color} ${cpugraph}
${color lightgrey}CPU Speed:$color $freq_dyn Mhz ${color lightgrey}CPU Temp:$color $acpitempf Degrees
${color lightgrey}Processes:$color $processes  ${color grey}Running:$color $running_processes
${color}Name              PID     CPU%   MEM%
${color #ddaa00} ${top name 1} ${top pid 1} ${top cpu 1} ${top mem 1}
${color lightgrey} ${top name 2} ${top pid 2} ${top cpu 2} ${top mem 2}
${color lightgrey} ${top name 3} ${top pid 3} ${top cpu 3} ${top mem 3}
${color lightgrey} ${top name 4} ${top pid 4} ${top cpu 4} ${top mem 4}
$color$stippled_hr
${color lightgrey}File Systems:
${color lightgrey} Root   $color${fs_free /}/${fs_size /}   ${fs_bar /}
${color lightgrey} Home   $color${fs_free /home}/${fs_size /home}   ${fs_bar /home}${if_mounted /media/disk}
${color lightgrey} MS    ${color} ${fs_free /media/disk}/${fs_size /media/disk}   ${fs_bar /media/disk}${endif}
${color lightgrey} RAM    $color $mem/$memmax    ${membar}
${color lightgrey} Swap  $color $swap/$swapmax    ${swapbar}
${color lightgrey}Disk Read-Write IO$color	          $diskio_read - $diskio_write
$stippled_hr
${color lightgrey}Wireless Mode: $color ${wireless_mode ath0}
${if_existing /sys/devices/pci0000:00/0000:00:1e.0/0000:02:04.0/net:ath0/operstate up}${color lightgrey}Wireless Rate:$color ${wireless_bitrate ath0} ${color lightgrey}Link Quality: $color ${wireless_link_qual_perc ath0}
${color lightgrey}IP Address:$color ${addr ath0} ${color lightgrey}Associated With:$color ${wireless_essid ath0}
 Down:${color #8844ee} ${downspeed ath0} k/s${color lightgrey} ${offset 80}Up:${color #22ccff} ${upspeed ath0} k/s
${color #000000}${downspeedgraph ath0 32,150 ffffff ffffff} ${color #000000}${upspeedgraph ath0 32,150 ffffff ffffff}${endif}
${if_existing /sys/devices/pci0000:00/0000:00:1e.0/0000:02:0e.0/net:eth0/operstate up}${color lightgrey}Wired IP Address: $color${addr eth0}
 Down:${color #8844ee} ${downspeed eth0} k/s${color lightgrey} ${offset 80}Up:${color #22ccff} ${upspeed eth0} k/s
${color #000000}${downspeedgraph eth0 32,150 ffffff ffffff} ${color #000000}${upspeedgraph eth0 32,150 ffffff ffffff}${endif}
```

Have fun!

Great, thanks a lot :)
After a bit of working with your .conkyrc and mine it got it working using this code:
```

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_hints undecorated,below,skip_taskbar,skip_pager

# If own_window is yes, you may use type normal, desktop or override
own_window_type override

# Use pseudo transparency with own_window?
own_window_transparent yes

```

Thanks a lot for your help :)

---

