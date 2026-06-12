---
title: "conkyrc documentation"
date: 2007-08-11
forum: General Help
---

### Post by BDNiner on 2007-08-11
Where can i find documentation on conkyrc. Like what all the options are? how to setup it? I got it installed, but now i would like to move it around the desktop. Now it covers the top right had corner of my desktop and i am unable to click on any applets over there? Also does it work well with compiz fusion?

Their main web site is kinda poor. Any help?

---

### Post by kellemes on 2007-08-11
> **BDNiner said:**
> Where can i find documentation on conkyrc. Like what all the options are? how to setup it? I got it installed, but now i would like to move it around the desktop. Now it covers the top right had corner of my desktop and i am unable to click on any applets over there? Also does it work well with compiz fusion?

Their main web site is kinda poor. Any help?

The best way to learn about Conky is to download the samples-sourcecode.

[http://conky.sourceforge.net/screenshots.html](http://conky.sourceforge.net/screenshots.html)

---

### Post by BDNiner on 2007-08-11
How do i decide where to display conky? I have found where to set the alignment of the text. but it shows up in the middle of the screen and i would like it on the right hand side. I think i will print out all the scripts and compare them to see if i can make any sense of this. Thank you for your help.

---

### Post by kellemes on 2007-08-11
I'm giving you my conkyscript, adapted from one of the examples.
It shows bottom-left on my screen.

I think it's this line that does it..
```
alignment bottom_left
```

I can't test it since I´m on XP right now.

```

# Conky configuration
#
# the list of variables has been removed from this file in favour
# of keeping the documentation more maintainable.
# Check http://conky.sf.net for an up-to-date-list.
#
# The additions to this config require curl and xsltproc be installed

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
mail_spool $MAIL

# Update interval in seconds
update_interval 1.0

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window no

# If own_window is yes, you may use type normal, desktop or override
own_window_type normal

# Use pseudo transparency with own_window?
own_window_transparent yes

# If own_window_transparent is set to no, you can set the background colour here
own_window_colour hotpink

# If own_window is yes, these window manager hints may be used
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Max window size
maximum_width 310

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
stippled_borders 0

# border margins
border_margin 4

# border width
border_width 1

# Default colors and also border colors
default_color EEDFCC
default_shade_color grey
default_outline_color grey

# Text alignment, other possible values are commented
#alignment top_left
#alignment top_right
alignment bottom_left
#alignment bottom_right
#alignment none

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 10
gap_y 50

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
override_utf8_locale no


# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer no

#   mldonkey_hostname     Hostname for mldonkey stuff, defaults to localhost
#   mldonkey_port         Mldonkey port, 4001 default
#   mldonkey_login        Mldonkey login, default none
#   mldonkey_password     Mldonkey password, default none

# boinc (seti) dir
# seti_dir /opt/seti

# Allow for the creation of at least this number of port monitors (if 0 or not set, default is 16) 
#min_port_monitors 16

# Allow each port monitor to track at least this many connections (if 0 or not set, default is 256)
#min_port_monitor_connections 256

# none, xmms, bmp, audacious, infopipe (default is none)
#xmms_player none

# variable is given either in format $variable or in ${variable}. Latter
# allows characters right after the variable and must be used in network
# stuff because of an argument

# stuff after 'TEXT' will be formatted on screen

# aside
#${color #888888}${cpugraph cpu1 888888 e9c703}
#${color #888888}${cpugraph cpu2 888888 e9c703}

#696969 = DimGray
#b22222 = FireBrick


TEXT



${color firebrick}Host:$color $nodename - $sysname $kernel on $machine

${color firebrick}Uptime:$color $uptime ${color firebrick}- Load:$color $loadavg

${color firebrick}Core 1 Usage:$color ${alignc} ${cpu cpu1}% ${color DimGray}${cpubar cpu1}
${color firebrick}Core 2 Usage:$color ${alignc} ${cpu cpu2}% ${color DimGray}${cpubar cpu2}

${color firebrick}RAM Usage:$color $mem/$memmax $color ${alignc}$memperc% ${color DimGray}${membar}
${color firebrick}Swap Usage:$color $swap/$swapmax $color ${alignc}$swapperc% ${color DimGray}${swapbar}
${color firebrick}Processes:$color $processes  ${color firebrick}Running:$color $running_processes
${color firebrick}File systems:
$color / ${alignc}${fs_used_perc /}% ${color DimGray}${fs_bar /}
$color /boot ${alignc}${fs_used_perc /boot}% ${color DimGray}${fs_bar /boot}
$color /home ${alignc}${fs_used_perc /home}% ${color DimGray}${fs_bar /home}
$color /mnt/crap ${alignc}${fs_used_perc /mnt/crap}% ${color DimGray}${fs_bar /mnt/crap}
$color /mnt/xp ${alignc}${fs_used_perc /mnt/xp}% ${color DimGray}${fs_bar /mnt/xp}

${color firebrick}Networking:${alignr}${color firebrick}IP Address: $color${addr eth0}
${color firebrick}Down:$color ${downspeed eth0} k/s ${offset 80}${color firebrick}Up:$color ${upspeed eth0} k/s
${color Dimgray}${downspeedgraph eth0 20,150 696969 b22222} ${color Dimgray}${upspeedgraph eth0 20,150 696969 b22222}
${color firebrick}Status:
${color firebrick}Active Port(s):
$color Inbound: ${tcp_portmon 1 32767 count}  Outbound: ${tcp_portmon 32768 61000 count}${alignr}Total: ${tcp_portmon 1 65535 count}

${color firebrick}Mini-top:
${color}Name              PID     CPU%   MEM%
${color white} ${top name 1} ${top pid 1} ${top cpu 1} ${top mem 1}
$color ${top name 2} ${top pid 2} ${top cpu 2} ${top mem 2}
$color ${top name 3} ${top pid 3} ${top cpu 3} ${top mem 3}
$color ${top name 4} ${top pid 4} ${top cpu 4} ${top mem 4}
${color firebrick}Mem usage:
${color white} ${top_mem name 1} ${top_mem pid 1} ${top_mem cpu 1} ${top_mem mem 1}
$color ${top_mem name 2} ${top_mem pid 2} ${top_mem cpu 2} ${top_mem mem 2}
$color ${top_mem name 3} ${top_mem pid 3} ${top_mem cpu 3} ${top_mem mem 3}

${color firebrick}Arch: Recent Package Updates:
$color${execi 900 /home/kelp/scripts/conky/conky-rss.sh http://www.archlinux.org/feeds/packages/ 6 2}

${color firebrick}System Logs:
${color firebrick}Messages:
$color${execi 10 /usr/bin/tail -n 5 /var/log/messages.log | cut -c 23-}
${color firebrick}Security:
$color${execi 10 /usr/bin/tail -n 5 /var/log/auth.log | cut -c 23-}


```

---

### Post by BDNiner on 2007-08-11
LOL, it covered up all my icons. How do i end conky without restarting my computer?

---

### Post by por100pre1 on 2007-08-11
> **BDNiner said:**
> LOL, it covered up all my icons. How do i end conky without restarting my computer?

```
pkill conky
```

---

### Post by amadeus266 on 2007-08-12
I just installed conky but I cannot seem to find my .comkyrc file. Where is it usually found?

---

### Post by hikaricore on 2007-08-12
> **amadeus266 said:**
> I just installed conky but I cannot seem to find my .comkyrc file. Where is it usually found?

It's in your home directory.
Files beginning with a "." are hidden by default and you'll need to select the show hidden files option.

If you don't have a .conkyrc file you can just find a template and create the file.

---

### Post by kellemes on 2007-08-12
You better create a copy of conkyrc (or one of the online samples), put this in ~/scripts
and then "Conky -c ~/scripts/mylittleconkyrc"

About hiding the icons see: [http://conky.sourceforge.net/faq.html]("http://conky.sourceforge.net/faq.html")

---

