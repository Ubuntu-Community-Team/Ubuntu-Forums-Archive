---
title: "[SOLVED] Conky cuts off at bottom"
date: 2008-05-25
forum: General Help
---

### Post by CSEatOSU on 2008-05-25
background yes
use_xft yes
xftfont HandelGotD:size=9
xftalpha 0.5
update_interval 1.0
total_run_times 0
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
minimum_size 230 5
maximum_width 260
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders yes
default_color white
default_shade_color black
default_outline_color white
alignment top_right
gap_x 10
gap_y 50
no_buffers yes
uppercase no
cpu_avg_samples 2
override_utf8_locale no
#${offset 5}${color}${pre_exec awk '/model name/' /proc/cpuinfo | sed -e 's/model name.*: //' | sed -e 's/  .*//'}${color red}${alignr}${freq_dyn_g}GHz
#${offset 5}${color}${pre_exec cat /proc/cpuinfo | grep -m1 'model name' | sed -e 's/model name.*: //' | sed -e 's/  .*//'}${color red}${alignr}${freq_dyn_g}GHz

TEXT
${color gold}SYSTEM ${hr 2}
${offset 5}${color cornflowerblue}Distro${alignr}${color}${pre_exec cat /etc/issue.net}
${offset 5}${color cornflowerblue}Gnome${alignr}${color}${pre_exec gnome-about --gnome-version | head -n 1 | awk '{print $2}'}
${offset 5}${color cornflowerblue}Kernel${alignr}${color}$sysname $kernel
${offset 5}${color cornflowerblue}Arch${alignr}${color}$machine
${offset 5}${color cornflowerblue}UpTime${alignr}${color}${uptime}
${offset 5}${color cornflowerblue}Battery${alignr}${color}${battery BAT0}

${color gold}CPU ${hr 2}
${offset 5}${color}${pre_exec awk -F '[ :][ :]+' '/^model name/ { print $2; }' /proc/cpuinfo | head -1}${color red}${alignr} ${freq_dyn_g cpu1}GHz
${offset 5}${color cornflowerblue}CPU1 ${color}${cpu cpu1}% ${cpubar cpu1}
${offset 5}${color}${pre_exec awk -F '[ :][ :]+' '/^model name/ { print $2; }' /proc/cpuinfo | tail -1}${color red}${alignr} ${freq_dyn_g cpu2}GHz
${offset 5}${color cornflowerblue}CPU2 ${color}${cpu cpu2}% ${cpubar cpu2}
${offset 5}${cpugraph cpu2 000000 ffffff}
${offset 5}${color cornflowerblue}Load${alignr}${color}$loadavg
${offset 5}${color cornflowerblue}Processes${alignr}${color}${processes}
${offset 5}${color cornflowerblue}Running ${alignr}${color} ${running_processes}

${color gold}MEMORY / DISK ${hr 2}
${offset 5}${color cornflowerblue}MEM${color}${alignr}${memmax}
${offset 5}$membar
${offset 5}${color cornflowerblue}HDD${color}${alignr}${fs_size /host}
${offset 5}${fs_bar /host}
${offset 5}${color cornflowerblue}/${color}${alignr}${fs_size /}
${offset 5}${fs_bar /}
${offset 5}${color cornflowerblue}/home${color}${alignr}${fs_size /home}
${offset 5}${fs_bar /home}

