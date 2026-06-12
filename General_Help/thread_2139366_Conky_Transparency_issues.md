---
title: "Conky Transparency issues"
date: 2013-04-26
forum: General Help
---

### Post by faqterson on 2013-04-26
I have found and programmed 2 different conky config files and not one of them I am able to get the transparency to the background to work correctly. I have found ```
own_window_argb_visual yes
``` forces into transparency mode but this cause a problem with weather icons I use.

My Main conkyrc file I will like to use:
```

# Conky Google Now style #

# Conky settings #
background no
update_interval 1
double_buffer yes
no_buffers yes

# Window specifications #
own_window yes
own_window_class Conky
own_window_transparent yes
own_window_type normal
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
own_window_title conly
own_window_colour FFFFFF
#own_window_argb_visual yes
#own_window_argb_value 255

minimum_size 250

# Alignment #
alignment tr
gap_x 300
gap_y 100

border_inner_margin 15
border_outer_margin 0

# Graphics settings #
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no

# Text settings #
use_xft yes
xftalpha 0
xftfont Open Sans Light:size=10

override_utf8_locale yes

imlib_cache_size 0

# Color scheme #
default_color white

color1 0099CC
color2 9933CC
color3 669900
color4 FF8800
color5 CC0000
color6 AAAAAA
color7 DDDDDD

TEXT
${color}${font Open Sans Light:size=21}${time %A,}${color1}${color}${time %T}
${font size=15}${color}${time %B %e, %G}
${color7}${hr}${color}
${execi 300 curl -s "http://weather.yahooapis.com/forecastrss?w=12753245&u=c" -o ~/.cache/weather2.xml}#${font Open Sans Light:size=9}${execi 300 grep "yweather:location" ~/.cache/weather.xml | grep -o "city=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*"}, ${execi 300 grep "yweather:location" ~/.cache/weather.xml | grep -o "country=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*"}${font}
${execi 300 curl -s "http://www.accuweather.com/en/za/johannesburg/305448/current-weather/305448" -o ~/.cache/weather.xml}${font Open Sans Light:size=9}${execi 300 grep "acm_RecentLocationsCarousel.push" ~/.cache/weather.xml | grep 305448 | grep -o "name:'[^\']*'" |grep -o "'[^\']*'" | grep -o "[^\']*"}
#${font Open Sans Light:size=45}${alignr}${execi 300 grep "yweather:condition" ~/.cache/weather.xml | grep -o "temp=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*"}°${font}
${font Open Sans Light:size=45}${alignr}${execi 300 grep "acm_RecentLocationsCarousel.push" ~/.cache/weather.xml | grep 305448 | grep -o "temp:'[^\']*'" | grep -o "'[^\']*'" | grep -o "[^\']*"}°${font}
${execi 300 wget -c -P web/ http://vortex.accuweather.com/adc2010/images/icons-numbered/$(grep "acm_RecentLocationsCarousel.push" ~/.cache/weather.xml | grep 305448 |grep -o "icon:'[^\']*'" | grep "'[^\']*'" | grep -o "[0-9][0-9]\-m.png")}
${execi 300 cp -f ~/web/$(grep "acm_RecentLocationsCarousel.push" ~/.cache/weather.xml | grep 305448 |grep -o "icon:'[^\']*'" | grep "'[^\']*'" | grep -o "[0-9][0-9]\-m.png") ~/.cache/weather.png}${image ~/.cache/weather.png -p 0,115 -s 90x60}
     ${execi 300 grep "acm_RecentLocationsCarousel.push" ~/.cache/weather.xml | grep 305448 | grep -o "text:'[^\']*'" | grep -o "'[^\']*'" | grep -o "[^\']*"}
     ${color6}${execi 300 grep -o "s = '[^\']*'" ~/.cache/weather.xml | grep -o "'[^\']*'" | grep -o "[^\']*"}
${color6}${execi 300}
${color}${execi 300 grep "yweather:forecast" ~/.cache/weather2.xml | grep -o "day=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | head -n1}  ${execi 300 grep "yweather:forecast" ~/.cache/weather2.xml | grep -o "high=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | head -n1}° ${color6}${execi 300 grep "yweather:forecast" ~/.cache/weather2.xml | grep -o "low=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | head -n1}°${color}${alignr}${execi 300 grep "yweather:forecast" ~/.cache/weather2.xml | grep -o "day=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | tail -n1}  ${execi 300 grep "yweather:forecast" ~/.cache/weather2.xml | grep -o "high=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | tail -n1}° ${color6}${execi 300 grep "yweather:forecast" ~/.cache/weather2.xml | grep -o "low=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | tail -n1}°${color}${voffset 1}
#CPU: ${cpu cpu 1}% ${alignr}${cpubar 8,60 cpu 1}
#CPU: ${cpu cpu 2}% ${alignr}${cpubar 8,60 cpu 2}
#CPU: ${cpu cpu 3}% ${alignr}${cpubar 8,60 cpu 3}
#CPU: ${cpu cpu 4}% ${alignr}${cpubar 8,60 cpu 4}
#CPU: ${cpu cpu 5}% ${alignr}${cpubar 8,60 cpu 5}
#CPU: ${cpu cpu 6}% ${alignr}${cpubar 8,60 cpu 6}
Uptime: ${alignr}${uptime_short}
Kernel: ${alignr}${kernel}
Disk Used: ${alignr}${fs_used} of ${fs_size}
${color7}${hr}${color}

${color5}$memperc%${color} of RAM is currently in use
${color2}${cpu cpu}%${color} of CPU is currently in use
${if_existing /proc/net/route wlan1}
${color1}Up:${color} ${color3}${upspeed wlan1}${color}${alignr}${color1}Down:${color} ${color3}${downspeed wlan1}${color}
${upspeedgraph wlan1 50,120 FF8800 FF8800}${alignr}${downspeedgraph wlan1 50,120 FF8800 FF8800}
${color1}Sent:${color} ${color2}${totalup wlan1}${color}${alignr}${color1}Received:${color} ${color2}${totaldown wlan1}${color}
${else}${if_existing /proc/net/route eth0}
${color1}Down:${color} ${color3}${downspeed eth0}${color}${alignr}${color1}Up:${color} ${color3}${upspeed eth0}${color}
${upspeedgraph eth0 50,120 FF8800 FF8800}${alignr}${downspeedgraph eth0 50,120 FF8800 FF8800}
${color1}Received:${color} ${color2}${totaldown eth0}${color}${alignr}${color1}Sent:${color} ${color2}${totalup eth0}${color}
${else}${if_existing /proc/net/route eth1}
${color1}Up:${color} ${color3}${upspeed eth1}${color}${alignr}${color1}Down:${color} ${color3}${downspeed eth1}${color}
${upspeedgraph eth1 50,120 FF8800 FF8800}${alignr}${downspeedgraph eth1 50,120 FF8800 FF8800}
${color1}Sent:${color} ${color2}${totalup eth1}${color}
${alignr}${color1}Received:${color} 
${color2}${totaldown eth1}${color}
${else}${if_existing /proc/net/route ppp0}
${color1}Up:${color} ${color3}${upspeed ppp0}${color}${alignr}${color1}Down:${color} ${color3}${downspeed ppp0}${color}
${upspeedgraph ppp0 50,120 FF8800 FF8800}${alignr}${downspeedgraph ppp0 50,120 FF8800 FF8800}
${color1}Sent:${color} ${color2}${totalup ppp0}${color}${alignr}${color1}Received:${color} ${color2}${totaldown ppp0}${color}
${else}
Network disconnected
${color6}Connect to a network to see statistics${color}
${voffset 50}
${endif}${endif}${endif}${endif}${voffset -15}

```

