---
title: "Conky updating on top of itself"
date: 2015-11-02
forum: General Help
---

### Post by Tom_greig on 2015-11-02
Hi,

I have a conkyrc script as follows:

```
background nofont sans:size=10
#xftfont sans:size=10
use_xft yes
xftalpha 0.9
update_interval 1
imlib_cache_size 0
total_run_times 0
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
#own_window_argb_visual true


# Uncomment and adjust the line below for window's opacity
own_window_argb_value 0
own_window_colour fafafa
double_buffer yes
minimum_size 225
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders yes
default_color 101010
default_shade_color 101010
alignment top_right
gap_x 25
gap_y 45
no_buffers yes
cpu_avg_samples 1
uppercase no
border_inner_margin 15
maximum_width 160


#colors
color1 0099ff
color2 slategray
color3 ffffff


TEXT
#Time
${color1}${font Oswald:size=10:bold} Time ${color3} ${hr 2} ${color3}${font}
${color3}${font Antipasto:pixelsize=50}${time %H:%M:%S}${font}
${color3}${font Open Sans:pixelsize=30}${time %A}${font}
${color3}${font Open Sans:pixelsize=30}${time %d %b}${alignr}${font Open Sans:pixelsize=20}${time %Z}${font}
#
#Weather
${color1}${font OSwald:size=10:bold} Weather ${color3}${hr 2} ${color3}${font}
${execi 300 curl -s "http://weather.yahooapis.com/forecastrss?w=27318601&u=c" -o ~/.cache/weather.xml}${font Open Sans Light:size=10}${execi 300 grep "yweather:location" ~/.cache/weather.xml | grep -o "city=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*"}
${execi 300 grep "yweather:location" ~/.cache/weather.xml | grep -o "country=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*"}${font}
${font Antipasto:size=37}${alignr}${execi 300 grep "yweather:condition" ~/.cache/weather.xml | grep -o "temp=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*"}°${font}${voffset -35}
${execi 300 cp -f ~/.conky-google-now/$(grep "yweather:condition" ~/.cache/weather.xml | grep -o "code=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*").png ~/.cache/weather.png}${image ~/.cache/weather.png -p 0,200 -s 30x30}
${execi 300 grep "yweather:condition" ~/.cache/weather.xml | grep -o "text=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | tr '[a-z]' '[A-Z]'}
${image ~/.conky-google-now/wind.png -p 0,245 -s 15x15}${goto 35}${execi 300 grep "yweather:wind" ~/.cache/weather.xml | grep -o "speed=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*"}${execi 300 grep "yweather:units" ~/.cache/weather.xml | grep -o "speed=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*"}
${goto 18}${execi 300 grep "yweather:forecast" ~/.cache/weather.xml | grep -o "day=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==1' | tr '[a-z]' '[A-Z]'}${goto 80}${execi 300 grep "yweather:forecast" ~/.cache/weather.xml | grep -o "day=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==2' | tr '[a-z]' '[A-Z]'}${goto 142}${execi 300 grep "yweather:forecast" ~/.cache/weather.xml | grep -o "day=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==3' | tr '[a-z]' '[A-Z]'}
${execi 300 cp -f ~/.conky-google-now/$(grep "yweather:forecast" ~/.cache/weather.xml | grep -o "code=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==1').png ~/.cache/weather-1.png}${image ~/.cache/weather-1.png -p 0,282 -s 30x30}${execi 300 cp -f ~/.conky-google-now/$(grep "yweather:forecast" ~/.cache/weather.xml | grep -o "code=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==2').png ~/.cache/weather-2.png}${image ~/.cache/weather-2.png -p 65,282 -s 30x30}${execi 300 cp -f ~/.conky-google-now/$(grep "yweather:forecast" ~/.cache/weather.xml | grep -o "code=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==3').png ~/.cache/weather-3.png}${image ~/.cache/weather-3.png -p 130,282 -s 30x30}


${goto 20}${execi 300 grep "yweather:forecast" ~/.cache/weather.xml | grep -o "high=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==1'}°${goto 90}${execi 300 grep "yweather:forecast" ~/.cache/weather.xml | grep -o "high=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==2'}°${goto 160}${execi 300 grep "yweather:forecast" ~/.cache/weather.xml | grep -o "high=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==3'}°
${goto 20}${execi 300 grep "yweather:forecast" ~/.cache/weather.xml | grep -o "low=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==1'}°${goto 90}${execi 300 grep "yweather:forecast" ~/.cache/weather.xml | grep -o "low=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==2'}°${goto 160}${execi 300 grep "yweather:forecast" ~/.cache/weather.xml | grep -o "low=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==3'}°
#
#Network
${color1}${font OSwald:size=10:bold} Network ${color3}${hr 2} ${color3}${font}
${color1}${font OSwald:size=10:bold}${alignr} Ethernet ${alignr}${font}
${if_up enp4s0f1}${color3}IP: ${alignr}${addr enp4s0f1}${alignr}
${downspeedgraph enp4s0f1 20,70}${alignr}${upspeedgraph enp4s0f1 20,70}
&#8595;: ${downspeed enp4s0f1}${alignr}&#8593;: ${upspeed enp4s0f1}${else}Not Connected${endif}
${color1}${font Oswald:size=10:bold}${alignr} Wireless ${alignr}${font}
${if_up wlp3s0}${color3}AP: ${alignr}${wireless_essid wlp3s0} ${wireless_link_qual_perc wlp3s0}%
IP: ${alignr}${addr wlp3s0}${alignr}
${downspeedgraph wlp3s0 20,70}${alignr}${upspeedgraph wlp3s0 20,70}
&#8595;: ${downspeed wlp3s0}${alignr}&#8593;: ${upspeed wlp3s0}${else}Not Connected${endif}
#
#Processor
${color1}${font OSwald:size=10:bold} Processor ${color3}${hr 2} ${color3}${font}
${alignr}Total: ${cpu cpu0}%
${cpugraph cpu0 20,160}
CPU1: ${cpu cpu1}% ${alignr} CPU2: ${cpu cpu2}%
${cpugraph cpu1 20,70}${alignr}${cpugraph cpu2 20,70}
CPU3: ${cpu cpu3}% ${alignr} CPU4: ${cpu cpu4}%
${cpugraph cpu3 20,70}${alignr}${cpugraph cpu4 20,70}
#
#Memory
${color1}${font OSwald:size=10:bold} Memory ${color3}${hr 2} ${color3}${font}
Mem: ${alignr}${mem}/${memmax}
${alignr}${memperc}%
${membar 10,160}
Swap: ${alignr}${swap}/${swapmax}
${alignr}${swapperc}%
${swapbar 10,160}


#
#Media Player
${color1}${font OSwald:size=10:bold} Media Player ${color3}${hr 2} ${color3}${font}
${if_match "${execi 10 python3 /home/tom/Programs/conky-cards-master/mediaplayer.py clementine -i}"=="yes"}${color3}${execpi 4 python3 /home/tom/Programs/conky-cards-master/mediaplayer.py clementine -tamlr -w 45}
${if_match "${execi 4 python3 /home/tom/Programs/conky-cards-master/mediaplayer.py clementine -p}"=="Unknown"}\
Progress: ${alignr}Unknown
${else}\
Progress:${alignr}${color1}${execibar 4  python3 /home/tom/Programs/conky-cards-master/mediaplayer.py clementine -p}
${endif}\
${else}
${color3}${font Open Sans:size=9}Not Running\
${endif}



```

It generally works fine however every now and then, it displays the updated view without clearing the old one so all the text shows up on top of itself (see image).
[ATTACH=CONFIG]265331[/ATTACH]

Is there anything I can do to stop this happening. At the moment, I have to just restart conky each time.

Thanks in advance.

---

### Post by QDR06VV9 on 2015-11-02
The problem for myself was where the line **own_window_type** is set to **override**. There are five possible values for this: desktop, override, dock, panel, and normal. The override mode causes drawing on top of itself when it updates (I have also experienced this). 
Setting mine to normal seems to do the trick for me.
If you are using unity you can also use the **dock** verb-age  which if you do this, I could then move that conky around with the mouse by holding down the <ALT> key.
Just tested the above with the Mate DE on Arch and it works as stated above <holding down ALT+holding Left mouse button drag to place the conky>
Regards

---

### Post by Tom_greig on 2015-11-03
Thanks, changing "own_window_type" fixed everything,
Tom

---

