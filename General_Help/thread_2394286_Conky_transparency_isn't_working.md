---
title: "Conky transparency isn't working"
date: 2018-06-15
forum: General Help
---

### Post by henrique-rj on 2018-06-15
Hi guys

How make my Conky transparency ?

I use the fowlling script in ~/.conkyrc

 ```
# Conky, a system monitor, based on torsmo
#
# Any original torsmo code is licensed under the BSD license
#
# All code written since the fork of torsmo is licensed under the GPL
#
# Please see COPYING for details
#
# Copyright (c) 2004, Hannu Saransaari and Lauri Hakkarainen
# Copyright (c) 2005-2010 Brenden Matthews, Philip Kovacs, et. al. (see AUTHORS)
# All rights reserved.
#
# This program is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
# You should have received a copy of the GNU General Public License
# along with this program.  If not, see <http://www.gnu.org/licenses/>.
#

alignment no
background no
border_width 1
cpu_avg_samples 2
default_color white
default_outline_color white
default_shade_color white
draw_borders no
draw_graph_borders yes
draw_outline no
draw_shades no
use_xft yes
xftfont DejaVu Sans Mono:size=10
gap_x 740
gap_y 60
minimum_size 5 5
net_avg_samples 2
no_buffers yes
double_buffer yes
out_to_console no
out_to_stderr no
extra_newline no
own_window yes
own_window_class Conky
own_window_type normal
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
stippled_borders 0
update_interval 1.0
uppercase no
use_spacer none
show_graph_scale no
show_graph_range no


TEXT
           ${color white}Conky - System Monitor
$hr
${color white}Uptime:$color $uptime
${color white}Frequency (in MHz):$color $freq
${color white}Frequency (in GHz):$color $freq_g
${color white}RAM:$color $mem / $memeasyfree / $memfree / $memmax
${color white}Swap:$color $swap/$swapmax - $swapperc% ${swapbar 4}
${color white}CPU Usage:$color $cpu% ${cpubar 4}
${color white}CPU Fan:$color ${hwmon 1 fan 1}rpm ${if_match ${hwmon 1 fan 1} < 1000} ${exec zenity --warning --text "Rotação CPU Fan abaixo do normal"} ${endif} Chassis Fan:$color ${hwmon 1 fan 2}rpm  ${if_match ${hwmon 1 fan 2} < 1000} ${exec zenity --warning --text "Rotação Chassis Fan abaixo do normal"} ${endif}
$hr
${color white}UPS APC BE600N-BR: 
Charge:$color ${apcupsd localhost 3551} ${apcupsd_charge}%  Load:${apcupsd_load}% ${if_match ${apcupsd_load} > 25} ${exec zenity --warning --text "Consumo do PC acima de 25% do Nobreak"} ${endif} ${apcupsd_loadbar 4}
Inp Volt: ${apcupsd_linev}V   Time Left: ${apcupsd_timeleft}min
Reason: ${apcupsd_lastxfer}
$hr
${color white}Voltages: 
Vcore:${hwmon 1 vol 0}V ${if_match ${hwmon 1 vol 0} < 1} ${exec zenity --warning --text "Tensão Vcore abaixo do normal"} ${endif} ${if_match ${hwmon 1 vol 0} > 1} ${exec zenity --warning --text "Tensão Vcore acima do normal"} ${endif} NB:${hwmon 1 vol 1}V   ${if_match ${hwmon 1 vol 1} < 1} ${exec zenity --warning --text "Tensão NB abaixo do normal"} ${endif}  ${if_match ${hwmon 1 vol 1} > 1} ${exec zenity --warning --text "Tensão NB acima do normal"} ${endif} +3,3V:${hwmon 1 vol 2}V  ${if_match ${hwmon 1 vol 2} < 3} ${exec zenity --warning --text "Tensão +3,3V abaixo do normal"} ${endif} ${if_match ${hwmon 1 vol 2} > 3} ${exec zenity --warning --text "Tensão +3,3V acima do normal"} ${endif} 
+5,0V:${hwmon 1 vol 3}V ${if_match ${hwmon 1 vol 3} < 3} ${exec zenity --warning --text "Tensão +5,0V abaixo do normal"} ${endif} ${if_match ${hwmon 1 vol 3} > 3} ${exec zenity --warning --text "Tensão +5,0V acima do normal"} ${endif} +12,0V:${hwmon 1 vol 4}V ${if_match ${hwmon 1 vol 4} < 3} ${exec zenity --warning --text "Tensão +12,0V abaixo do normal"} ${endif} ${if_match ${hwmon 1 vol 4} > 3} ${exec zenity --warning --text "Tensão +12,0V acima do normal"} ${endif} DRAM:${hwmon 1 vol 5}V ${if_match ${hwmon 1 vol 5} < 1} ${exec zenity --warning --text "Tensão DRAM abaixo do normal"} ${endif} ${if_match ${hwmon 1 vol 5} > 2} ${exec zenity --warning --text "Tensão DRAM acima do normal"} ${endif}
LDT:${hwmon 1 vol 6}V ${if_match ${hwmon 1 vol 6} < 1} ${exec zenity --warning --text "Tensão LDT abaixo do normal"} ${endif} ${if_match ${hwmon 1 vol 6} > 1} ${exec zenity --warning --text "Tensão LDT acima do normal"} ${endif}   3VSB:${hwmon 1 vol 7}V  ${if_match ${hwmon 1 vol 7} < 2} ${exec zenity --warning --text "Tensão 3VSB abaixo do normal"} ${endif} ${if_match ${hwmon 1 vol 7} > 3} ${exec zenity --warning --text "Tensão 3VSB acima do normal"} ${endif}  Vbat:${hwmon 1 vol 8}V ${if_match ${hwmon 1 vol 8} < 3} ${exec zenity --warning --text "Tensão Vbat abaixo do normal"} ${endif} ${if_match ${hwmon 1 vol 8} > 3} ${exec zenity --warning --text "Tensão Vbat acima do normal"} ${endif}
$hr
${color white}Temperatures:
CPU:$color ${hwmon 1 temp 1}°C   NB:$color ${hwmon 1 temp 2}°C   SB:$color ${hwmon 1 temp 3}°C
HDD:$color ${execi 5 hddtemp /dev/sda}
$hr
${color white}File systems:
 / $color${fs_used /}/${fs_size /} ${fs_bar 6 /}
${color white}Networking:
Up:$color ${upspeed eth0} ${color white} - Down:$color ${downspeed eth0}
$hr
${color white}Name               PID    CPU%   MEM%
${color white} ${top name 1} ${top pid 1} ${top cpu 1} ${top mem 1} 
${color white} ${top name 2} ${top pid 2} ${top cpu 2} ${top mem 2}
${color white} ${top name 3} ${top pid 3} ${top cpu 3} ${top mem 3}
${color white} ${top name 4} ${top pid 4} ${top cpu 4} ${top mem 4}
```

