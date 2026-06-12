---
title: "Conky RAM Sensor wrong??"
date: 2014-10-25
forum: General Help
---

### Post by dan143 on 2014-10-25
My conkys RAM sensor is not giving a correct reading, it currently reads at around 90%+ when according to the inbuilt system monitor its only at 15%.

[ATTACH=CONFIG]257488[/ATTACH]
(Screenshot of conky)

```
background yes
use_xft yes
xftfont Monospace:size=8
xftalpha 1
update_interval 1.0
total_run_times 0
own_window yes
own_window_transparent yes
own_window_type normal
own_window_argb_visual yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
minimum_size 200 200
maximum_width 190
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders yes
default_color 03E5E5
default_shade_color 1EA2C7
default_outline_color white
color3 979797
color4 AntiqueWhite4
gap_x 10
gap_y 30
no_buffers no
alignment top_right
uppercase no
cpu_avg_samples 2
override_utf8_locale no
text_buffer_size 2048
max_user_text 65000
##############################################
#  Output
##############################################
TEXT

#Sector 1: "Date", Time, Date, Year
${font monospace:bold:size=12}DATE ${hr 2}
${font monospace:size=29}${alignc}${time %H:%M:%S}${font}


${font monospace:bold:size=12}${alignc}${time %a | %d %b | Wk%V}

${voffset 4}${alignc 7}${execpi 60 VinDSL_Cal= date +'${offset 6}%Y'}

#Sector 2: "System", Kernel, Host_Name, Uptime
${font monospace:bold:size=12}SYSTEM ${hr 2}
${font monospace:normal:size=8}$sysname $kernel $alignr $machine
#Host:$alignr$nodename
${font monospace:bold:size=8}Host:${font monospace:normal:size=8}THiNKPAD Ron SL510
Uptime:$alignr$uptime

#Sector 4: "i5 Processor 3320", Core Frequency, Core temp, CPU1&2 gauge
${font monospace:bold:size=12}CPU - Core i5 ${hr 2}
${font monospace:bold:size=8}${cpugraph cpu0 03E5E5 03E5E5}
${font monospace:normal:size=8}Core frequency $color $alignr ${freq_g (1)} GHz
Core 1 temp: $alignr ${hwmon 0 temp 1} C
CPU1: ${cpu cpu1}% ${cpubar cpu1}
CPU2: ${cpu cpu2}% ${cpubar cpu2}
CPU3: ${cpu cpu3}% ${cpubar cpu3}
CPU4: ${cpu cpu4}% ${cpubar cpu4}
#${cpugraph cpu1}
#${cpugraph cpu2}
#${cpugraph cpu3}
#${cpugraph cpu4}

#Sector 5: "HDD & RAM", RAM use gauge, HDD use gauge
${font monospace:bold:size=12}HDD & RAM ${hr 2}
${font monospace:normal:size=8}RAM $alignc $mem / $memmax $alignr $memperc%
$membar

${font monospace:normal:size=8}HDD $alignc ${fs_used /} / ${fs_size /} $alignr ${fs_used_perc /}%
${fs_bar /}

#Sector 6: "Network", Wi-Fi ID, Signal, IP address, Upload/Download graph
${font monospace:bold:size=12}NETWORK ${hr 2}
${font monospace:normal:size=8}IP address: $alignr ${addr eth0}
${downspeedgraph eth0}
${font monospace:normal:size=8}Down:   (Tot: ${totaldown eth0}) $alignr${downspeed eth0}/s
#${upspeedgraph eth0}
#${font monospace:normal:size=8}Up:       (Tot: ${totalup eth0}) $alignr ${upspeed eth0}/s


```

And that is the conky code i'm currently using.

I have installed all packages for conky and the lm-sensors package and ran the sudo-detect command and answered yes to everything.

Any help will be appreciated =)

---

### Post by vasa1 on 2014-10-25
I'm a conky noob but shouldn't things like```

#Sector 5: "HDD & RAM", RAM use gauge, HDD use gauge
${font monospace:bold:size=12}HDD & RAM ${hr 2}
${font monospace:normal:size=8}RAM $alignc $mem / $memmax $alignr $memperc%
$membar
```have ${mem}, ${memperc}%, ${membar}? In other words, aren't the curly brackets important?

---

### Post by dan143 on 2014-10-26
> I'm a conky noob but shouldn't things like

So am I :P, but if I put brackets around these variables they brake and actually displays the bracket in the output =/ conky uses the lua programming language which I'm unfamiliar with so I have no idea :P

---

