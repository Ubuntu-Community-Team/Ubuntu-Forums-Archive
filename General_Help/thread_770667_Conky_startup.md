---
title: "Conky startup"
date: 2008-04-27
forum: General Help
---

### Post by Donald-Duck on 2008-04-27
I added conky to my session start up, and it does start up. But it goes over all my windows, anything opened after it appears below it. Is there anyway to fix this?

Edit: I should add that if I kill the proccess and start it from terminal it works fine.

---

### Post by Donald-Duck on 2008-04-27
I think I solved this, I disabled my screenlets and stopped screenlet manager starting up and it seems to be fixed. Looks like they were conflicting

---

### Post by Necrobrit on 2008-08-01
I am having the same exact issue, disabling screenlets isn't a solution for me as I don't have them installed in the first place. I'm using compiz with emerald. The issue appears to be with compiz, as the behavior persists without emerald installed. Without compiz or emerald it simply blinks on for a second on startup, there are quite a few google hits on that problem so I'm going to try and fix that and see if the solutions aren't one and the same. As with the original poster everything works perfectly if I use killall and restart conky.

I've already tried a bash script that uses sleep before launching, the result is either the same or it fails to launch altogether.

conkyrc:
```
background yes
font Snap.se:size=8
xftfont Snap.se:size=8
use_xft yes
xftalpha 0.1
update_interval 3.0
total_run_times 0
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
draw_shades yes
draw_outline no
draw_borders no
draw_graph_borders no
minimum_size 206 5
maximum_width 206
default_color ffffff
default_shade_color 000000
default_outline_color 000000
alignment top_right
gap_x 6
gap_y 22
no_buffers yes
cpu_avg_samples 2
override_utf8_locale no
uppercase no # set to yes if you want all text to be in uppercase
use_spacer no


TEXT
${font arial:style=Bold:pixelsize=56}${alignc}${time %H:%M}${font Snap.se:size=8}
$alignc${color }${time %a %e %B %G}

${font arial:style=Bold:pixelsize=12}SYSTEM${font Snap.se:size=8} ${hr 1 }

Hostname: $alignr$nodename
Kernel: $alignr$kernel
Uptime: $alignr$uptime
Processes: ${alignr}$processes ($running_processes running)
Load: ${alignr}$loadavg

CPU       ${alignc} ${freq}MHz / ${acpitemp}C ${alignr}(${cpu cpu1}%)
${cpubar 4 cpu1}
${cpugraph cccccc ffffff}

RAM ${alignr}$mem / $memmax ($memperc%)
${membar 4}

SWAP ${alignr}$swap / $swapmax ($swapperc%)
${swapbar 4}

Highest CPU $alignr CPU% MEM%
${hr 1}
${top name 1}$alignr${top cpu 1}${top mem 1}
${top name 2}$alignr${top cpu 2}${top mem 2}
${top name 3}$alignr${top cpu 3}${top mem 3}

Highest MEM $alignr CPU% MEM%
${hr 1}
${top_mem name 1}$alignr${top_mem cpu 1}${top_mem mem 1}
${top_mem name 2}$alignr${top_mem cpu 2}${top_mem mem 2}
${top_mem name 3}$alignr${top_mem cpu 3}${top_mem mem 3}



${font Aerial:style=Bold:pixelsize=12}FILESYSTEM ${font Snap.se:size=8}${hr 1}

Root: ${alignr}${fs_free /} / ${fs_size /}
${fs_bar 4 /}

Home: ${alignr}${fs_free /home} / ${fs_size /home}
${fs_bar 4 /home}



${font Aerial:style=Bold:pixelsize=12}NETWORK ${font Snap.se:size=8}${hr 1}

Down ${downspeed eth0} k/s ${alignr}Up ${upspeed eth0} k/s
${downspeedgraph eth0 25,107 cccccc ffffff} ${alignr}${upspeedgraph eth0 25,107 cccccc ffffff}
Total ${totaldown eth0} ${alignr}Total ${totalup eth0}

```

A screenshot just after startup with FF launched is attached to show exactly whats going on. 

Sorry for reviving a somewhat old thread. Any help/ideas are much appreciated, I'm going to continue to work at it.

EDIT: Ah, I've fixed it, and the problem was me. I revisited the delayed start bash script idea again, and realized that even though it was only one line long I had managed to screw it up by adding a ; to the end.

---

