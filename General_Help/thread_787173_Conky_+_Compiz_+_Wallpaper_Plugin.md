---
title: "Conky + Compiz + Wallpaper Plugin"
date: 2008-05-08
forum: General Help
---

### Post by Locutus_of_Borg on 2008-05-08
Hello, I am running Compiz with the wallpaper plugin so as to have different wallpapers on each side of my cube/sphere.  To do this I had to stop XFCE from managing my desktop, and doing so caused conky to no longer display.

how does fix plz? :)

---

### Post by mano cazalet on 2008-05-08
i am not sure
but maybe the only option is to run conky in its own window by adding own_window yes
to conkyrc

---

### Post by Locutus_of_Borg on 2008-05-08
own_window was already set as yes

here is the conkyrc if it helps:
```
# do not fork to background
background no

# font settings
use_xft no
font monospace-8
uppercase no

# update every 3 secs
update_interval 3

# stay running forever
total_run_times 0

own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# avoid flickering
double_buffer yes

# size
minimum_size 1600 800
maximum_width 1600

# position
alignment top_left
gap_x 0
gap_y 0

# colors
default_color white
default_shade_color black
default_outline_color black
color0 000000
color1 1a1a1a
color2 3a3a3a

# borders
draw_borders no
stippled_borders 8
border_margin 4
border_width 1

# shades
draw_shades no

# outline
draw_outline no

# spacer
use_spacer no

# buffers
no_buffers yes

# sampling
cpu_avg_samples 2
net_avg_samples 2

# configuration
TEXT
${voffset 50}${offset 950}${color2}System
${offset 900}$color1 $nodename $kernel
${offset 933}$color1 Uptime:$color2 $uptime

${voffset 25}${offset 1025}${color2}Power
${offset 1050}$color1 $acpiacadapter
${offset 950}$color1 ${execi 8 acpi -t | grep Battery}

${voffset 5}${offset 1100}${color2}CPU
${offset 939}$color1 Frequency: $color2$freq MHz $color1 Temperature:$color2 $acpitemp C
${offset 910}$color1 Load: $color2$cpu% ${cpubar cpu0 6,223}
${offset 925}$color1 ${cpugraph cpu0 24,300 000000 ffffff}

${voffset 46}${offset 898}${color2}Memory
${voffset 4}${offset 808}$color1 RAM: $color2$mem ($memperc%) ${membar 6,200}
${voffset 1}${offset 777}$color1 Swap: $color2$swap ($swapperc%) ${swapbar 6,200}

${voffset 66}${offset 1033}${color2}Network (wlan0)
${voffset 2}${offset 966}$color1 IPv4: $color2${addr wlan0} ${color #2a2a2a}
${offset 919}$color1 Down: $color2${downspeed wlan0} k/s $color1 Up:$color2 ${upspeed wlan0} k/s
${voffset 3}${offset 950}$color1 ${downspeedgraph wlan0 12,300 000000 2a2a2a}
${offset 950}${voffset -3}$color1 ${upspeedgraph wlan0 12,300 000000 2a2a2a}

${voffset 66}${offset 979}${color2}Filesystem
${voffset 1}${offset 888}$color1 root $color2${fs_used /} (${fs_used_perc /}%) ${fs_bar 6,200 /}
${voffset 2}${offset 919}$color1 borg $color2${fs_used /home} (${fs_used_perc /home}%) ${fs_bar 6,200 /home}


```

---

### Post by mano cazalet on 2008-05-08
hmmm

i'm just shooting in the dark but maybe if you tell compiz that conky is a widget

---

### Post by Locutus_of_Borg on 2008-05-08
thats interesting and may work...i havent been able to get it working while playing with some options yet though.

i have "class=Conky" in widget layers, and have tried changing the window options in conkyrc a lot, but no success yet..

---

### Post by xtracool_protik on 2009-11-15
hope u guys still reading this post 
Seems I've issue with using wallpaper plugin
It is not working with Karmic
Can anyone clear it for me? 
Thank you

---

### Post by thefinn93 on 2010-11-16
bump...

---

