---
title: "how to display total number of connections by port in Conky"
date: 2008-04-27
forum: General Help
---

### Post by munkyeetr on 2008-04-27
What I want my conky display to show is this:

Connections:
http: 3
ftp: 0
ssh: 1
pop3: 1
torrent: 12

where the numbers are the total number of connections through the specified port.

Currently, the total number of torrent connections displays okay, but that is it, none of the others display anything. Here is my conkyrc file. The section at hand is bolded:

> 
# Conky sample configuration
#
# the list of variables has been removed from this file in favour
# of keeping the documentation more maintainable.
# Check [http://conky.sf.net](http://conky.sf.net) for an up-to-date-list.

# set to yes if you want Conky to be forked in the background
background yes

# Use Xft?
use_xft yes

# Xft font when Xft is enabled
xftfont Trebuchet MS:size=10

# Text alpha when using Xft
xftalpha 0.9

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
update_interval 1.0

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window yes

# If own_window is yes, you may use type normal, desktop or override
own_window_type normal

# Use pseudo transparency with own_window?
own_window_transparent yes

# If own_window is yes, these window manager hints may be used
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 200 5
maximum_width 220

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Draw borders around graphs
draw_graph_borders no

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

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right
#alignment none

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 12
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
use_spacer no

# Allow each port monitor to track at most this many connections (if 0 or not set, default is 256)
#max_port_monitor_connections 256

# Maximum number of special things, e.g. fonts, offsets, aligns, etc.
#max_specials 512

# Maximum size of buffer for user text, i.e. below TEXT line.
#max_user_text 16384

# Colors
color0 lightgrey # normal text
color1 66BBCC	 # bars
color2 green	 # dynamic values (except u/l speed)
color3 yellow	 # ul speed

# variable is given either in format $variable or in ${variable}. Latter
# allows characters right after the variable and must be used in network
# stuff because of an argument

# stuff after 'TEXT' will be formatted on screen

TEXT


${color0}Uptime:$alignr${color2}$uptime_short
${color1}${hr 2}

${color0}CPU: $alignr$freq Mhz
${offset 20} ${color2}$cpu% ${color1}${cpubar}
${color0}RAM: $alignr$mem/$memmax
${offset 20} ${color2}$memperc% ${color1}${membar}
${color0}Swap: $alignr$swap/$swapmax
${offset 20} ${color2}$swapperc% ${color1}${swapbar}

${color1}${hr 2}
${color1}${addr eth0}
${color0}Download:$alignr${color2}${downspeed eth0} kb/s
${color0}Upload:$alignr${color3}${upspeed eth0} kb/s
[B]
${color1}Connections:
${color0}http: ${color3}${tcp_portmon 80 80 count}
${color0}ftp: ${color3}${tcp_portmon 20 21 count}
${color0}ssh: ${color3}${tcp_portmon 22 22 count}
${color0}pop3: ${color3}${tcp_portmon 110 110 count}
${color0}torrent: ${color3}${tcp_portmon 38040 38040 count}
[/B]
${color1}${hr 2}

${color0}root: ${fs_size /}$alignr${color2}${fs_free_perc /}% free
${offset 20}${color1}${fs_bar /}
${color0}storage: ${fs_size /media/Storage}$alignr${color2}${fs_free_perc /media/Storage}% free
${offset 20}${color1}${fs_bar /media/Storage}
${color0}network1: ${fs_size /media/Network1}$alignr${color2}${fs_free_perc /media/Network1}% free
${offset 20}${color1}${fs_bar /media/Network1}
${color0}network2: ${fs_size /media/Network2}$alignr${color2}${fs_free_perc /media/Network2}% free
${offset 20}${color1}${fs_bar /media/Network2}
${color0}backups: ${fs_size /media/Backup1}$alignr${color2}${fs_free_perc /media/Backup1}% free
${offset 20}${color1}${fs_bar /media/Backup1}

${color1}${hr 2}
${color0}Processes: ${color2}$processes ${alignr}${color0}Running: ${color2}$running_processes


Anyone have any ideas? Now, I do run though a router; could that be "hiding" the connections in some way? Any ideas would be appreciated.

---

### Post by munkyeetr on 2008-04-28
bump. anyone?

---

