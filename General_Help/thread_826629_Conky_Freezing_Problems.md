---
title: "Conky Freezing Problems"
date: 2008-06-12
forum: General Help
---

### Post by spaise on 2008-06-12
Sup,

For some reason my conky shutsdown the process and i have to restart it.

anyone got any ideas as to why this is?

Here is my .conkyrc


#
#
# ·ë{¶«¡Çø}&#8212;æÂê®Úî&#339;ô&#8364;âÒÌÏÈ¬µÙ@©&#9830;ß~÷&#376;´É[å»ÛÁ]&#8211;ÆÅÊ¤&#376;ªï&#338;Ô¥À·ÎÍË|Óû#¢~¿¿·\± 
#######################################################################
# variables ###########################################################

# fork to background ? ################################################
background yes

# font settings #######################################################
use_xft yes
#font monospace-8
xftfont Acknowledge TT BRK:size=8
#xftfont Edit Undo BRK:size=8
#xftfont Visitor TT2 BRK:size=10
uppercase yes
override_utf8_local yes

# update every 1 secs #################################################
update_interval 1

# stay running forever ################################################
total_run_times 1000

# draw to root window #################################################
own_window no

# avoid flickering ####################################################
double_buffer yes

# size ################################################################
minimum_size 1270 800
maximum_width 1270

# position ############################################################
alignment bottom_left
#alignment top_middle
#alignment top_right
#alignment bottom_left
#alignment bottom_middle
#alignment bottom_right
#alignment middle_left
#alignment middle_right
gap_x 0
gap_y 0

# colors ##############################################################
default_color white
default_shade_color white
default_outline_color black
# custom colors #######################################################
color0 FFFFFF
color1 F5F5F5
color2 A2AEC6
color3 696969
color4 D3D3D3
color5 6495ED
color6 87CEFA
color7 5F9EA0
color8 BBBBBB
color9 262729


# borders #############################################################
draw_borders no
draw_graph_borders yes
stippled_borders 8
border_margin 2
border_width 1

# shades ##############################################################
draw_shades no

# outline #############################################################
draw_outline no

# spacer ##############################################################
use_spacer no

# buffers (Substract (file system) buffers from used memory?)##########
no_buffers yes

# sampling ############################################################
cpu_avg_samples 2
net_avg_samples 2

# configuration #######################################################



TEXT
${voffset 10}${offset 10}$color8 /$color3 System$color8 /
${offset 10}$color2 $sysname$color9 -$color2 $machine
${offset 10}$color2 $kernel
${offset 10}$color2 Spaise$color9 on$color2 $nodename
${offset 10}$color6 ${time %A %d/%m/%y %kh%M}
${offset 10}$color2 Uptime :$color6 $uptime



${voffset -25}${offset 70}$color8 /$color3 CPU #01$color8 /
${offset 80}$color2 Temperature :$color4 ${execi 10 sensors | grep -A 2 '^coretemp-isa-0000' | cut -c15-18 | grep '°'}C  -  $color2 Frequency : $color4${freq_dyn cpu1}$color2 MHz
${offset 80}$color2 Load: $color9 ${cpubar cpu1 6,220} $color4${cpu cpu1}$color2 %
${offset 80}$color4 ${cpugraph cpu1 15,255 262729 87CEFA}
${offset 70}$color8 /$color3 CPU #02$color8 /
${offset 80}$color2 Temperature :$color4 ${execi 10 sensors | grep -A 2 '^coretemp-isa-0001' | cut -c15-18 | grep '°'}C  -  $color2 Frequency : $color4${freq_dyn cpu2}$color2 MHz 
${offset 80}$color2 Load: $color9 ${cpubar cpu2 6,220} $color4${cpu cpu2}$color2 %
${offset 80}$color4 ${cpugraph cpu2 15,255 262729 87CEFA}


${voffset 70}${offset 20}$color8 /$color3 Wifi (wlan0)$color8 /
${offset 35}$color2 essid : $color4${wireless_essid wlan0}$color2 - MAC : $color4${wireless_ap wlan0}
${offset 35}$color2 Wifi Level : $color4${wireless_link_qual wlan0}$color2 /$color4 ${wireless_link_qual_max wlan0}$color2 - Quality: $color4 ${wireless_link_qual_perc wlan0}
${offset 35}$color2 IPv4 : $color4${addr wlan0}$color2 -$color4 ${execi 1800 ~/.conky/ip.sh}
${offset 30}$color2 Down : $color4 ${downspeed wlan0}$color2 kb/s
${offset 30}$color4 ${downspeedgraph wlan0 15,250 262729 87CEFA}
${offset 30}$color2 Up : ${offset 6} $color4 ${upspeed wlan0}$color2 kb/s
${offset 30}$color4 ${upspeedgraph wlan0 15,250 262729 87CEFA}


${voffset 80}${offset 20}$color8 /$color3 Volumes$color8 /
${offset 35}$color2 #!-root :  $color4 ${fs_used_perc /}% - ${fs_used /} + ${fs_free /} = ${fs_size /}
${offset 35}$color9 ${fs_bar 6,320 /}
${offset 50}$color2 #!-home :  $color4 ${fs_used_perc /home}% - ${fs_used /home} + ${fs_free /home} = ${fs_size /home}
${offset 50}$color9 ${fs_bar 6,320 /home}


${voffset -90}${offset 600}$color8 /$color3 Memory$color8 /
${offset 605}$color2 RAM: ${offset 0} $color9 ${membar 6,200}$color4 $mem ($memperc%)
${offset 610}$color2 Swap: $color9 ${swapbar 6,200}$color4 $swap ($swapperc%)

${voffset -90}${offset 1110}$color8 /$color3 Activity$color8 /
${offset 1105}$color2 Hdd Temp:$color4 ${hddtemp /dev/sda}
${offset 1100}$color2 Read/Write: $color4 $diskio
${offset 1090}$color2 Process :$color4 $running_processes$color2 /$color4 $processes
${offset 1090}$color6 ${top name 1}$alignr$color4 ${top cpu 1}%
${offset 1090}$color5 ${top name 2}$alignr$color4 ${top cpu 2}%
${offset 1090}$color5 ${top name 3}$alignr$color4 ${top cpu 3}%
${offset 1090}$color5 ${top name 4}$alignr$color4 ${top cpu 4}%
${offset 1090}$color5 ${top name 5}$alignr$color4 ${top cpu 5}%
${offset 1090} ${diskiograph 15,180 262729 87CEFA}

---

### Post by cammin on 2008-06-12
**total_run_times 1000**
should be
**total_run_times 0**

---

