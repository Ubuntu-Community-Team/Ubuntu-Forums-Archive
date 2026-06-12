---
title: "Issues trying to get Temps working in my Conky config"
date: 2013-06-20
forum: General Help
---

### Post by xentrix1220 on 2013-06-20
Ok so I have been searching around and it looks like I need lm-sensors installed and I do and also acpi and shows in terminal when i type sensors. However I  can not get this to work in conky any help would be much appreciated.

below is my conky config

[IMG]http://i.imgur.com/zlpSpro.jpg[/IMG]

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
# -- Pengo (conky@pengo.us)
#

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
own_window_hints below

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer yes
use_xft no

# Update interval in seconds
update_interval 3.0

#Maximum Width of Window
maximum_width 320

# Minimum size of text area
# minimum_size 250 5

# Draw shades?
draw_shades no

# Text stuff
draw_outline no # #4e9a06mplifies text if yes
draw_borders no
font arial
uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 3

# border margins
border_margin 5

# border width
border_width 6

# Default colors and also border colors, grey90 == #e5e5e5
default_color FFFFCC

own_window_colour brown
own_window_transparent yes
# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 10
gap_y 10

# stuff after â€˜TEXTâ€™ will be formatted on screen

TEXT
$color
${color CC9900}SYSTEM ${hr 2}$color
$nodename $sysname $kernel on $machine

${color CC9900}CPU ${hr 2}$color
Intel i7 3.4 Ghz

Total CPU: ${cpu cpu0}%
${color CC0000}${cpubar}$color
${cpugraph 000000 597DB2}
Core 1: ${freq 1} MHz        Temprature: $color ${exec sensors|grep 'Core0' |awk '{print $3}'}
${cpu cpu1}% ${color CC0000}${cpubar cpu1}$color
Core 2: ${freq 2} MHz        Temprature: $color ${exec sensors|grep 'Core1'|awk '{print $3}'}
${cpu cpu2}% ${color CC0000}${cpubar cpu2}$color
Core 3: ${freq 3} MHz        Temprature: $color ${exec sensors|grep 'Core1'|awk '{print $3}'}
${cpu cpu3}% ${color CC0000}${cpubar cpu3}$color
Core 4: ${freq 4} MHz        Temprature: $color ${exec sensors|grep 'Core1'|awk '{print $3}'}
${cpu cpu4}% ${color CC0000}${cpubar cpu4}$color
Core 5: ${freq 5} MHz        Temprature: $color ${exec sensors|grep 'Core1'|awk '{print $3}'}
${cpu cpu5}% ${color CC0000}${cpubar cpu5}$color
Core 6: ${freq 6} MHz        Temprature: $color ${exec sensors|grep 'Core1'|awk '{print $3}'}
${cpu cpu6}% ${color CC0000}${cpubar cpu6}$color
Core 7: ${freq 7} MHz        Temprature: $color ${exec sensors|grep 'Core1'|awk '{print $3}'}
${cpu cpu7}% ${color CC0000}${cpubar cpu7}$color
Core 8: ${freq 8} MHz        Temprature: $color ${exec sensors|grep 'Core1'|awk '{print $3}'}
${cpu cpu8}% ${color CC0000}${cpubar cpu8}$color
NAME            PID	 CPU%  	MEM%
${color CCFFFF}${top name 1} ${top pid 1} ${top cpu 1} ${top mem 1}
${top name 2} ${top pid 2} ${top cpu 2} ${top mem 2}
${top name 3} ${top pid 3} ${top cpu 3} ${top mem 3}
${top name 4} ${top pid 4} ${top cpu 4} ${top mem 4}$color

${color CC9900}MEMORY ${hr 2}$color
RAM Used: ${mem}	RAM Free: ${memfree}/ ${memmax}
 RAM: $memperc%  ${color FF6600} ${membar 6}$color
Swap: $swapperc%   ${color FF6600} ${swapbar 6}$color

${color CC9900}DISK ${hr 2}$color
sdc5 ${fs_type} (Root): ${fs_free_perc /}% ${color FFFF33} ${fs_bar 6 /}$color
sda1 ext4 (Filez): ${fs_free_perc /media/Filez}% ${color FFFF33} ${fs_bar 6 /media/Filez}$color

${color CC9900}NETWORK (${addr wlan0}) ${hr 2}$color
Down: $color${downspeed wlan0} k/s ${alignr}Up: ${upspeed wlan0} k/s
${downspeedgraph eth1 25,140 000000 ff0000} ${alignr}${upspeedgraph wlan0
25,140 000000 00ff00}$color
Total: ${totaldown wlan0} ${alignr}Total: ${totalup wlan0}
Inbound: ${tcp_portmon 1 32767 count} Outbound: ${tcp_portmon 32768
61000 count}${alignr}Total: ${tcp_portmon 1 65535 count}

${color CC9900}LOGGING ${hr 2}$color
${color FFF000}${execi 30 tail -n3 /var/log/ufw.log | fold -w50}$color

```

---

### Post by Habitual on 2013-06-20
open a terminal and input this ... 
```
sensors
``` is there any output? show it to us?

---

### Post by xentrix1220 on 2013-06-20
Yes I do get an output for sensors:

> lol@lol-PC:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +27.8°C  (crit = +106.0°C)
temp2:        +29.8°C  (crit = +106.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +45.0°C  (high = +87.0°C, crit = +105.0°C)
Core 0:         +42.0°C  (high = +87.0°C, crit = +105.0°C)
Core 1:         +39.0°C  (high = +87.0°C, crit = +105.0°C)
Core 2:         +32.0°C  (high = +87.0°C, crit = +105.0°C)
Core 3:         +45.0°C  (high = +87.0°C, crit = +105.0°C)


---

### Post by stinkeye on 2013-06-21
sensors output shows you need to grep '**Core 0**', not '**Core0**'

Eg
The line in your conky...
```
${exec sensors|grep 'Core0' |awk '{print $3}'}
```

should be (space between **Core** and **0**)
```
${exec sensors | grep 'Core 0' | awk '{print $3}' | cut -c2-}
```
The cut command removes the "+" sign.

Test in terminal....
```
sensors | grep 'Core 0' | awk '{print $3}' | cut -c2-
```

Alter the other lines accordingly.

---

### Post by xentrix1220 on 2013-06-21
Awesome! wow amazing how something so small can make a big difference thank you! Anyways I just noticed it only goes up to core 3 is there anyway to get the temps for the rest of the cores?

---

### Post by stinkeye on 2013-06-21
> **xentrix1220 said:**
> Awesome! wow amazing how something so small can make a big difference thank you! Anyways I just noticed it only goes up to core 3 is there anyway to get the temps for the rest of the cores?
If there not being shown in sensors, I dont know.

---

### Post by xentrix1220 on 2013-06-21
ohwell at least I got some thank you so much

---

