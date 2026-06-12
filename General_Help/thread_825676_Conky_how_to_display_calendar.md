---
title: "Conky: how to display calendar?"
date: 2008-06-11
forum: General Help
---

### Post by gaijindewanai on 2008-06-11
Is anyone know how to display a calendar in conky?
I can only display today's date, month and year.. but I want to display the current month calendar, is that possible? if it is possible, then how I can display it?

(as far as I know, there is no variable to display calendar in conky)

Thanx in advance.

---

### Post by squaregoldfish on 2008-06-11
Assuming conky itself can't do what you want, would the 'cal' command be of any use to you? I don't know it very well, but it will output the current month (or any other month) to stdout. You could call it in conky using
```

${exec cal}
```

Just an idea - if others have better suggestions, then please ignore me.

Steve.

---

### Post by kerry_s on 2008-06-11
> **squaregoldfish said:**
> Assuming conky itself can't do what you want, would the 'cal' command be of any use to you? I don't know it very well, but it will output the current month (or any other month) to stdout. You could call it in conky using
```

${exec cal}
```

Just an idea - if others have better suggestions, then please ignore me.

Steve.

use
```
${pre_exec cal}
```

the cal command only needs to be run once, no need for it to keep running after that, saves resources.

---

### Post by gaijindewanai on 2008-06-12
hmm.. it works but the date is scattered..
how can i align them so that it looks neat?

---

### Post by squaregoldfish on 2008-06-12
What font are you using? You'll need to be using a monospaced font for the text to line up properly.

Steve.

---

### Post by kerry_s on 2008-06-12
> **gaijindewanai said:**
> hmm.. it works but the date is scattered..
how can i align them so that it looks neat?

screenshot and post your conkyrc please.

---

### Post by MeKino on 2008-06-12
This is how I solved the problem:

