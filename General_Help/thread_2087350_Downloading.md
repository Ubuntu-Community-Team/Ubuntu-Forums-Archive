---
title: "Downloading"
date: 2012-11-23
forum: General Help
---

### Post by poolhustler on 2012-11-23
Is there a way how to check how much I download from the internet on Ubuntu?
I have a limited amount that I can download every month and I would like to keep track of it. I have a mobile broadband-usb-stick and I cant find where to check those things.

Thanks

---

### Post by socialdtk on 2012-11-23
Your provider will usually make that information available via your user account on their website. I think it's probably a good idea to occasionally check there to see the "official numbers". It also allows you to track usage across multiple devices.

If you must track usage using your local machine I found this on the forums posted by stinkeye ( [http://ubuntuforums.org/showthread.php?t=1965123](http://ubuntuforums.org/showthread.php?t=1965123) ). I just installed and it seems to work very well.

Save this as .conkyrc in your home folder.

Code:
> 
font Sans Seriff:size=9
xftfont DejaVu Sans Mono:bold:size=10
use_xft yes
xftalpha 0.8
update_interval 1.0
total_run_times 0
own_window yes
own_window_type override
own_window_transparent no
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
draw_shades yes
draw_outline no
draw_borders no
draw_graph_borders no
minimum_size 300
maximum_width 300
default_color 919FAA
default_shade_color 333333
default_outline_color 00ff00
alignment br
gap_x 10
gap_y 10
no_buffers yes
cpu_avg_samples 2
override_utf8_locale yes
uppercase no # set to yes if you want all text to be in uppercase
use_spacer right

# colours
#off white
color1 BDAC88

# cream
color2 D2B16A

# cyan
#color3 08A1A1

# bluemoon
color3 919FAA

# yellow
color4 F1BC49

# Green
color5 00940F

#dark cyan
color6 074C4C


#grey
color7 6b6b6b

#orange
color8 AF560D

#yellow
color9 F1BC49

#lua_load /home/glen/conky/draw_bg.lua
#lua_draw_hook_pre draw_bg

TEXT
${goto 90}${color1}${font DejaVu Sans Mono:bold:size=12}INTERNET USAGE
${goto 90}${voffset -15}______________
${goto 90}${font DejaVu Sans Mono:bold:size=10}${color3}Down${goto 170}${color9}Up${goto 235}${color5}Total
${goto 10}${font DejaVu Sans Mono:bold:size=9}${color1}Yesterday: ${color3}${execi 300 vnstat | grep "yesterday" | awk '{print $2 $3}'}${goto 170}${color9}${execi 300 vnstat | grep "yesterday" | awk '{print $5 $6}'}${goto 235}${color5}${execi 300 vnstat | grep "yesterday" | awk '{print $8 $9}'}
${goto 10}    ${color1}Today: ${color3}${execi 300 vnstat | grep "today" | awk '{print $2 $3}'}${goto 170}${color9}${execi 300 vnstat | grep "today" | awk '{print $5 $6}'}${goto 235}${color5}${execi 300 vnstat | grep "today" | awk '{print $8 $9}'}
${goto 10}     ${color1}Week: ${color3}${execi 300 vnstat -w | grep "current week" | awk '{print $3 $4}'}${goto 170}${color9}${execi 300 vnstat -w | grep "current week" | awk '{print $6 $7}'}${goto 235}${color5}${execi 300 vnstat -w | grep "current week" | awk '{print $9 $10}'}
${goto 10}    ${color1}Month: ${color3}${execi 300 vnstat -m | grep "`date +"%b '%y"`" | awk '{print $3 $4}'}${goto 170}${color9}${execi 300 vnstat -m | grep "`date +"%b '%y"`" | awk '{print $6 $7}'}${goto 235}${color5}${execi 300 vnstat -m | grep "`date +"%b '%y"`" | awk '{print $9 $10}'}${font}


Code: To Install
> 
sudo apt-get install conky-all


Code: To Run
> 
conky


---

