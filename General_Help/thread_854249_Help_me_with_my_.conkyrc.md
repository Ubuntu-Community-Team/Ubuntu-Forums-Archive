---
title: "Help me with my .conkyrc"
date: 2008-07-09
forum: General Help
---

### Post by bobbob1016 on 2008-07-09
I'm trying to get conky working.  I found this file, and changed a few things, as in he had a dual-core, I have a quad-core so I added cpu3 and cpu4.  I have compiz enabled with multiple wallpapers, and nautilus not drawing the desktop.  When I had transparency enabled, the transparency went showed my nautilus background through my compiz one.  I disabled transparency and my compiz wallpaper went away entirely and I just had my skydome showing, and when I dragged a window, I got glitches that were exactly like the "clipping" code from Doom 2.  I also changed where he had wlan0 to eth0, since I'm not using wireless on this computer.  Here is my .conkyrc:

use_xft yes
xftfont HandelGotD:size=8
xftalpha 0.1
update_interval 0.5
total_run_times 0
own_window yes
own_window_type desktop
own_window_transparent no
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
minimum_size 200 5
maximum_width 200
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no
default_color black
default_shade_color black
default_outline_color black
alignment top_right
gap_x 18
gap_y 48
no_buffers yes
uppercase no
cpu_avg_samples 2
net_avg_samples 1
override_utf8_locale no
use_spacer yes

TEXT
$sysname $kernel $alignr $machine
Intel Pentium Quad $alignr${freq_g cpu0}Ghz
$alignr
${cpugraph cpu0 16,200 ffffff ffffff}
CPU:1  ${cpu cpu1}% ${cpubar cpu1}
CPU:2  ${cpu cpu2}% ${cpubar cpu2}
CPU:3  ${cpu cpu3}% ${cpubar cpu3}
CPU:4  ${cpu cpu4}% ${cpubar cpu4}

MEM $alignc $mem / $memmax $alignr $memperc%
$membar

/home $alignc ${fs_used /home} / ${fs_size /home} $alignr ${fs_free_perc /home}%
${fs_bar /home}

Disk i/o ${diskiograph 16,200} 

Processes 
$alignr $running_processes Running 
$alignr $processes Sleeping

Top Processes

CPU $alignr CPU% MEM%

${top name 1}$alignr${top cpu 1}${top mem 1}
${top name 2}$alignr${top cpu 2}${top mem 2}
${top name 3}$alignr${top cpu 3}${top mem 3}
${top name 4}$alignr${top cpu 4}${top mem 4}

MEM $alignr CPU% MEM%

${top_mem name 1}$alignr${top_mem cpu 1}${top_mem mem 1}
${top_mem name 2}$alignr${top_mem cpu 2}${top_mem mem 2}
${top_mem name 3}$alignr${top_mem cpu 3}${top_mem mem 3}

IP on eth0 $alignr ${addr eth0}

Down $alignr ${downspeed eth0} kb/s
${downspeedgraph eth0}
Up $alignr ${upspeed eth0} kb/s
${upspeedgraph eth0 16,200}

Connections ${tcp_portmon 32768 61000 count} ${alignr} Service/Port

${tcp_portmon 32768 61000 rhost 0} ${alignr} ${tcp_portmon 32768 61000 rservice 0}
${tcp_portmon 32768 61000 rhost 1} ${alignr} ${tcp_portmon 32768 61000 rservice 1}
${tcp_portmon 32768 61000 rhost 2} ${alignr} ${tcp_portmon 32768 61000 rservice 2}
${tcp_portmon 32768 61000 rhost 3} ${alignr} ${tcp_portmon 32768 61000 rservice 3}
${tcp_portmon 32768 61000 rhost 4} ${alignr} ${tcp_portmon 32768 61000 rservice 4}
${tcp_portmon 32768 61000 rhost 5} ${alignr} ${tcp_portmon 32768 61000 rservice 5}

I attached the "clipping" glitch

---

### Post by Minus_Fireal on 2008-07-09
Try changing this "own_window_type desktop" to "own_window_type override"

See how that works out..

---

### Post by bobbob1016 on 2008-07-09
I changed it to "override" and I got this when I ran conky in a terminal:

Conky: use_spacer should have an argument of left, right, or none.  'yes' seems to be some form of 'true', so defaulting to right.
Conky: desktop window (52) is root window
Conky: window type - override
Conky: drawing to created window (4c00001)
Conky: drawing to double buffer

I can guess what "defaulting to right" is, but the rest I don't know.  This didn't mess up the desktop though, so I guess we're heading in the right direction.

---

### Post by cammin on 2008-07-09
change
**use_spacer yes**
to 
**use_spacer none** 
Or left or right

---

### Post by Sealbhach on 2008-07-10
> **bobbob1016 said:**
> I changed it to "override" and I got this when I ran conky in a terminal:

Conky: use_spacer should have an argument of left, right, or none.  'yes' seems to be some form of 'true', so defaulting to right.
Conky: desktop window (52) is root window
Conky: window type - override
Conky: drawing to created window (4c00001)
Conky: drawing to double buffer

I can guess what "defaulting to right" is, but the rest I don't know.  This didn't mess up the desktop though, so I guess we're heading in the right direction.

I get that all the time, but my conky works fine.Perhaps 'yes' should be changed to'true'in the conky.rc?


.

---

### Post by bobbob1016 on 2008-07-10
That fixed that error, but I still don't see conky when I run "conky" in a terminal, or alt+f2 and type conky.

Edit:  When I run it in the terminal, it says "Conky: desktop window (52) is root window" it's finding my nautilus desktop, which is still rendering under my compiz wallpapers.  I disabled compiz wallpaper, and now I see conky over my nautilus background.  Anyone know how to disable the nautilus background (I told it not to draw in gconf-editor)?  Or get Conky to see my compiz wall paper as the desktop?

---

### Post by Minus_Fireal on 2008-07-10
Try changing this "own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager"
to this  "own_window_hints undecorated,sticky,skip_taskbar,skip_pager"

---

### Post by bobbob1016 on 2008-07-10
That seems to have done it.  I went to scratch and changed the "own_window_hints" line.  Thanks.  Now I can play with the other conky settings.

---

