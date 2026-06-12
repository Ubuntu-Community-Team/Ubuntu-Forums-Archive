---
title: "Conky Disappears from Desktop on click"
date: 2015-06-15
forum: General Help
---

### Post by Kpenguin on 2015-06-15
Hi everyone,
I just installed conky today. I like it, but it keeps disappearing when I click anywhere else on the desktop. [This thread ]("http://ubuntuforums.org/showthread.php?t=778131")had a solution that didn't work for me. I'm using conky manager if that helps any. Below is my .conkyrc file:
```
background yes
use_xft yes
xftfont Roboto:size=9
xftalpha 0.8
update_interval 1
total_run_times 0
own_window yes
own_window_type override
own_window_transparent yes
##############################################
# Compositing tips:
# Conky can play strangely when used with
# different compositors. I have found the
# following to work well, but your mileage
# may vary. Comment/uncomment to suit.
##############################################
## no compositor
#own_window_type override
#own_window_argb_visual no

## xcompmgr
#own_window_type override
#own_window_argb_visual yes

## cairo-compmgr
own_window_type desktop
own_window_argb_visual no
##############################################
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no
stippled_borders 0
border_margin 5
border_width 1
default_color 000000
default_shade_color 000000
default_outline_color 000000
alignment top_right
minimum_size 600 600
maximum_width 600
gap_x -250
gap_y 0
alignment top_right
no_buffers yes
uppercase no
cpu_avg_samples 2
net_avg_samples 2
short_units yes
text_buffer_size 2048
use_spacer none
override_utf8_locale yes
color1 DEE2E3
color2 121111
color3 E82A2A
##############################################
#  Output
##############################################
own_window_argb_value 0
own_window_colour 000000
TEXT
${voffset 130}${offset 70}${color1}${font AvantGarde LT ExtraLight:size=65}${time %I:%M}${color1}
${voffset -23}${offset 65}${time %d}${font AvantGarde LT ExtraLight:size=18}
${voffset -90}${offset 175}${time %b}${font AvantGarde LT ExtraLight:size=18}
${offset 175}${time %A}
${offset 175}${time %Y}
##Weather

${texeci 1300 curl -s "http://weather.yahooapis.com/forecastrss?w=12776955&u=f" -o ~/.cache/weather.xml}
${voffset -52}${offset 190}${font AvantGarde LT ExtraLight:bold:size=22}${execi 1300 grep "yweather:condition" ~/.cache/weather.xml | grep -o "temp=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*"}${font ITC Avant Garde Gothic Pro:bold:size=8}${voffset -16}o${voffset 14}${font}${color1}
${execi 1300 cp -f .weather-icons/$(grep "yweather:condition" ~/.cache/weather.xml | grep -o "code=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*").png ~/.cache/weather.png}${image ~/.cache/weather.png -p 145,310 -s 35x35}${font AvantGarde LT ExtraLight:size=18}
##Wireless
${voffset -268}${offset 165}${wireless_link_qual wlan0}%
${image wifi.png -p 114,112 -s 35x20}

${image circle.png -p 25,80 -s 321x300}



```
Thanks!

---

