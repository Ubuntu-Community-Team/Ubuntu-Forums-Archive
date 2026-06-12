---
title: "Conky isn't transperant while using compiz"
date: 2008-04-25
forum: General Help
---

### Post by zka on 2008-04-25
My conky stopped being transparent as soon as I disabled nautilus option show deskop through configuration editor in order to have different wallpapers on each workspace. Instead the background of conky shows the part of the old wallpaper(default background on hardy).

Googled around and the problem seems to be that conky uses the default background of nautilus instead of being a "real" transperant. One solution was to use feh but the only guide on how to do it was for kde and it didn't work for me..

How do I fix this ? :(

PS: Only started using ubuntu few weeks ago so be easy on an eventual answer so that i can apply it myself =)

Thanks
 
My conky cfg taken from gnomelooks i think...

```
background no
font Zekton:size=7
xftfont Zekton:size=7
use_xft yes
xftalpha 0.1
update_interval 1.0
total_run_times 0
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no
minimum_size 220 5
maximum_width 220
default_color d7d7d7
default_shade_color black
default_outline_color black
alignment middle_right
gap_x 2
gap_y 10
no_buffers yes
cpu_avg_samples 2
override_utf8_locale no
uppercase no # set to yes if you want all text to be in uppercase
use_spacer left

TEXT
${font Zekton:style=Bold:pixelsize=42}${alignc}${time %H:%M:%S}${font Zekton:size=7}
SYSTEM ${hr 1 }

Hostname: $alignr$nodename
Kernel: $alignr$kernel
Uptime: $alignr$uptime
Processes: ${alignr}$processes ($running_processes running)
Load: ${alignr}$loadavg
Battery    ${battery_time BAT0} ${alignr}(${battery BAT0})
${battery_bar 4 BAT0}
CPU       ${alignc} ${freq}MHz / ${acpitemp}C ${alignr}(${cpu cpu1}%)
${cpubar 4 cpu1}
${cpugraph}
RAM ${alignr}$mem / $memmax ($memperc%)
${membar 4}
SWAP ${alignr}$swap / $swapmax ($swapperc%)
${swapbar 4}

Highest CPU $alignr CPU% MEM%
${top name 1}$alignr${top cpu 1}${top mem 1}
${top name 2}$alignr${top cpu 2}${top mem 2}
${top name 3}$alignr${top cpu 3}${top mem 3}

Highest MEM $alignr CPU% MEM%
${top_mem name 1}$alignr${top_mem cpu 1}${top_mem mem 1}
${top_mem name 2}$alignr${top_mem cpu 2}${top_mem mem 2}
${top_mem name 3}$alignr${top_mem cpu 3}${top_mem mem 3}

FILESYSTEM ${hr 1}${color}

Root: ${alignr}${fs_free /} / ${fs_size /}
${fs_bar 4 /}
Home: ${alignr}${fs_free /home} / ${fs_size /home}
${fs_bar 4 /}

NETWORK ${hr 1}${color}

Down ${downspeed wlan0} k/s ${alignr}Up ${upspeed wlan0} k/s
${downspeedgraph wlan0 25,107} ${alignr}${upspeedgraph wlan0 25,107}
Total ${totaldown wlan0} ${alignr}Total ${totalup wlan0}
```

---

### Post by pompeyjohn on 2008-07-07
+1 me too

---

### Post by loomsen on 2008-08-09
Hi Guys.

There's no way to make conkey look like it used to, due to its fake transparency. But I found a rather satisfying way to still have it integrated into my desktop as far as possible.

As you are using Compiz anyways since u suffer this problem, try and use ccsm to define window rules.

First set your conky to draw its own window, which may not be transparent.

```
 
own_window yes
own_window_hints undecorated
own_window_type normal  #desktop
own_window_transparent no

```

Then press Alt+F2 and type ccsm to open up the settings manager window.
Now u may want do define window rules for conky. You may do this under Window Management --> Window rules. Now add
```
class=conky
```
to every field EXCEPT 
Above, Fullscreen, No RGB Visuals.

U may define size rules as well, tho I didnt.

Then go back to ccsm main menu, chose general options, opacity settings,
window opacity --> new 
and add
```
class=conky
```
once again.

Now u gotta toy around and find the opacity settings according to your very own taste.

Some screenshots how this looks:

[[img]http://www.ubuntu-pics.de/thumb/2002/screenshot01PK44P.png[/img]](http://www.ubuntu-pics.de/bild/2002/screenshot01PK44P.png)  [[img]http://www.ubuntu-pics.de/thumb/2003/screenshot02RXRSP.png[/img]](http://www.ubuntu-pics.de/bild/2003/screenshot02RXRSP.png)
[[img]http://www.ubuntu-pics.de/thumb/2004/screenshot036LSNW.png[/img]](http://www.ubuntu-pics.de/bild/2004/screenshot036LSNW.png)  [[img]http://www.ubuntu-pics.de/thumb/2005/screenshot04M3Y8N.png[/img]](http://www.ubuntu-pics.de/bild/2005/screenshot04M3Y8N.png)

You may like it. I actually dont know what to think of it yet... :)

---