Another Conky config file I found that is also not working with tranparency
```

# Conky settings #
background no
update_interval 1

cpu_avg_samples 2
net_avg_samples 2

override_utf8_locale yes

double_buffer yes
no_buffers yes

text_buffer_size 2048
#imlib_cache_size 0

temperature_unit fahrenheit

# Window specifications #

own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorate,sticky,skip_taskbar,skip_pager,below
own_window_argb_visual yes
own_window_argb_value 0

border_inner_margin 0
border_outer_margin 0

minimum_size 200 250
maximum_width 200

alignment tr
gap_x 35
gap_y 55

# Graphics settings #
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no

# Text settings #
use_xft yes
xftfont caviar dreams:size=8
xftalpha 0.5

uppercase no

temperature_unit celsius


default_color FFFFFF

# Lua Load  #
lua_load ~/.conky/clock_rings.lua
lua_draw_hook_pre clock_rings

TEXT
${voffset 8}${color FF6600}${font caviar dreams:size=16}${time %A}${font}${voffset -8}${alignr 50}${color FFFFFF}${font caviar dreams:size=38}${time %e}${font}
${color FFFFFF}${voffset -30}${color FFFFFF}${font caviar dreams:size=18}${time %b}${font}${voffset -3} ${color FFFFFF}${font caviar dreams:size=20}${time %Y}${font}${color FF6600}${hr}
${voffset 140}${font caviar dreams:size=10}${alignr}HOME${font}
${font caviar dreams:size=12}${color FFFFFF}${alignr}${weather http://weather.noaa.gov/pub/data/observations/metar/stations/ FAJS temperature temperature 30} °C${font}
${image ~/.conky/new-ubuntu-logo.png -p 64,125 -s 70x20}

${color FFFFFF}${goto 25}${voffset 35}${cpu cpu0}%
${color FF6600}${goto 25}CPU
${color FFFFFF}${goto 50}${voffset 23}${memperc}%
${color FF6600}${goto 50}RAM
${color FFFFFF}${goto 75}${voffset 23}${swapperc}%
${color FF6600}${goto 75}Swap
${color FFFFFF}${goto 100}${voffset 23}${fs_used_perc /}%
${color FF6600}${goto 100}Disk
${color FFFFFF}${goto 125}${voffset 25}${downspeed wlan1}
${color FFFFFF}${goto 125}${upspeed wlan1}
${color FF6600}${goto 125}Net



${color FFFFFF}${font caviar dreams:size=8}Uptime: ${uptime_short}
${color FFFFFF}${font caviar dreams:size=8}Processes: ${processes}
${color FFFFFF}${font caviar dreams:size=8}Running: ${running_processes}


${color FF6600}${font caviar dreams:size=8}${alignr}${nodename}
${color FF6600}${font caviar dreams:size=8}${alignr}${pre_exec cat /etc/issue.net}  $machine
${color FF6600}${font caviar dreams:size=8}${alignr}Kernel: ${kernel}

```

