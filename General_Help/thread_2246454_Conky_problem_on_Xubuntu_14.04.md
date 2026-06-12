---
title: "Conky problem on Xubuntu 14.04"
date: 2014-09-30
forum: General Help
---

### Post by lazar-zivadinovic on 2014-09-30
Hi all,

i have problem with conky on xubuntu 14.04 LTS x64.

This code worked for about 2-3 months, but one day, after updating it just stoped. I check conky site for syntax changes and i changed 2-3 lines with new syntx. but still nothing.

this is output of console run
```
lazar@lazar-XUB:~$ conky
Conky: desktop window (1c00003) is subwindow of root window (c0)
Conky: window type - override
Conky: drawing to created window (0x3a00001)
Conky: drawing to double buffer

```

and just stays there like that.

on screenshot you can see what does it loke like when i run conky (just black cube).


This is my .conkyrc:

```
# Use Xft?
use_xft yes
xftfont AvantGarde:size=9

# Update interval in seconds
update_interval 1

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window  yes
own_window_transparent yes
own_window_type override
own_window_hints undecorate,sticky,skip_taskbar,skip_pager 

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 768 5

maximum_width 250

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Stippled borders?
stippled_borders 0

# border margins
border_outer_margin 5

# border width
border_width 1

# Default colors and also border colors
#default_color 303030
#default_shade_color white
#default_outline_color black
#own_window_colour 262524

# Text alignment, other possible values are commented
#alignment top_left
#alignment top_right
alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 10
gap_y 100

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# number of cpu samples to average
# set to 1 to disable averaging
cpu_avg_samples 2

# number of net samples to average
# set to 1 to disable averaging
net_avg_samples 2

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale yes

# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer right

#COLORS
color1 a4a4a4
color3 9CFC4D
color2 94D100 



TEXT
${color1}${hr 1}
${color1}${alignc 20}${font DotMatrix:size=14}${time %H:%M:%S}${font}${color1}
${hr 1}
|
${color3}o ${color1}--${color3} o${color2} DATE
${color1}|${offset 2}    ${color1}|${color1}
|     ${color3}o ${color1}---${color3} o${color2} Day:${color1}................${time %A}
|             ${color3} o${color2} Date:${color1}...............${time %d/%m/%y }
|
${color3}o ${color1}--${color3} o${color2} SYS${color1}
|${offset 2}    ${color1}|
|     ${color3}o ${color1}---${color3} o${color2} OS:${color1}...................${offset 1}Xubuntu 14.04.1 LTS
|             ${color3} o${color2} Kernel:${color1}............${offset 1}$kernel
|             ${color3} o${color2} Up:${color1}...................${offset 1}$uptime
|             ${color3} o${color2} Ram:${color1}................$mem/ $memmax
|             ${color3} o${color2} Model:${color1}............${execi 1000 cat /proc/cpuinfo | grep 'model name' | uniq | cut -c 32-49}
|             ${color3} o${color2} CPU1:${color1}...............${cpu cpu1}%
|             ${color3} o${color2} CPU2:${color1}...............${cpu cpu2}%
|             ${color3} o${color2} CPU-T:${color1}..............${execi 30 sensors |grep 'Core 0' | cut -c18-24}               
|             ${color3} o${color2} Battery:${color1}............${battery_percent}%
|             ${color3} o${color2} Time left:${color1}..........${battery_time}
|
${color3}o ${color1}--${color3} o${color2} DISK${color1}
|${offset 2}    ${color1}|
|     ${color3}o ${color1}---${color3} o${color2} Root:${color1}................${fs_used /}/ ${fs_size /}
|             ${color3} o${color2} Data:${color1}...............${fs_used /media/lazar/data_p}/ ${fs_size /media/lazar/data_p}
|
${color3}o ${color1}--${color3} o${color2} NET${color1}
${offset 2}       ${color1}|
        ${color3}o ${color1}---${color3} o${color2} Public:${color1}...............${execi 300 wget -qO- http://ipecho.net/plain ; echo}
               ${color3} o${color2} Local_rl:${color1}...........${addr wlan0}
               ${color3} o${color2} Local_ath:${color1}........${addr wlan1}
               ${color3} o${color2} Up_rl:${color1}......................${upspeed wlan0}/s
               ${color3} o${color2} Down_rl:${color1}................${downspeed wlan0}/s
               ${color3} o${color2} Up_ath:${color1}......................${upspeed wlan1}/s
               ${color3} o${color2} Down_ath:${color1}................${downspeed wlan1}/s


```

---

### Post by CantankRus on 2014-10-01
Your conky appears to be waiting for the wget command in your "NET" section to complete.

When tested in terminal I cannot connect to [http://ipecho.net/plain](http://ipecho.net/plain) 
[http://ipecho.net](http://ipecho.net) is still up though. 
```
[COLOR="#008000"]glen@Trusty:~$[/COLOR] **wget -O- --tries=3 --connect-timeout=10 http://ipecho.net/plain**
--2014-10-01 13:25:50--  http://ipecho.net/plain
Resolving ipecho.net (ipecho.net)... 146.255.36.1
Connecting to ipecho.net (ipecho.net)|146.255.36.1|:80... failed: Connection timed out.
Retrying.

--2014-10-01 13:26:01--  (try: 2)  http://ipecho.net/plain
Connecting to ipecho.net (ipecho.net)|146.255.36.1|:80... failed: Connection timed out.
Retrying.

--2014-10-01 13:26:13--  (try: 3)  http://ipecho.net/plain
Connecting to ipecho.net (ipecho.net)|146.255.36.1|:80... failed: Connection timed out.
**Giving up**.
```

Try replacing this section...
```
${execi 300 wget -qO- http://ipecho.net/plain ; echo}
```
with
```
${execi [COLOR="#FF0000"]3600[/COLOR] wget -qO- --tries=3 --connect-timeout=10 icanhazip.com}
```

This will check your WAN ip address [COLOR="#FF0000"]every hour[/COLOR] using **[http://icanhazip.com](http://icanhazip.com)**. It will try to connect 3 times for 10 seconds each try.

---

### Post by lazar-zivadinovic on 2014-10-01
Ok. Now it's working. Thanks a lot, dude.

---