### Post by Cavsfan on 2015-06-15
> **Kpenguin said:**
> Hi everyone,
I just installed conky today. I like it, but it keeps disappearing when I click anywhere else on the desktop. [This thread ]("http://ubuntuforums.org/showthread.php?t=778131")had a solution that didn't work for me. I'm using conky manager if that helps any. Below is my .conkyrc file:
```
background yes
use_xft yes
xftfont Roboto:size=9
xftalpha 0.8
update_interval 1
total_run_times 0
own_window yes
own_window_type override
own_window_transparent yes
##############################################
# Compositing tips:
# Conky can play strangely when used with
# different compositors. I have found the
# following to work well, but your mileage
# may vary. Comment/uncomment to suit.
##############################################
## no compositor
#own_window_type override
#own_window_argb_visual no

## xcompmgr
#own_window_type override
#own_window_argb_visual yes

## cairo-compmgr
own_window_type desktop
own_window_argb_visual no
##############################################
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no
stippled_borders 0
border_margin 5
border_width 1
default_color 000000
default_shade_color 000000
default_outline_color 000000
alignment top_right
minimum_size 600 600
maximum_width 600
gap_x -250
gap_y 0
alignment top_right
no_buffers yes
uppercase no
cpu_avg_samples 2
net_avg_samples 2
short_units yes
text_buffer_size 2048
use_spacer none
override_utf8_locale yes
color1 DEE2E3
color2 121111
color3 E82A2A
##############################################
#  Output
##############################################
own_window_argb_value 0
own_window_colour 000000
TEXT
${voffset 130}${offset 70}${color1}${font AvantGarde LT ExtraLight:size=65}${time %I:%M}${color1}
${voffset -23}${offset 65}${time %d}${font AvantGarde LT ExtraLight:size=18}
${voffset -90}${offset 175}${time %b}${font AvantGarde LT ExtraLight:size=18}
${offset 175}${time %A}
${offset 175}${time %Y}
##Weather

${texeci 1300 curl -s "http://weather.yahooapis.com/forecastrss?w=12776955&u=f" -o ~/.cache/weather.xml}
${voffset -52}${offset 190}${font AvantGarde LT ExtraLight:bold:size=22}${execi 1300 grep "yweather:condition" ~/.cache/weather.xml | grep -o "temp=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*"}${font ITC Avant Garde Gothic Pro:bold:size=8}${voffset -16}o${voffset 14}${font}${color1}
${execi 1300 cp -f .weather-icons/$(grep "yweather:condition" ~/.cache/weather.xml | grep -o "code=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*").png ~/.cache/weather.png}${image ~/.cache/weather.png -p 145,310 -s 35x35}${font AvantGarde LT ExtraLight:size=18}
##Wireless
${voffset -268}${offset 165}${wireless_link_qual wlan0}%
${image wifi.png -p 114,112 -s 35x20}

${image circle.png -p 25,80 -s 321x300}



```
Thanks!

Possibly changing own_window_type to normal will do the trick. This is what I have in most of my conkys.

```
own_window yes
own_window_transparent yes
own_window_type [COLOR=#ff0000]normal[/COLOR]
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager 
```

You might also want to change update_interval  to 2.0 (seconds).

---

### Post by deadflowr on 2015-06-15
You have both own_window_type override and own_window_type desktop set, so therein lies a possible problem.
I'd say comment out the desktop one. (add a # to the front of the line)
Of course using the override option negates/ignores the own_window_hints rules in place.

You might also try setting one using the normal option.
own_window_type normal
That way you will still have the hints.

My two cents, at least

---

### Post by Cavsfan on 2015-06-15
I got this - VinDSL's conky from this thread: [http://ubuntuforums.org/showthread.php?t=1771033](http://ubuntuforums.org/showthread.php?t=1771033)

But, you can't really start from page one as it is outdated. Just look for conkywx 3.0 in that thread. That has all the details for creating one like I have.

