---
title: "Conky problem"
date: 2008-07-03
forum: General Help
---

### Post by BlackSpot on 2008-07-03
Hello, my problem is that when i start ubuntu, conky loaded, but conky window dont match with desktop :/

---

### Post by rjmdomingo2003 on 2008-07-03
> **BlackSpot said:**
> Hello, my problem is that when i start ubuntu, conky loaded, but conky window dont match with desktop :/
Can you post your ~/.conkyrc?

---

### Post by BlackSpot on 2008-07-03
[HTML]background yes
use_xft
xftfont HandelGotD:size=8
xftalpha 0.5
update_interval 1
total_run_times 0   
own_window yes
own_window_type yes
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager 
double_buffer yes
minimum_size 300 5
maximum_width 250
draw_shades no
draw_outline no   
draw_borders no
draw_graph_borders no
default_color white
default_shade_color black
default_outline_color green
alignment top_right
gap_x 2 
gap_y 26
no_buffers yes
uppercase no
cpu_avg_samples 2
# Force UTF8? note that UTF8 support required XFT
override_utf8_locale yes 



TEXT
                                  ${color 00e500}MONIII PC

${color 1200ff}$hr
${color #00e500}Ubuntu 8.04 $sysname $kernel on $machine
${voffset -7}${color #1200ff}$hr ${color #FFFFFF}
${color #FFFFFF}Today is:                                                ${color white}${time %D}
${color #FFFFFF}The Time is:                                           ${color #FFFFFF}${time %H:%M.%S}${alignr}
${color #FFFFFF}Uptime:$alignr $uptime
${color #FFFFFF}Hostname:$alignr $nodename
${color #ffffff}Users:$alignr $user_number
${color 1200ff}$hr
${color #FFFFff}Network
eth1:$alignr ${addr eth1}
Inbound:$alignr ${downspeed eth1}kb/s 
${downspeedgraph eth1 ff7200 00e500}
Outbound:$alignr ${upspeed eth1} kb/s
${upspeedgraph eth1 00e500 ff7200}
Total down:                              ${totaldown eth1}
Total up:                                  ${totalup eth1}
${color #1200ff}$hr
${color ffffff}System statistics
$processes processes ($running_processes running)
${color ffffff}CPU Load: ${color #FF0000}${cpu cpu0}${color #FFFFFF}%
${cpugraph ff7200 00e500} 
${color ffffff}CPU: ${color FFFFFF}${freq_dyn cpu0}${color ffffff} MHz
CPU:${execi       1000 cat /proc/cpuinfo|grep 'model name'|sed -e 's/model name.*://'}
${color ffffff}Frequency (in MHz):$color $freq
${color ffffff}Frequency (in GHz):$color $freq_g
${color #1200ff}$hr
${color #ffffff}Now running processes
${color ffffff}NAME:            PID:        CPU%:      MEM%:
${color ffffff}${top name 1} ${top pid 1}   ${top cpu 1}    ${top mem 1}
${color ffffff}${top name 2} ${top pid 2}   ${top cpu 2}    ${top mem 2}
${color ffffff}${top name 3} ${top pid 3}   ${top cpu 3}    ${top mem 3}
${color ffffff}${top name 4} ${top pid 4}   ${top cpu 4}    ${top mem 4}
${color #1200ff}$hr
${color #ffffff}Memory
${color #ffffff}Memory:$alignc$mem/$memmax $alignr${color #FF0000}$memperc${color #ffffff}% 
${color ffffff}Memory cached:       ${color #FFFFFF}${cached}${color #FFFFFF}
${color ffffff}Memory buffered:     ${color #FFFFFF}${buffers}${color #FFFFFF}
${color #1200ff}$hr
${color #ffffff}Disk Information

Home:${color 00e500}$alignc${fs_used /home} / ${fs_size /home} $alignr ${fs_free_perc /home}%
${fs_bar /home}
${color #1200ff}$hr

${color ffffff}${execi 1800 /home/moni/scripts/weather.sh BUXX0005}

${font openlogos:size=100}${color 00e500}v${font}
${font openlogos:size=50}${color 00e500}  S  P${font}    
  [/HTML]

---

### Post by Doji on 2008-07-03
Try changing own_window_type to override.

---

### Post by psyopper on 2008-07-03
Conky uses a fake transparency to achieve its transparent window effect. Conky takes a snapshot of the desktop and then applies it as the Conky window background. 

What I believe is happening is that Conky is loading before your task bar. When the taskbar loads it pushes the Conky window up the screen. If you notice, the offset is the same width as your taskbar.

To avoid this try starting conky with a script using a wait command.

---

### Post by BlackSpot on 2008-07-03
write here the script

---

### Post by easybake on 2008-07-03
#!/bin/bash

sleep 15 && conky

---