Any help related to this issue will be very help full

---

### Post by cariboo on 2013-04-26
You'd probably be better off asking your question in the [Conky]("http://ubuntuforums.org/showthread.php?t=281865") thread.

---

### Post by VinDSL on 2013-04-26
Here's what I use:

```
<SNIP>

####
## Create 'own_window' type. Makes Conky behave like other panels.
#
own_window yes
**[COLOR="#0000CD"]own_window_transparent yes[/COLOR]**
**[COLOR="#0000CD"]own_window_type normal[/COLOR]**
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
####
## Some distros require the following lines for true transparency.
## BOTH of these lines need to be Commented/Uncommented in tandem.
#
[B][COLOR="#0000CD"]own_window_argb_visual yes
own_window_argb_value 255[/COLOR][/B]

<SNIP>
```


Works fine on multiple DEs. I'm using the above on Ubu 13.04 Unity / GS 3.8.1 / LXDE...  ;)

---

### Post by faqterson on 2013-04-27
```



**[COLOR=#0000CD]own_window_argb_visual yes own_window_argb_value 255[/COLOR]**
```

I am not able to use this as it also makes my weather icons transparent as well.

```

${execi 300 cp -f ~/web/$(grep "acm_RecentLocationsCarousel.push" ~/.cache/weather.xml | grep 305448 |grep -o "icon:'[^\']*'" | grep "'[^\']*'" | grep -o "[0-9][0-9]\-m.png") ~/.cache/weather.png}${image ~/.cache/weather.png -p 0,115 -s 90x60} 
```