[[img]http://www.zimagez.com/miniature/screenshotfrom2015-06-14163114.png[/img]](http://www.zimagez.com/zimage/screenshotfrom2015-06-14163114.php)

Edit: This is with conky1.9.0

---

### Post by Kpenguin on 2015-06-15
Thanks deadflowr and Cavsfan! It works perfectly now! I had to comment out the desktop line that deadflowr suggested. Here's what my .conkyrc file looks like now:
```
background yes
use_xft yes
xftfont Roboto:size=9
xftalpha 0.8
update_interval 2.0
total_run_times 0
own_window yes
own_window_transparent yes
own_window_type override
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
##############################################
# Compositing tips:
# Conky can play strangely when used with
# different compositors. I have found the
# following to work well, but your mileage
# may vary. Comment/uncomment to suit.
##############################################
## no compositor
#own_window_type override
#own_window_argb_visual no

## xcompmgr
#own_window_type override
#own_window_argb_visual yes

## cairo-compmgr
#own_window_type desktop
own_window_argb_visual no
##############################################
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no
stippled_borders 0
border_margin 5
border_width 1
default_color 000000
default_shade_color 000000
default_outline_color 000000
alignment top_right
minimum_size 600 600
maximum_width 600
gap_x -250
gap_y 0
alignment top_right
no_buffers yes
uppercase no
cpu_avg_samples 2
net_avg_samples 2
short_units yes
text_buffer_size 2048
use_spacer none
override_utf8_locale yes
color1 DEE2E3
color2 121111
color3 E82A2A
##############################################
#  Output
##############################################
own_window_argb_value 0
own_window_colour 000000
TEXT
${voffset 130}${offset 70}${color1}${font AvantGarde LT ExtraLight:size=65}${time %I:%M}${color1}
${voffset -23}${offset 65}${time %d}${font AvantGarde LT ExtraLight:size=18}
${voffset -90}${offset 175}${time %b}${font AvantGarde LT ExtraLight:size=18}
${offset 175}${time %A}
${offset 175}${time %Y}
##Weather

${texeci 1300 curl -s "http://weather.yahooapis.com/forecastrss?w=12776955&u=f" -o ~/.cache/weather.xml}
${voffset -52}${offset 190}${font AvantGarde LT ExtraLight:bold:size=22}${execi 1300 grep "yweather:condition" ~/.cache/weather.xml | grep -o "temp=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*"}${font ITC Avant Garde Gothic Pro:bold:size=8}${voffset -16}o${voffset 14}${font}${color1}
${execi 1300 cp -f .weather-icons/$(grep "yweather:condition" ~/.cache/weather.xml | grep -o "code=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*").png ~/.cache/weather.png}${image ~/.cache/weather.png -p 145,310 -s 35x35}${font AvantGarde LT ExtraLight:size=18}
##Wireless
${voffset -268}${offset 165}${wireless_link_qual wlan0}%
${image wifi.png -p 114,112 -s 35x20}

${image circle.png -p 25,80 -s 321x300}



```
Thank you!

---

### Post by ajgreeny on 2015-06-15
Yes, I think your .conkyrc window configuration is messy and confusing.
The parts in mine relating to window type are
```
# Create own window instead of using desktop (required in nautilus)
own_window yes

# If own_window is yes, you may use type normal, desktop or override
own_window_type override

# Use pseudo transparency with own_window?
own_window_transparent yes

# If own_window is yes, these window manager hints may be used
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
```
and I start conky automatically in the autostart list with command conky -p 20 to make sure it is delayed by 20 seconds to allow the desktop to start properly.  Without that delay I get many and varied problems with the display of conky.

Tidy up your .conkyrc, add a similar delay if it starts at session start-up, and you may overcome your problems.

EDIT:
Too slow again, and beaten to the answer.  The pause option may still be helpful to you.

---

### Post by Cavsfan on 2015-06-17
You should also have this in there which I don't see.
```
own_window_type [COLOR=#ff0000]normal[/COLOR]
```

Errrrum never mind Normal is the default.

---

### Post by Kpenguin on 2015-08-18
I'm having more issues with Conky :(
I start Conky using this command:
```
conky -c ~/conkyconfigs/conkyrc
```
This works fine when I start it from terminal, but when I put it in startup applications, it acts like a window that stays on top of anything in the center of the screen like this:
[ATTACH=CONFIG]263922[/ATTACH] 
Here's the conkyrc file:
```
# Conky settings #
background yes
update_interval 1
double_buffer yes
no_buffers yes

# Window specifications #
gap_x 0
gap_y 0
alignment middle_middle
minimum_size 600 360
maximum_width 600
own_window yes
own_window_type desktop
own_window_transparent yes
own_window_hints undecorate,sticky,skip_taskbar,skip_pager,below
#own_window_argb_visual yes
#own_window_argb_value 0
#border_margin 0
#border_inner_margin 0
#border_outer_margin 0

# Graphics settings #
draw_shades no
draw_outline no 
draw_borders no
draw_graph_borders no

# Text settings #
use_xft yes
xftalpha 0
xftfont Raleway:size=10

override_utf8_locale yes

imlib_cache_size 0

# Color scheme #
default_color FFFFFF

color1 FFFFFF

TEXT
\
#-----WOIED-----#
\
\
${execi 300 curl -s "http://weather.yahooapis.com/forecastrss?w=12776955&u=f" -o ~/.cache/weather.xml}\
\
\
#---Clock+Date---#
\
\
${font Raleway:weight=Light :size=100}${alignc}${time %H}${alignc}:${alignc}${time %M}
${font Raleway:weight=Light:size=32}${voffset -60}${alignc}${time %A %B %d}\
\
\
#---High Temperatures---#
\
\
${font Raleway:size=20}\
${voffset 76}${goto 40}${execi 300 grep "yweather:condition" ~/.cache/weather.xml | grep -o "temp=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*"}°
${font Raleway:weight=Light:size=14}\
${voffset -28}${goto 160}${execi 300 grep "yweather:forecast" ~/.cache/weather.xml | grep -o "high=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==2'}°\
${goto 270}${execi 300 grep "yweather:forecast" ~/.cache/weather.xml | grep -o "high=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==3'}°\
${goto 380}${execi 300 grep "yweather:forecast" ~/.cache/weather.xml | grep -o "high=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==4'}°\
${goto 490}${execi 300 grep "yweather:forecast" ~/.cache/weather.xml | grep -o "high=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==5'}°\
\
\
#---Low Temparatures---#
\
\
${font Raleway:weight=Light:size=10}\
${voffset 48}${goto 210}${execi 300 grep "yweather:forecast" ~/.cache/weather.xml | grep -o "low=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==2'}°\
${goto 320}${execi 300 grep "yweather:forecast" ~/.cache/weather.xml | grep -o "low=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==3'}°\
${goto 430}${execi 300 grep "yweather:forecast" ~/.cache/weather.xml | grep -o "low=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==4'}°\
${goto 540}${execi 300 grep "yweather:forecast" ~/.cache/weather.xml | grep -o "low=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==5'}°\
\
\
#---Name of the day---#
\
\
${font Raleway:weight=Light:size=14}\
${voffset 30}${goto 60}${execi 300 grep "yweather:forecast" ~/.cache/weather.xml | grep -o "day=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==1' | tr '[a-z]' '[A-Z]'}\
${goto 170}${execi 300 grep "yweather:forecast" ~/.cache/weather.xml | grep -o "day=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==2' | tr '[a-z]' '[A-Z]'}\
${goto 280}${execi 300 grep "yweather:forecast" ~/.cache/weather.xml | grep -o "day=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==3' | tr '[a-z]' '[A-Z]'}\
${goto 390}${execi 300 grep "yweather:forecast" ~/.cache/weather.xml | grep -o "day=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==4' | tr '[a-z]' '[A-Z]'}\
${goto 500}${execi 300 grep "yweather:forecast" ~/.cache/weather.xml | grep -o "day=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==5' | tr '[a-z]' '[A-Z]'}\
\
\
#---Weather Icons---#
\
\
${execi 300 cp -f ~/.conky-vision-icons/$(grep "yweather:condition" ~/.cache/weather.xml | grep -o "code=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*").png ~/.cache/weather-1.png}${image ~/.cache/weather-1.png -p 61,260 -s 32x32}\
\
${execi 300 cp -f ~/.conky-vision-icons/$(grep "yweather:forecast" ~/.cache/weather.xml | grep -o "code=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==2').png ~/.cache/weather-2.png}${image ~/.cache/weather-2.png -p 171,260 -s 32x32}\
\
${execi 300 cp -f ~/.conky-vision-icons/$(grep "yweather:forecast" ~/.cache/weather.xml | grep -o "code=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==3').png ~/.cache/weather-3.png}${image ~/.cache/weather-3.png -p 281,260 -s 32x32}\
\
${execi 300 cp -f ~/.conky-vision-icons/$(grep "yweather:forecast" ~/.cache/weather.xml | grep -o "code=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==4').png ~/.cache/weather-4.png}${image ~/.cache/weather-4.png -p 391,260 -s 32x32}\
\
${execi 300 cp -f ~/.conky-vision-icons/$(grep "yweather:forecast" ~/.cache/weather.xml | grep -o "code=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==5').png ~/.cache/weather-5.png}${image ~/.cache/weather-5.png -p 501,260 -s 32x32}${font}${voffset -46}\
```
Also, after a few minutes of it being open, no matter how I launch it, I have this problem:
[ATTACH=CONFIG]263921[/ATTACH]
Any help would be appreciated!
Thanks
Kpenguin

---

### Post by QDR06VV9 on 2015-08-18
> **Kpenguin said:**
> I'm having more issues with Conky :(
I start Conky using this command:
```
conky -c ~/conkyconfigs/conkyrc
```
This works fine when I start it from terminal, but when I put it in startup applications, it acts like a window that stays on top of anything in the center of the screen like this:
[ATTACH=CONFIG]263922[/ATTACH] 
Here's the conkyrc file:
```
# Conky settings #
background yes
update_interval 1
double_buffer yes
no_buffers yes

# Window specifications #
gap_x 0
gap_y 0
alignment middle_middle
minimum_size 600 360
maximum_width 600
own_window yes
own_window_type desktop
own_window_transparent yes
own_window_hints undecorate,sticky,skip_taskbar,skip_pager,below
#own_window_argb_visual yes
#own_window_argb_value 0
#border_margin 0
#border_inner_margin 0
#border_outer_margin 0

# Graphics settings #
draw_shades no
draw_outline no 
draw_borders no
draw_graph_borders no

# Text settings #
use_xft yes
xftalpha 0
xftfont Raleway:size=10

override_utf8_locale yes

imlib_cache_size 0

# Color scheme #
default_color FFFFFF

color1 FFFFFF

TEXT
\
#-----WOIED-----#
\
\
${execi 300 curl -s "http://weather.yahooapis.com/forecastrss?w=12776955&u=f" -o ~/.cache/weather.xml}\
\
\
#---Clock+Date---#
\
\
${font Raleway:weight=Light :size=100}${alignc}${time %H}${alignc}:${alignc}${time %M}
${font Raleway:weight=Light:size=32}${voffset -60}${alignc}${time %A %B %d}\
\
\
#---High Temperatures---#
\
\
${font Raleway:size=20}\
${voffset 76}${goto 40}${execi 300 grep "yweather:condition" ~/.cache/weather.xml | grep -o "temp=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*"}°
${font Raleway:weight=Light:size=14}\
${voffset -28}${goto 160}${execi 300 grep "yweather:forecast" ~/.cache/weather.xml | grep -o "high=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==2'}°\
${goto 270}${execi 300 grep "yweather:forecast" ~/.cache/weather.xml | grep -o "high=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==3'}°\
${goto 380}${execi 300 grep "yweather:forecast" ~/.cache/weather.xml | grep -o "high=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==4'}°\
${goto 490}${execi 300 grep "yweather:forecast" ~/.cache/weather.xml | grep -o "high=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==5'}°\
\
\
#---Low Temparatures---#
\
\
${font Raleway:weight=Light:size=10}\
${voffset 48}${goto 210}${execi 300 grep "yweather:forecast" ~/.cache/weather.xml | grep -o "low=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==2'}°\
${goto 320}${execi 300 grep "yweather:forecast" ~/.cache/weather.xml | grep -o "low=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==3'}°\
${goto 430}${execi 300 grep "yweather:forecast" ~/.cache/weather.xml | grep -o "low=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==4'}°\
${goto 540}${execi 300 grep "yweather:forecast" ~/.cache/weather.xml | grep -o "low=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==5'}°\
\
\
#---Name of the day---#
\
\
${font Raleway:weight=Light:size=14}\
${voffset 30}${goto 60}${execi 300 grep "yweather:forecast" ~/.cache/weather.xml | grep -o "day=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==1' | tr '[a-z]' '[A-Z]'}\
${goto 170}${execi 300 grep "yweather:forecast" ~/.cache/weather.xml | grep -o "day=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==2' | tr '[a-z]' '[A-Z]'}\
${goto 280}${execi 300 grep "yweather:forecast" ~/.cache/weather.xml | grep -o "day=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==3' | tr '[a-z]' '[A-Z]'}\
${goto 390}${execi 300 grep "yweather:forecast" ~/.cache/weather.xml | grep -o "day=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==4' | tr '[a-z]' '[A-Z]'}\
${goto 500}${execi 300 grep "yweather:forecast" ~/.cache/weather.xml | grep -o "day=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==5' | tr '[a-z]' '[A-Z]'}\
\
\
#---Weather Icons---#
\
\
${execi 300 cp -f ~/.conky-vision-icons/$(grep "yweather:condition" ~/.cache/weather.xml | grep -o "code=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*").png ~/.cache/weather-1.png}${image ~/.cache/weather-1.png -p 61,260 -s 32x32}\
\
${execi 300 cp -f ~/.conky-vision-icons/$(grep "yweather:forecast" ~/.cache/weather.xml | grep -o "code=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==2').png ~/.cache/weather-2.png}${image ~/.cache/weather-2.png -p 171,260 -s 32x32}\
\
${execi 300 cp -f ~/.conky-vision-icons/$(grep "yweather:forecast" ~/.cache/weather.xml | grep -o "code=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==3').png ~/.cache/weather-3.png}${image ~/.cache/weather-3.png -p 281,260 -s 32x32}\
\
${execi 300 cp -f ~/.conky-vision-icons/$(grep "yweather:forecast" ~/.cache/weather.xml | grep -o "code=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==4').png ~/.cache/weather-4.png}${image ~/.cache/weather-4.png -p 391,260 -s 32x32}\
\
${execi 300 cp -f ~/.conky-vision-icons/$(grep "yweather:forecast" ~/.cache/weather.xml | grep -o "code=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==5').png ~/.cache/weather-5.png}${image ~/.cache/weather-5.png -p 501,260 -s 32x32}${font}${voffset -46}\
```
Also, after a few minutes of it being open, no matter how I launch it, I have this problem:
[ATTACH=CONFIG]263921[/ATTACH]
Any help would be appreciated!
Thanks
Kpenguin

You or something changed <own_window_type desktop>
switch back to override && consider ajgreeny idea of adding p-20 [COLOR=#000000] to make sure it is delayed by 20 seconds to allow the desktop to start properly.
[/COLOR]so your command to start conky would be like this
```
conky -c ~/conkyconfigs/conkyrc -p20
```
Side Note sometimes conky-manager has a mind of it's own.
See this [http://ubuntuforums.org/showthread.php?t=2285118](http://ubuntuforums.org/showthread.php?t=2285118)
If you are going to use conky-manager it will work better if you edit your .conkyrc's with the edit option in conky-manager.
 
Regards

---

### Post by Kpenguin on 2015-08-18
Appears to be working now. Thanks!

---

### Post by Kpenguin on 2015-08-18
Guess not... still having the second issue. :(

---

### Post by Cavsfan on 2015-08-21
> **Kpenguin said:**
> Guess not... still having the second issue. :(

I never could get override working on Ubuntu. It works great on Arch though.

```
    own_window = true,
    own_window_transparent = true,
    own_window_type = 'normal',
    own_window_hints = 'undecorated,below,sticky,skip_taskbar,skip_pager', 
```

Has always worked for me. Also are you aware of the changes between conky 1.9.0 and 1.10.0?

In the section above TEXT comments are 2 dashes "--" (without quotes) and inside the TEXT section the # character is still for comments.

Also the 1st line must be:
**conky.config = {**
Then all of the stuff above TEXT must have a comma at the end.
At the bottom before the TEXT part you must have a line like this with a blank line above it and below it:
**};**

The word TEXT has been replaced with:
**conky.text = [[**
on it's own line then after all of the lines in that bottom section you must have this:
**]];**
as the very last line.

This is only in the conkyrc file or whatever you named it. I renamed mine to have a .lua at the end.
The templates and conf files are unchanged.

Also you could save some CPU usage by checking the weather less than every 5 minutes as it's unlikely to change that quickly.

I check mine every 30 minutes and that seems to work well.

---

### Post by Cavsfan on 2015-08-22
This may depend on whether you use lua or not. If you use lua it definitely needs to be converted if you don't I don't think it does.

Here are some differences between the two:
[http://fossies.org/diffs/conky/1.9.0_vs_1.10.0/](http://fossies.org/diffs/conky/1.9.0_vs_1.10.0/)

Also on that page is a conversion file that you can either copy into a text file and save it as **convert.lua** in your conky directory.
Make it executable or at the top is a link where you can download it as a text file and then make it executable.
It's probably wise to just make the conversion just in case anything you do from this point forward involves lua. But that is totally up to you.
Again this is only the conkyrc file and none of the templates or config files that it uses.

[http://fossies.org/linux/privat/conky-1.10.0.tar.gz/conky-1.10.0/extras/convert.lua](http://fossies.org/linux/privat/conky-1.10.0.tar.gz/conky-1.10.0/extras/convert.lua)

[COLOR=#ff0000]Usage: convert.lua old_conkyrc [new_conkyrc][/COLOR] I used [COLOR=#b22222]convert.lua[/COLOR] [COLOR=#0000ff]old_conkyrc[/COLOR]  [COLOR=#ff0000]new_conkyrc.lua[/COLOR] just so I could tell them apart.
In case you have **max_specials** in your conkyrc file I believe it will miss that and you'll have to prepend that with double dashes (the new comment character).

But other than that it should work like a charm.

Edit: **pre_exec** is not included but can be replaced with **exec** and **if_running** is not included but **if_match** will substitute in it's place.

E.G. **${if_running audacious}**  won't work but **${if_match "${exec pidof audacious}" > "0"}** will work.

---

### Post by Cavsfan on 2015-08-23
That convert.lua file works much better on conkyrc files than trying to convert it/them yourself. I tried one file and failed.
So I converted it with convert.lua and viola perfect conversion. You can tell when it's right the letter colors are all pink in the new **conky.text** section.

Above that certain words are different colors too.

Hope this helps.

---

### Post by Cavsfan on 2015-09-01
Did you ever get your Conky fixed?

---