${color gold}NETWORK ${hr 2}
${alignc}${color red}${if_existing /sys/class/net/eth0/operstate up}WIRED${else}${if_existing /sys/class/net/wlan0/operstate up}Wi-Fi$endif$endif
${offset 5}${color cornflowerblue}Hostname${color}${alignr}$nodename
${offset 5}${color cornflowerblue}User${color}${alignr}${execi 1000 whoami}
${offset 5}${color cornflowerblue}Public IP${alignr}${color}${execi 1000 wget -O - [http://whatismyip.org/](http://whatismyip.org/) | tail}
${offset 5}${color cornflowerblue}${if_existing /sys/class/net/eth0/operstate up}Private IP$color$alignr${addr eth0}$else${if_existing /sys/class/net/wlan0/operstate up}Private IP$color$alignr ${addr wlan0}$endif$endif
${offset 5}${color cornflowerblue}${if_existing /sys/class/net/eth0/operstate up}Down: $color${downspeed eth0} k/s${color cornflowerblue}{$alignr}Total: $color${totaldown eth0}$else${if_existing /sys/class/net/wlan0/operstate up}MAC $color$alignr ${wireless_ap wlan0}$endif$endif
${offset 5}${if_existing /sys/class/net/eth0/operstate up}${downspeedgraph eth0 000000 ffffff}$else${if_existing /sys/class/net/wlan0/operstate up}${wireless_essid wlan0}${alignr}${wireless_bitrate wlan0}   ${wireless_link_qual_perc wlan0}%$endif$endif
${offset 5}${color cornflowerblue}${if_existing /sys/class/net/eth0/operstate up}Up: $color${upspeed eth0} k/s${color cornflowerblue}${alignr}Total: $color${totalup eth0}$else${if_existing /sys/class/net/wlan0/operstate up}Down: $color${downspeed wlan0} k/s${color cornflowerblue}$alignr Total: $color${totaldown wlan0}$endif$endif
${offset 5}${if_existing /sys/class/net/eth0/operstate up}${upspeedgraph eth0 000000 ffffff}$else${if_existing /sys/class/net/wlan0/operstate up}${downspeedgraph wlan0 000000 ffffff}$endif$endif
${offset 5}${color cornflowerblue}${if_existing /sys/class/net/wlan0/operstate up}Up: $color${upspeed wlan0} k/s${color cornflowerblue}${alignr}Total: $color${totalup wlan0}
${offset 5}${upspeedgraph wlan0 000000 ffffff}$endif

---

### Post by SkonesMickLoud on 2008-05-25
Try removing "$endif".

Failing that, you could always modify your conky start up to read:

```
conky && killall conky && conky
```

---

### Post by CSEatOSU on 2008-05-25
> **SkonesMickLoud said:**
> Try removing "$endif".

Failing that, you could always modify your conky start up to read:

```
conky && killall conky && conky
```

Well that kinda worked, it didn't cut off as much. :confused:

Could you please explain the start-up script you recommended?

EDIT:
Oh I see, *conky* will start conky as normal.  Then *killall conky* will kill the conky process just started, then the last *conky* is to restart it.  Hmm, let me try that and I'll restart.

---

### Post by CSEatOSU on 2008-05-25
> **SkonesMickLoud said:**
> Try removing "$endif".

Failing that, you could always modify your conky start up to read:

```
conky && killall conky && conky
```

Nope, that script you gave me didn't work.

---

### Post by CSEatOSU on 2008-05-25
I figured it out.  The last two lines need to be in their own if-statement :confused:

---

### Post by CSEatOSU on 2008-05-26
> **CSEatOSU said:**
> I figured it out.  The last two lines need to be in their own if-statement :confused:

Nope, that wasn't it.  Any suggestions?

---

### Post by CSEatOSU on 2008-05-27
I still haven't gotten a fix for it.  I've narrowed down the problem.  If I'm connected via eth0, it is fine no problems.  But if I'm connected to wireless (wlan0) for start-up, that's when I get the cut-off at the bottom.  I'm guessing it has something to do with the fact that the wireless is not yet initialized when conky is started, therefore it cannot load the bottom portion of the NETWORK section.

Help please.

---

### Post by easybake on 2008-05-27
> **CSEatOSU said:**
> I still haven't gotten a fix for it.  I've narrowed down the problem.  If I'm connected via eth0, it is fine no problems.  But if I'm connected to wireless (wlan0) for start-up, that's when I get the cut-off at the bottom.  I'm guessing it has something to do with the fact that the wireless is not yet initialized when conky is started, therefore it cannot load the bottom portion of the NETWORK section.

Help please.


try creating a delay in conky startup with a script. 

#!/bin/bash
sleep 60 && conky;

you can change '60' to allow for more/less time. remember to make it executable. put in home folder.

---

### Post by CSEatOSU on 2008-06-01
I reinstalled Ubuntu, I had done the Wubi install but decided to go all-out linux.  Now it doesn't happen.  Oh well, solved!

---