I am doing this on ubuntu 13.04 as well, using Unity. From what I have read up, it seams to be related to the way Ubuntu creates backgrounds.

---

### Post by VinDSL on 2013-04-27
> **faqterson said:**
> ```



**[COLOR=#0000CD]own_window_argb_visual yes own_window_argb_value 255[/COLOR]**
```

I am not able to use this as it also makes my weather icons transparent as well.
Yep, true transparency means TRUE transparency.  :)

You could probably make a separate semi-transparent conkyrc for the weather component and overlay it.  

Dunno, never tried it...

Personally, I prefer my icons to be transparent.

---

### Post by Elfy on 2013-04-27
*Thread moved to **General Help**.*

---

### Post by faqterson on 2013-04-30
I have decided to add some screen shots related to this issue.
```

# Conky settings #
background yes
update_interval 1
double_buffer yes
no_buffers yes

# Window specifications #
own_window yes
own_window_type normal
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
own_window_title conky
#own_window_colour FFFFFF
own_window_transparent yes

```

[ATTACH=CONFIG]241980[/ATTACH]

Now if I added the following line
```
own_window_argb_visual yes
```

[ATTACH=CONFIG]241981[/ATTACH]

So as you can see the new line added, does make it transparent but the weather Icon also goes transparent which makes it look ugly.

---

### Post by figure002 on 2013-06-18
The problem you are having is a known bug in Conky. I've reported this bug back in 2010 (see [https://sourceforge.net/p/conky/bugs/317/](https://sourceforge.net/p/conky/bugs/317/)), but unfortunately there has not been any reply from the developers.

---

### Post by faqterson on 2013-06-18
I have found that when conky is added to my start menu it fixes the back ground image issue. However on reload or restart of conky it breaks. 

Totally weard bug, could very well be related to the way ubuntu loads the background as well.

---

### Post by VinDSL on 2013-06-18
> **faqterson said:**
> Totally weard bug [...]
Cannot reproduce it here.  Sorry!


