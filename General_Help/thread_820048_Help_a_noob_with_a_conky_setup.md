---
title: "Help a noob with a conky setup?"
date: 2008-06-05
forum: General Help
---

### Post by 9sillyunix9 on 2008-06-05
I was looking around and stumbled on Conky. I installed it from the repo and would like to customize it but I am a noob and am lost as to where to start.

Could someone help point me in the right direction as to how to load some of the configs from [[[http://conky.sourceforge.net/screenshots.html]("http://conky.sourceforge.net/screenshots.html")]].

TIA

---

### Post by easybake on 2008-06-05
Try this out [http://ubuntuforums.org/showthread.php?t=205865&highlight=conky]("http://ubuntuforums.org/showthread.php?t=205865&highlight=conky")

My screenshot: [http://img293.imageshack.us/my.php?image=screenshotzc8.png]("http://img293.imageshack.us/my.php?image=screenshotzc8.png")

My .conkyrc
> 
use_spacer yes

#background yes

font freesans:size=8
xftfont freesans:size=8
use_xft yes

xftalpha 1

update_interval 5.0

own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

double_buffer yes

minimum_size 260 5
maximum_width 155

color0 0033ff
color1 cbcbcb
color2 a6a6a6
color3 757575
color4 515151
color5 ffffff

draw_shades yes

draw_outline no # amplifies text

draw_borders no
draw_graph_borders no

default_color grey90
default_shade_color black
default_outline_color DarkGrey

#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

gap_x 10
gap_y 35

no_buffers yes

uppercase no

# stuff after 'TEXT' will be formatted on screen

TEXT
${color5}${font freesans:style=Bold:pixelsize=55}$alignc${time %I:%M}${font freesans:size=8}

${color0}CPU:$color $alignr${color0}$cpu%
${cpugraph 20,155 cbcbcb 515151}
${color0}PROCESSES:$alignr CPU%
${color1}${top name 1} $alignr${top cpu 1}
${color2}${top name 2}$alignr${top cpu 2}
${color3}${top name 3}$alignr${top cpu 3}
${color4}${top name 4}$alignr${top cpu 4}
${color0}RAM:${color0}$alignr$memperc%
${color4}${membar 7,155}
${color0}HD: ${color2}${fs_used /}$alignr${fs_free /}
${color4}${fs_bar 7,155}
${color0}UP: ${color2}${upspeed eth0}k/s$alignr${color0}DOWN: ${color2}${downspeed eth0}k/s 
${upspeedgraph eth0 20,75 cbcbcb 757575}$alignr${downspeedgraph eth0 20,75 757575 515151}
${color2}${totalup eth0} $alignr${totaldown eth0}

${color0}${font freesans:size=10}Mundelein, IL$font$alignr${color0}${offset -12}${execi 3600 python conkyforecast.py --location=USIL0823 --datatype=DW --startday=1 -w}
${color2}${font freesans:size=7}${execi 3600 python conkyforecast.py --location=USIL0823 --datatype=CC --startday=0}$font$alignr${color3}${execi 3600 python conkyforecast.py --location=USIL0823 --datatype=HT --startday=1 -i -u}/${execi 3600 python conkyforecast.py --location=USIL0823 --datatype=LT --startday=1 -i -u}
$alignr${color0}${offset -12}${execi 3600 python conkyforecast.py --location=USIL0823 --datatype=DW --startday=2 -w}
$alignr${color3}${execi 3600 python conkyforecast.py --location=USIL0823 --datatype=HT --startday=2 -i -u}/${execi 3600 python conkyforecast.py --location=USIL0823 --datatype=LT --startday=2 -i -u}
$alignr${color0}${offset -12}${execi 3600 python conkyforecast.py --location=USIL0823 --datatype=DW --startday=3 -w}
$alignr${color3}${execi 3600 python conkyforecast.py --location=USIL0823 --datatype=HT --startday=3 -i -u}/${execi 3600 python conkyforecast.py --location=USIL0823 --datatype=LT --startday=3 -i -u}
${voffset -42}${font freesans:style=Bold:size=36}${color2}${execi 3600 python conkyforecast.py --location=USIL0823 --datatype=HT -i -u}${offset -18}${font freesans:size=13}/${color3}${execi 3600 python conkyforecast.py --location=USIL0823 --datatype=LT -i -u}

You'll need a python weather script if you want to add weather. [http://ubuntuforums.org/showthread.php?t=760527]("http://ubuntuforums.org/showthread.php?t=760527")

---

### Post by 9sillyunix9 on 2008-06-06
Thanks for the info. I was able to get conky running and configure it as well. It takes some time to get it where I want it to be (not there yet) but hopefully soon it will be polished and shiney.

I appreciate your help Easybake.

---