I have try the fowlling lines in ~/.conkyrc but without success:

```
own_window_transparent yes
own_window_argb_visual yes
own_window_argb_value 0
own_window_type override
```

My system is Kubuntu 14.04 ( trusty ) KDE Plasma 64 ( monitor VESA ).

Look my Conky in desktop image:

[IMG]https://s33.postimg.cc/4bn9423db/conky1.png[/IMG]

Thanks for any help.

---

### Post by henrique-rj on 2018-06-15
Solved !!!

It  was just go in the settings and effects of the desktop, go in advanced,  select composition type, OpenGL 3.1 (was XRender) and apply. Then I edited ~ / .conkyrc by adding the lines below and it finally became transparent.

own_window_transparent yes
own_window_argb_visual yes
own_window_argb_value 0

Now the transparency it working very well !!!

Done

---

### Post by again? on 2018-06-15
I see you're using xclock.
As you have installed conky you may want to try this conky analog clock.
[https://ubuntuforums.org/showthread.php?t=2391975&p=13767360#post13767360](https://ubuntuforums.org/showthread.php?t=2391975&p=13767360#post13767360)
You can customize the size and colour of various elements in the clock3.lua file.

---

### Post by henrique-rj on 2018-06-16
> **guber2 said:**
> I see you're using xclock.
As you have installed conky you may want to try this conky analog clock.
[https://ubuntuforums.org/showthread.php?t=2391975&p=13767360#post13767360](https://ubuntuforums.org/showthread.php?t=2391975&p=13767360#post13767360)
You can customize the size and colour of various elements in the clock3.lua file.

Very good

Thanks !!!

O:)

---

### Post by mörgæs on 2018-06-16
Please mark the thread solved using Thread Tools. It will help other users with a similar question.

---

### Post by henrique-rj on 2018-06-16
> **mörgæs said:**
> Please mark the thread solved using Thread Tools. It will help other users with a similar question.

Done !!!

---