[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-18-jun-2013-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-18-jun-2013-1.png")[/INDENT]

Tried [this]("http://ubuntuforums.org/showthread.php?t=2139366&p=12620796&viewfull=1#post12620796") yet?

If yes, and it didn't work, have you tried switching your weather icon set?

Some icon sets are more transparent than others -- some not transparent at all...

---

### Post by HiImTye on 2013-06-18
here's one of my configs that works on 12.10```
background yes

use_xft yes # Use Xft?
#xftfont Bitstream Vera Sans Mono:size=8
xftfont Ubuntu:size=9
xftalpha 1 # Text alpha when using Xft

update_interval 2 # Update interval in seconds

total_run_times 0

own_window yes
own_window_argb_visual no
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

double_buffer yes # Use double buffering (reduces flicker, may not work for everyone)

minimum_size  160
maximum_width 160

draw_shades yes
draw_outline no
draw_borders no
stippled_borders 8

border_width 1

default_color white
default_shade_color black
default_outline_color white

no_buffers yes
uppercase no

cpu_avg_samples 4

override_utf8_locale no

use_spacer right # Add spaces to keep things from moving about?  This only affects certain objects.

#color1 lightgrey
color1 green
color2 blue
color3 orange
color4 midnightblue

TEXT
${color2}Distro: ${alignr}${color3}${pre_exec lsb_release -d -s}
${color2}Codename: ${alignr}${color3}${pre_exec lsb_release -c -s}
${color2}Kern: ${alignr}${color3}$kernel
${color2}UpTime: ${alignr}${color3}$uptime
${color2}Session: ${alignr}${color3}${pre_exec echo $USER} @ ${nodename}\
${pre_exec echo $DISPLAY}
${color1}${top name 10}${alignr}${color1}${top pid 10}${color1}${top cpu 10}
${color1}${top name 9}${alignr}${color1}${top pid 9}${color1}${top cpu 9}
${color1}${top name 8}${alignr}${color1}${top pid 8}${color1}${top cpu 8}
${color1}${top name 7}${alignr}${color1}${top pid 7}${color1}${top cpu 7}
${color1}${top name 6}${alignr}${color1}${top pid 6}${color1}${top cpu 6}
${color1}${top name 5}${alignr}${color1}${top pid 5}${color1}${top cpu 5}
${color1}${top name 4}${alignr}${color1}${top pid 4}${color1}${top cpu 4}
${color1}${top name 3}${alignr}${color1}${top pid 3}${color1}${top cpu 3}
${color1}${top name 2}${alignr}${color1}${top pid 2}${color1}${top cpu 2}
${color3}${top name 1}${alignr}${color1}${top pid 1}${color1}${top cpu 1}
${color2}Name${alignr}PID  CPU
${color2}GPU: ${alignr}${color3}${nvidia temp}${iconv_start UTF-8 ISO_8859-1}°${iconv_stop}C
${color2}Load: ${alignr}${color3}${loadavg 1}${color2}|${color3}${loadavg 2}${color2}|${color3}${loadavg 3}
${color2}Freq: ${alignr}${color3}${freq 1} MHz${color2}|${color3}${freq 2} MHz
${color2}CPU: ${alignr}${color3}${cpu}% ${color2}(${color3}${cpu cpu1}%${color2}|${color3}${cpu cpu2}%${color2})
${color4}${cpugraph 12,160 0000ff ff00ff -t}
${cpugraph cpu2 12,160 0000ff ff00ff -t}
${cpugraph cpu1 12,160 0000ff ff00ff -t}

```[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]

---

### Post by figure002 on 2013-06-19
> **VinDSL said:**
> Cannot reproduce it here.  Sorry!

Tried [this]("http://ubuntuforums.org/showthread.php?t=2139366&p=12620796&viewfull=1#post12620796") yet?

If yes, and it didn't work, have you tried switching your weather icon set?

Some icon sets are more transparent than others -- some not transparent at all...

That's because you have a dark background/wallpaper. You'll only notice the glitch with lighter backgrounds (this is also mentioned in the bug report). Try setting a lighter background, and you'll probably see the same problem.

About the possible solution you have (the code colored in blue): I have the same values in my Conky configuration, so that won't help. Also, I've tried many different configurations, but none fix this issue. This has also noting to do with the images or icons themselves; I've tried many many different images/icons, so it seems to happen with any image.

I've chatted with one of the Conky developers on IRC yesterday to ask about this issue. He said that this problem cannot be fixed, because according to him, it's because of the way compositors (Compiz, Clutter, etc.) work. Apparently, Conky uses the compositor to create true transparency. He said: "It's not a problem with the compositor, it's just the way things work". But I find it hard to believe that this cannot be fixed in Conky, because there are other applications out there that manage to combine transparency with opaque graphics.

---

### Post by figure002 on 2013-06-19
> **HiImTye said:**
> here's one of my configs that works on 12.10

...

Your configuration won't have that problem because you have true transparency disabled:
```
own_window_argb_visual no
```

This problem only occurs with true transparency enabled:
```

own_window_transparent yes
own_window_argb_visual yes

```

So it's not really a solution, but at least we have a workaround.

---

### Post by VinDSL on 2013-07-02
~cool

Works, for me! 

```
####
## Create 'own_window' type. Makes Conky behave like other panels.
#
own_window yes
own_window_transparent yes
own_window_type normal
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
####
## Some distros require the following lines for TRUE transparency.
## BOTH of these lines need to be Commented/Uncommented in tandem.
#
own_window_argb_visual yes
own_window_argb_value 255
####
## Don't want TRUE transparency? (icons look janky on certain walls)
## Comment both of the lines above and Uncomment the line below.
#
# own_window_argb_visual no
```

---