[http://ubuntuforums.org/showthread.php?t=690753](http://ubuntuforums.org/showthread.php?t=690753)

---

### Post by gaijindewanai on 2008-06-13
hmmm...
i use:
${exec cal}

its work rite now as i used a single-spaced font (DeJavu ...)

but i have another question,
I can display last month and this month, or this month and next month on the same row, but I cant display last month and next month on the same row.. can u help me with the script?

---

### Post by kerry_s on 2008-06-13
```
${pre_exec cal -3}
```

---

### Post by gaijindewanai on 2008-06-13
hmm.. it displayed last month, this month and next month..

but what I wanted to be displayed is last month and next month only (without displaying this month).
is it possible?

---

### Post by kerry_s on 2008-06-13
open a terminal:
man cal

---

### Post by gaijindewanai on 2008-06-13
I opened it, yet it didn't show me how to display LAST MONTH and NEXT MONTH.

i know some script like these:
${exec cal -3 | cut -c01-22} <----------displaying LAST MONTH and THIS MONTH
${exec cal -3 | cut -c23-64} <----------displaying THIS MONTH and NEXT MONTH

what about LAST MONTH and NEXT MONTH (without THIS MONTH)? is that possible? :confused:
i have no idea bout it, n I hope there is somebody know bout it..

---

### Post by squaregoldfish on 2008-06-13
The cut command is selecting the characters that are specified by -c. By adding --complement, you can select everything *except* those characters.

Try this:

cal -3 |cut -c19-40 --complement

Steve.

---

### Post by gaijindewanai on 2008-06-13
Hei, thanx!!
It works.. its cool. this is my script:

${font DejaVu Sans Mono :size=5}${exec cal -3 | cut -c23-44 --complement}

thanx again!!

I attach the screenshot.

---

### Post by kerry_s on 2008-06-13
that's pretty spiffy. :)

why don't you go ahead and put your whole conkyrc in case some one else wants it?

---

### Post by gaijindewanai on 2008-06-13
here's my whole script:

```
background yes
font Snap.se:size=8
xftfont Snap.se:size=8
use_xft yes
xftalpha 0.1
update_interval 1.0
total_run_times 0
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no
minimum_size 210 5
maximum_width 210
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
${font LCDDisplayCapsSSi:style=Bold:pixelsize=54}${alignc}${time %H:%M:%S}${font Snap.se:size=8}
${alignr}${time %A, %e %B %G}

${font Aerial:style=Bold:pixelsize=12}CALENDAR${font Snap.se:size=8}${hr 1}
${font DejaVu Sans Mono :size=12}${exec cal}
${font DejaVu Sans Mono :size=6}${exec cal -3 | cut -c23-44 --complement}
${font Aerial:style=Bold:pixelsize=12}SYSTEM${font Snap.se:size=8} ${hr 1 }
User: $alignr$user_names
Computer: $alignr$nodename
$alignc$sysname $kernel ($machine)
Uptime: $alignr$uptime
Process: ${alignr}$processes ($running_processes running)
Load: ${alignr}$loadavg

Battery ${alignr}(${battery BAT1})
${battery_bar 4 BAT1}

CPU       ${alignc} ${freq}MHz / ${acpitemp}C ${alignr}(${cpu cpu1}%)
${cpubar 4 cpu1}
${cpugraph 0000ff 00ec00}

RAM ${alignr}$mem / $memmax ($memperc%)
${membar 4}

${font Aerial:style=Bold:pixelsize=12}FILE SYSTEM${font Snap.se:size=8}${hr 1}
HDD: ${alignr}${fs_used /} / ${fs_size /}
${fs_bar 4 /}

${font Aerial:style=Bold:pixelsize=12}CONNECTION${font Snap.se:size=8}${hr 1}
Down ${downspeed eth0} k/s ${alignr}Up ${upspeed eth0} k/s
${downspeedgraph eth0 25,107 cccccc ffffff} ${alignr}${upspeedgraph eth0 25,107 cccccc ffffff}
Total ${totaldown eth0} ${alignr}Total ${totalup eth0}
```

in my screenshot, I use my language (Indonesian) but I've translated here.

---

### Post by kerry_s on 2008-06-14
thanks, now i'm going to steal it and sell it on the conky black market. :evil: muhahaha
:lolflag:

just joking, your hard work will benefit all.

---

### Post by gaijindewanai on 2008-06-14
hahaha... no one's gonna buy my script, cuz it's posted here :KS n they can steal it too :lolflag: any way, if you steal it, it's okay.. but remember one thing: don't sell it to windows user, hahahaha...

Unlike Windows,
It's free, It's open source, It's Linux..

---

### Post by Pablo Pablovski on 2008-06-14
Thanks for a helpful thread, guys. I wonder if I could ask for a little help with my conky config. I've settled on just presenting the current month's calendar, but it doesn't line up with the rest of the conky output, being offset to the left (see attached). 
TIA, 
Paul

Conkyrc:

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
own_window no
own_window_hints undecorated,below,skip_taskbar
background no

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer right
use_xft yes

# Update interval in seconds
update_interval 8.0

# Minimum size of text area
minimum_size 200 5

# Draw shades?
draw_shades yes

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no

uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 8

# border margins
border_margin 4

# border width
border_width 1

# Default colors and also border colors, grey90 == #e5e5e5
default_color white
default_shade_color black
default_outline_color white

own_window_colour brown
own_window_transparent yes

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 10
gap_y 20

override_utf8_locale no
xftfont Terminus:size=8
xftalpha 0.8

# Line below inserts total GPU memory in bytes
# ${offset 200}${color slate grey}GPU Mem: ${color } ${execi 60 nvidia-settings -q VideoRam | grep  "Attr" | cut -c38-43} B

# ${offset 200}${color slate grey} CPU: ${color } ${acpitemp}C
# ${offset 200}${color slate grey} M/B: ${color } 

# stuff after 'TEXT' will be formatted on screen

TEXT

${offset 200}${color slate grey}${font Terminus:size=10}${time %a, } ${color }${time %e %B %G}
${offset 200}${color slate grey}${time %Z -  }${color }${time %H:%M:%S}${font}
**${offset 200}${font DejaVu Sans Mono:size=8}${color slate grey}${pre_exec cal | cut -c1-20}**
${offset 200}${font Terminus:size=8}
${offset 200}${color slate grey}Node: ${color }$nodename ${color slate grey} System: ${color }$sysname
${offset 200}${color slate grey} Kernel:${color }$kernel
${offset 200}${color slate grey} UpTime: ${color }$uptime

${offset 200}${color slate grey}CPU
${offset 200}${color slate grey} Model: ${color}${execi 3600 cat /proc/cpuinfo | grep 'model name' | cut -c14-46}
${offset 200}${color slate grey} Clock: ${color}${freq}MHz
${offset 200}${color slate grey} Usage:${color } $cpu%
${offset 200}${cpugraph 20,130 000000 ffffff}
${offset 200}${color slate grey}Fans /Temps
${offset 200}${color slate grey} CPU: ${color}${execi 30 sensors | grep "fan1" | cut -c10-20} /  ${acpitemp}C
${offset 200}${color slate grey} M/B: ${color}${execi 30 sensors | grep "fan3" | cut -c10-20} /  ${execi 60 sensors | grep "M/B" | cut -c15-16} C
${offset 200}${color slate grey} GPU: ${color } ${execi 60 nvidia-settings -q GPUCoreTemp | grep "Attr" | cut -c40-42} C

${offset 200}${color slate grey}Memory
${offset 200}${color slate grey} Used:  ${color } $memperc%  $mem / $memmax
${offset 200}${color #ddaa00}${membar 3,100}
${offset 200}${color slate grey} Swap: ${color }$swapperc%  $swap / $swapmax
${offset 200}${color #ddaa00}${swapbar 3,100}

${offset 200}${color slate grey}Processes: ${color }$processes ${color slate grey}Running:   ${color }$running_processes

${offset 200}${color slate grey}Highest CPU%
${offset 200}${color #ddaa00} ${top name 1}${top cpu 1}
${offset 200}${color lightgrey} ${top name 2}${top cpu 2}
${offset 200}${color lightgrey} ${top name 3}${top cpu 3}
${offset 200}${color lightgrey} ${top name 4}${top cpu 4}

${offset 200}${color slate grey}Highest MEM%
${offset 200}${color #ddaa00} ${top_mem name 1}${top_mem mem 1}
${offset 200}${color lightgrey} ${top_mem name 2}${top_mem mem 2}
${offset 200}${color lightgrey} ${top_mem name 3}${top_mem mem 3}
${offset 200}${color lightgrey} ${top_mem name 4}${top_mem mem 4}

${offset 200}${color slate grey}Filesystems
${offset 200}${color slate grey} kubuntu:  ${color }${fs_free /} of ${fs_size /} free
${offset 200}${color #ddaa00}${fs_bar 3,100 /}
${offset 200}${color slate grey} Windows:  ${color }${fs_free /mnt/Windows} of ${fs_size /mnt/Windows} free
${offset 200}${color #ddaa00}${fs_bar 3,100 /mnt/Windows}

${offset 200}${color slate grey} Music:    ${color }${fs_free /mnt/music} of ${fs_size /mnt/music} free
${offset 200}${color #ddaa00}${fs_bar 3,100 /mnt/music}
${offset 200}${color slate grey} Media:    ${color }${fs_free /mnt/media} of ${fs_size /mnt/media} free 
${offset 200}${color #ddaa00}${fs_bar 3,100 /mnt/media}

${offset 200}${color slate grey} Archive:   ${color }${fs_free /mnt/Archive} of ${fs_size /mnt/Archive} free
${offset 200}${color #ddaa00}${fs_bar 3,100 /mnt/Archive}
${offset 200}${color slate grey} Shared:    ${color }${fs_free /mnt/FAT32} of ${fs_size /mnt/FAT32} free
${offset 200}${color #ddaa00}${fs_bar 3,100 /mnt/FAT32}
${if_mounted /media/OneTouch}
${offset 200}${color slate grey} Ext. (Win):   ${color }${fs_free /media/OneTouch} of ${fs_size /media/OneTouch} free
${offset 200}${color #ddaa00}${fs_bar 3,100 /media/OneTouch}
${offset 200}${color slate grey} Ext. (Mac):    ${color }${fs_free /media/OneTouch Mac} of ${fs_size /media/OneTouch Mac} free
${offset 200}${color #ddaa00}${fs_bar 3,100 /media/OneTouch Mac}
${endif}
${offset 200}${color slate grey}Network
${offset 200}${color slate grey} Int: ${color }${addr eth0}${color slate grey} / Ext: ${color }${execi 7200 wget -O - [http://whatismyip.org/](http://whatismyip.org/) | tail}
${offset 200}${color slate grey} Up: ${color }${upspeedf eth0}kB/s ${color #ddaa00} Total: ${totalup eth0}${color} 
${offset 200}${upspeedgraph eth0 20,130 000000 ffffff}
${offset 200}${color slate grey} Down: ${color }${downspeedf eth0}kB/s ${color #ddaa00} Total: ${totaldown eth0}${color}
${offset 200}${downspeedgraph eth0 20,130 000000 ffffff}
${if_running amarokapp}${offset 200}${color slate grey}Now Playing
${offset 200}${color lawn green} "${execi 1 ~/.local/amarok.sh title}" 
${offset 200}${color } ${execi 1 ~/.local/amarok.sh artist}
${offset 200} ${execi 1 ~/.local/amarok.sh album}
${offset 200} ${color #ddaa00}${execibar 1 ~/.local/amarok.sh progress}
${endif}

```

---

### Post by kerry_s on 2008-06-14
try changing this:

```
# Minimum size of text area
minimum_size 200 5
```

there's to much space around your conky, after you adjust that you can probably lose the offset. to see it better just make your conky background a solid color to it or non-transparent.

---

### Post by Pablo Pablovski on 2008-06-14
Thanks for that, but it didn't fix the problem. 

I've tried various numbers in there, and even commented out the setting altogether. 

I've tried aligning that particular output to the right - no effect. I even tried "cal -3 | cut -c20-42" to see if cutting the middle chunk of the cal command output would make a difference.

---

### Post by Pablo Pablovski on 2008-06-14
> **kerry_s said:**
> try changing this:

```
# Minimum size of text area
minimum_size 200 5
```

there's to much space around your conky, after you adjust that you can probably lose the offset. to see it better just make your conky background a solid color to it or non-transparent.

You were right - I hadn't removed the offsets. Once I did that, and having changed the minimum_size back to default, everything lined up perfectly.

Thanks for your help - appreciated..

---