### Post by munkyeetr on 2008-04-29
one more BUMP in the hopes that someone out there has some ideas [-o<

---

### Post by SnakeHips on 2008-04-29
does this help? 


```

own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
use_spacer yes
use_xft no
update_interval 3.0
maximum_width 240
draw_shades no
draw_outline no # amplifies text if yes
draw_borders no
font arial
uppercase no # set to yes if you want all text to be in uppercase
stippled_borders 3
border_margin 9
border_width 10
# Default colors and also border colors, grey90 == #e5e5e5
default_color white
own_window_colour brown
own_window_transparent yes
alignment top_right
gap_x 10
gap_y 10
# stuff after 'TEXT' will be formatted on screen

TEXT
$color
${color orange}SYSTEM ${hr 2}$color
$nodename $sysname $kernel on $machine
${color orange}CPU ${hr 2}$color
$color${execi 1000 cat /proc/cpuinfo | grep 'model name' | sed -e 's/model name.*: //'}
Running @ ${freq_dyn}Mhz${alignr}
Load ${loadavg}
Temp${execi 1 /usr/bin/sensors | grep Core0 | cut -c11-18}C Usage: ${cpu}%$cpubar
${cpugraph 20,240 000000 ffffff}
${color orange}SENSORS ${hr 2}$color 
temp1${execi 1 /usr/bin/sensors | grep temp1 | cut -c11-18}C 
temp2${execi 1 /usr/bin/sensors | grep temp2 | cut -c11-18}C 
Fan${execi 1 /usr/bin/sensors | grep fan2 | cut -c11-18}pm

${color orange}GFX ${hr 2}$color
Nvidia ${execi 30 nvclock -i | grep 'Card:' | cut -c16-29}${alignr} Temp: ${execi 30 nvidia-settings -q gpucoretemp |grep '):' | awk '{print $4}'}C 

${color orange}TOP PROC ${hr 2}$color
NAME               PID     CPU%    MEM%
${top name 1}${top pid 1}  ${top cpu 1}  ${top mem 1}
${top name 2}${top pid 2}  ${top cpu 2}  ${top mem 2}
${top name 3}${top pid 3}  ${top cpu 3}  ${top mem 3}
${top name 4}${top pid 4}  ${top cpu 4}  ${top mem 4}

${color orange}MEMORY / DISK ${hr 2}$color
RAM:   $memperc%   ${membar 6}$color
Swap:  $swapperc%   ${swapbar 6}$color
Root: ${fs_used /}/${fs_size /}${alignr}${fs_bar 6, 80/}$color
Usr:  ${fs_used /usr}/${fs_size /usr}${alignr}${fs_bar 6, 80/usr}$color
Home: ${fs_used /home}/${fs_size /home}${alignr}${fs_bar 6, 80/home}

${color orange}LOGGING ${hr 2}$color
${execi 30 tail -n3 /var/log/messages | fold -w50}

${color orange}NETWORK (${addr eth0}) ${hr 2}$color
Down: $color${downspeed eth0} k/s ${alignr}Up: ${upspeed eth0} k/s
${downspeedgraph eth0 20,100 000000 ff0000} ${alignr}${upspeedgraph eth0 20,100 000000 00ff00}$color
Total: ${totaldown eth0} ${alignr}Total: ${totalup eth0}
Inbound: ${tcp_portmon 1 32767 count}${alignr}Outbound: ${tcp_portmon 32768 
61000 count}
Connections ${tcp_portmon 32768 61000 count} ${alignr} Service/Port
${tcp_portmon 32768 61000 rhost 0} ${alignr} ${tcp_portmon 32768 61000 rservice 0}
${tcp_portmon 32768 61000 rhost 1} ${alignr} ${tcp_portmon 32768 61000 rservice 1}
${tcp_portmon 32768 61000 rhost 2} ${alignr} ${tcp_portmon 32768 61000 rservice 2}
${tcp_portmon 32768 61000 rhost 3} ${alignr} ${tcp_portmon 32768 61000 rservice 3}
${tcp_portmon 32768 61000 rhost 4} ${alignr} ${tcp_portmon 32768 61000 rservice 4}
${tcp_portmon 32768 61000 rhost 5} ${alignr} ${tcp_portmon 32768 61000 rservice 5}
```

---

### Post by munkyeetr on 2008-04-29
SnakeHips: No, but thanks. I'm not looking for what the connections are, just *how many* connections **per port**. So how many through http(80) ftp(20,21), etc.

Even using the total up and total down would be fine for me, but my torrents use 38040, so they'll all be listed as outgoing even if they're inbound. Frustrating mostly because, as I said, the display of port 38040 - my torrents - works, but none of the others do.

---

