---
title: "hddtemp in conky on startup"
date: 2008-06-30
forum: General Help
---

### Post by kds1398 on 2008-06-30
Looking for an assist on this, I have a startup script:

```

#!/bin/bash
sleep 15;
conky;
``` which starts conky on system boot and my .conkyrc is as follows:
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
#

override_utf8_locale yes
text_buffer_size 256

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
background no

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes


# Update interval in seconds
update_interval 3

# Minimum size of text area
minimum_size 330 5
maximum_width 330

# Draw shades?
draw_shades no

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no
#font arial
uppercase no # set to yes if you want all text to be in 

# Stippled borders?
stippled_borders 3

# border margins
border_margin 8

# border width
border_width 8

# Default colors and also border colors, grey90 == #e5e5e5
default_color grey

own_window_colour brown
own_window_transparent yes

# Text alignment, other possible values are commented
#alignment top_left
alignment middle_right
#alignment middle_left
#alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 2
gap_y 12

# stuff after 'TEXT' will be formatted on screen

TEXT
$color
${color yellow}SYSTEM ${hr 2}$color
Node Name:            $nodename 
Kernel and Machine:   $kernel on $machine
Uptime:               $uptime
Wan IP:               ${execi 600 /home/kds1398/Scripts/wan-ip.sh}

${color yellow}CPU ${hr 2}$color
CPU 1 temp: ${execi 6 /usr/bin/sensors -f | grep Core\ 0 | paste -s | cut -c14-16;}F${alignr}CPU 2 temp: ${execi 6 /usr/bin/sensors -f | grep Core\ 1 | paste -s | cut -c14-16;}F
${cpugraph cpu1 25,140 000000 ff0000} ${alignr}${cpugraph cpu2 25,140 000000 00ff00}$color

${color yellow}PROCESSES ${hr 2}$color
Total Processes:$processes ${alignr}Running Processes:$running_processes
Usage: ${cpu}% ${cpubar}
Load: ${loadavg} 
Process Name      PID     CPU%      MEM%
${top name 1} ${top pid 1}   ${top cpu 1}    ${top mem 1}
${top name 2} ${top pid 2}   ${top cpu 2}    ${top mem 2}
${top name 3} ${top pid 3}   ${top cpu 3}    ${top mem 3}

${color yellow}MEMORY / DISK ${hr 2}$color
Hard Drive Temp:   ${execi 300 sudo hddtemp --u=F /dev/sda | cut -b36-38;} F
Root / $alignc ${fs_used /} / ${fs_size /} $alignr Free: ${fs_free_perc /}%
${fs_bar /}
RAM $alignc $mem/$memmax $alignr Used: $memperc%
$membar       $alignc $mem / $memmax $alignr          
Name              PID   MEM%
${top_mem name 1} ${top_mem pid 1} ${top_mem mem 1}  
${top_mem name 2} ${top_mem pid 2} ${top_mem mem 2}  
${top_mem name 3} ${top_mem pid 3} ${top_mem mem 3}
Swap /dev/sda6 $alignc ${fs_used /dev/sda6} / ${fs_size /dev/sda6} $alignr Free: ${fs_free_perc /dev/sda6}%
${fs_bar /dev/sda6}

${color yellow}WIFI (${addr wlan0}) ${hr 2}$color
SSID: ${wireless_essid wlan0}
Quality: ${color}${wireless_bitrate wlan0} ${wireless_link_qual_perc wlan0} ${wireless_link_bar wlan0}${color }
Down: $color${downspeed wlan0} k/s ${alignr}Up: ${upspeed wlan0} k/s
${downspeedgraph wlan0 25,140 000000 ff0000} ${alignr}${upspeedgraph wlan0 
25,140 000000 00ff00}$color
Total: ${totaldown wlan0} ${alignr}Total: ${totalup wlan0}
Inbound: ${tcp_portmon 1 32767 count} Outbound: ${tcp_portmon 32768 
61000 count}${alignr}Total: ${tcp_portmon 1 65535 count}

${color yellow}Ethernet0 (${addr eth0}) ${hr 2}$color
Down: $color${downspeed eth0} k/s ${alignr}Up: ${upspeed eth0} k/s
${downspeedgraph eth0 25,140 000000 ff0000} ${alignr}${upspeedgraph eth0 
25,140 000000 00ff00}$color
Total: ${totaldown eth0} ${alignr}Total: ${totalup eth0}

${color yellow}PORT CONNECTIONS ${hr 2}$color
Inbound: ${tcp_portmon 1 32767 count} Outbound: ${tcp_portmon 32768 
61000 count}${alignr}Total: ${tcp_portmon 1 65535 count}

Inbound Connection ${alignr} Local Service/Port$color
 ${tcp_portmon 1 32767 rhost 0} ${alignr} ${tcp_portmon 1 32767 lservice 0}
 ${tcp_portmon 1 32767 rhost 1} ${alignr} ${tcp_portmon 1 32767 lservice 1}
 ${tcp_portmon 1 32767 rhost 2} ${alignr} ${tcp_portmon 1 32767 lservice 2}
 ${tcp_portmon 1 32767 rhost 3} ${alignr} ${tcp_portmon 1 32767 lservice 3}
Outbound Connection ${alignr} Remote Service/Port$color
 ${tcp_portmon 32768 61000 rhost 0} ${alignr} ${tcp_portmon 32768 61000 rservice 0}
 ${tcp_portmon 32768 61000 rhost 1} ${alignr} ${tcp_portmon 32768 61000 rservice 1}
 ${tcp_portmon 32768 61000 rhost 2} ${alignr} ${tcp_portmon 32768 61000 rservice 2}
 ${tcp_portmon 32768 61000 rhost 3} ${alignr} ${tcp_portmon 32768 61000 rservice 3}

${color yellow}LOG MESSAGES ${hr 2}$color
${execi 30 tail -n4 /var/log/messages | fold -w50}
```

When conky starts it doesn't pull the HDD temp, however if I kill the conky process & manually start it again it will pull it no problem.  Also, I have added hddtemp to my sudoers file as a NOPASSWD command since hddtemp requires sudo access.

Can anyone assist?  I'm clueless where to go with this one.

---

### Post by kds1398 on 2008-06-30
The screenie was taken after I stopped & started conky.  When I boot my system the line reads "Hard Drive Temp:     F"

---

### Post by kds1398 on 2008-06-30
kds1398@kds1398-laptop:~/Documents$ conky_start.sh 
Conky: desktop window (12000b4) is subwindow of root window (13b)
Conky: window type - override
Conky: drawing to created window (4000002)
Conky: drawing to double buffer
[sudo] password for kds1398: 


hmmm.... something is amiss here with the script

---

### Post by kds1398 on 2008-06-30
use this command to solve this issue:

```
sudo dpkg-reconfigure hddtemp
```

When it asks if you want to install hddtemp with SUID bit set use yes.  You can then run hddtemp without having to sudo.  I also removed any NOPASSWD references to HDDTEMP from my sudoers file.  Works like a charm.

---

