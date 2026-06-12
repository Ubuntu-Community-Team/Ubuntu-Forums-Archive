---
title: "weird conky output"
date: 2015-09-29
forum: General Help
---

### Post by jeremiah9 on 2015-09-29
hi everyone, i was wondering if someone could help me figure out why my conky is displaying more numbers then im telling it to display . So for the script im using a slightly tweaked version of the parted magic one. The issue is the cpu temp. i specified it to us the info from "lmsensors" and to read from the 16th spot in the command line to the 19th. PS sorry if im not using the right lingo. im learning here as i go lol. AS u can see in the screen shot cpu temp is 35c. but now the weird part. why is there that 28.5 later on. my goal was to have temp and vcore next to each other but that 28.5 is spaced out after the 35 causing vcore to be under cpu temp? basically where on earth is that 28.5 coming from? 
```

# X font when Xft is disabled, you can pick one with program xfontsel
#font 5x7
#font 6x10
#font 7x10
#font 8x13
#font 9x15
#font *mintsmild.se*
#font -*-*-*-*-*-*-34-*-*-*-*-*-*-*


# Use Xft?
use_xft yes


# Xft font when Xft is enabled
xftfont Bitstream Vera Sans Mono:size=10


# Text alpha when using Xft
xftalpha 0.8


# Print everything to stdout?
# out_to_console no


# Print everything to console?
# out_to_console no


# Update interval in seconds
update_interval 1


# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0


#own_window_title Parted Magic - conky


# Create own window instead of using desktop (required in nautilus)
own_window yes


# If own_window is yes, you may use type normal, desktop or override
own_window_type normal


# Use pseudo transparency with own_window?
own_window_transparent no


# If own_window_transparent is set to no, you can set the background colour here
own_window_colour 000000


# If own_window is yes, these window manager hints may be used
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
#own_window_hints below,skip_taskbar,skip_pager


# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes


# Minimum size of text area
minimum_size 220 100


# Draw shades?
draw_shades yes


# Draw outlines?
draw_outline no


# Draw borders around text
draw_borders no


# Draw borders around graphs
draw_graph_borders yes


# Stippled borders?
stippled_borders 4


# border margins
border_inner_margin 4


# border width
border_width 1


# Default colors and also border colors
default_color white
default_shade_color black
default_outline_color black


# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right
#alignment none


# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 25
gap_y 25


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
override_utf8_locale no


# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer none


own_window_argb_value 64
own_window_argb_visual yes
TEXT
${color goldenrod}Hostname: $nodename
${color goldenrod}Linux Kernel: $kernel
${color goldenrod}CPU Details:  $machine, $freq(MHz)


${color}CPU History:  ${color darkgreen}${cpugraph 30,0 0000ff 00ff00}
${color}CPU Usage:${color magenta2} $cpu% ${cpubar 11,0}


${color}RAM Usage:${color green} $mem ($memperc%) ${membar 11,0}
${color}Available RAM:${color green} $memmax


${color}CPU Temp: ${execi 1 sensors | grep 'temp1' | cut -c 16-19} ${color}Vcore: ${execi 1 sensors | grep 'in0' | cut -c 16-21}
${color}CPU Fan speed: ${execi 1 sensors | grep 'fan1' | cut -c 14-21}
$color$stippled_hr
$alignc${color}Processes:$color $processes  ${color grey}Running:$color $running_processes
$alignc${color}(top 5 sorted by CPU usage)
${color goldenrod} NAME              PID    CPU%   MEM%
${color} ${top name 1} ${top pid 1} ${top cpu 1} ${top mem 1}
${color} ${top name 2} ${top pid 2} ${top cpu 2} ${top mem 2}
${color} ${top name 3} ${top pid 3} ${top cpu 3} ${top mem 3}
${color} ${top name 4} ${top pid 4} ${top cpu 4} ${top mem 4}
${color} ${top name 5} ${top pid 5} ${top cpu 5} ${top mem 5}


$alignc${color}(top 5 sorted by MEM usage)
${color goldenrod} NAME              PID    CPU%   MEM%
${color} ${top_mem name 1} ${top_mem pid 1} ${top_mem cpu 1} ${top_mem mem 1}
${color} ${top_mem name 2} ${top_mem pid 2} ${top_mem cpu 2} ${top_mem mem 2}
${color} ${top_mem name 3} ${top_mem pid 3} ${top_mem cpu 3} ${top_mem mem 3}
${color} ${top_mem name 4} ${top_mem pid 4} ${top_mem cpu 4} ${top_mem mem 4}
${color} ${top_mem name 5} ${top_mem pid 5} ${top_mem cpu 5} ${top_mem mem 5}
$color$stippled_hr
$alignc${color}Download Speed: $downspeed
$alignc${color}System Uptime:${color DarkOrange1} $uptime

```[ATTACH=CONFIG]264740[/ATTACH]

EDIT* add comp info
AMD 1100T BE CPU
gigabyte 990xa-ud3 rev.1 mobo
amd HD7870ghz oc edition
corsair cheapy 4gig stick of ram

---

### Post by deadflowr on 2015-09-29
You know you need to specify just one temp1 output.
You have two.
Perhaps sed will help.
try adding this pipe between grep and cut
```
sed -n 1p
```
That should output only the first temp1 output.

---

### Post by CantankRus on 2015-09-29
Because, as in my sensors output, you have 2 "temp1" outputs that you are grepping.
You can specify the sensor to use.
ie
```
sensors **it8720-isa-0228** | grep 'temp1' | cut -c 16-19
```
The order the sensors load when running the "sensors" command can vary with each boot
so it is best to specify a sensor to use.

---

### Post by jeremiah9 on 2015-09-30
thank you for the help guys! when i get home from work ill update with the results!

---

### Post by jeremiah9 on 2015-09-30
SOLVED!! thanks guys, i appreciate it very much! so i put in what u said deadflowr. I'll be honest tho, i didnt know what "adding this pipe" ment lol so i just put it beside the words "temp 1" and it didnt work but then i gave it its own "|" and bam. Now could you guys explain what exactly adding sed -n 1p did so i can learn and what exactly was the problem? (so i dont have to bug ppl) it sounds like "temp 1" has 2 temps? how is that if in the command line it only shows one temp? thanks again to you both!
[ATTACH=CONFIG]264762[/ATTACH]

---

