---
title: "Conky not aligning text grab since upgrade to 14.04"
date: 2015-01-05
forum: General Help
---

### Post by mjjohanson on 2015-01-05
Greetings,

I have a weather display in Conky that grabs forecast text from weather.gov. Prior to 14.04 the following line would display a chunk of text in a block starting at 52 with subsequent lines wrapping back to 52. 

${goto 52}${exec sed -n '1p' ~/.conky/weather/forecast | fold -s -w 28}

Now, subsequent lines wrap to 0 or the left edge of the box. It seems that the /n that comes from fold is now interpreted in a different way than it used to be. Before rearranging my display to account for this, I am wondering if anyone has encountered and resolved this problem. 

Here is an image of what is happening. The text blocks under 'forecast' should be aligned at 52 pixels in and the '100%' should be centered under the moon. (BTW I live in Minneapolis, Minnesota, USA. Also, I delayed the upgrade until last month.)

Script that grabs data:
```
#!/bin/bash
# by mjjohanson
# ugly but it works
wget -O ~/.conky/weather/weather_data "http://forecast.weather.gov/MapClick.php?lat=44.89090425391711&lon=-93.36250305175781&site=mpx&smap=1&unit=0&lg=en&FcstType=text&TextType=1" #saved as HTML file
grep -E "ay:|night:|noon:" <~/.conky/weather/weather_data >~/.conky/weather/forecast #put forecast lines in new file

sed -i 's/<br>/\n/g' ~/.conky/weather/forecast #change code to linefeed
sed -i '/warn">/d' ~/.conky/weather/forecast #delete line
sed -i 's/<[^>]\+>//g' ~/.conky/weather/forecast #delete tags
sed -i '/^$/d' ~/.conky/weather/forecast #delete blank lines

sed -i 's/\.  /\. /g' ~/.conky/weather/forecast #change double space to single
sed -i 's/\([0-9]\) percent/\1%/g' ~/.conky/weather/forecast #change percent to symbol
sed -i 's/\([0-9]\)\./\1°\. /g' ~/.conky/weather/forecast #add degree symbol after numbers at end of sentences
sed -i 's/\([0-9]\) /\1° /g' ~/.conky/weather/forecast #add degree symbol after numbers in lines
sed -i 's/\([0-9]\)° to/\1 to/g' ~/.conky/weather/forecast #remove degree symbol before 'to'
sed -i 's/\([0-9]\)° mph/\1 mph/g' ~/.conky/weather/forecast #remove degree symbol before 'mph'
sed -i 's/\([0-9]\)° inches/\1 inches/g' ~/.conky/weather/forecast #remove degree symbol before 'inches'
sed -i 's/\([0-9]\)° of/\1 of/g' ~/.conky/weather/forecast #remove degree symbol before 'of'
sed -i 's/\([0-9]\)° and/\1 and/g' ~/.conky/weather/forecast #remove degree symbol before 'of'
```

Conky script:
```
#==============================================================================
#                                 conkyrc_weather
#  
# by mjjohanson based on work by TeoBigusGeekus
#
#==============================================================================

background yes
update_interval 2000

double_buffer yes
no_buffers yes
text_buffer_size 2048

alignment tr
gap_x 224
gap_y 700
minimum_size 180 500
maximum_width 180

own_window yes
own_window_type normal
own_window_transparent yes
own_window_argb_visual yes
own_window_argb_value 200
own_window_hints undecorate,sticky,skip_taskbar,skip_pager,below
border_inner_margin 1
border_outer_margin 1

draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no

override_utf8_locale yes
use_xft yes
xftfont ubuntu:size=7

xftalpha 0.5
uppercase 20

default_color cccccc #text
color1 999999 #lines
color2 aaaaaa #icons
color3 888888 #footer
color4 404040 #moon phase
color5 444444 #

lua_load ~/.conky/weather/set_icon.lua
lua_load ~/.conky/weather/set_icon_current.lua
lua_load ~/.conky/weather/set_icon_wind.lua

TEXT
${exec sh ~/.conky/weather/conky_weather_current.sh}
${exec sh ~/.conky/weather/conky_weather.sh}
${exec sh ~/.conky/weather/conky_moon.sh}
${goto 4}${voffset -28}${font Ubuntu:size=7,weight:bold}${color ffffff}current
${voffset -4}${color1}${hr 1}${color}
${voffset -8}${alignc 76}${font Ubuntu:size=32}${exec sed -n '2p' ~/.conky/weather/current}${voffset -18}${font Ubuntu:size=11}F
${voffset 16}${alignc 60}${font Ubuntu:size=11,weight:bold}${exec sed -n '3p' ~/.conky/weather/current}${voffset -4}${font Ubuntu:size=6}C${font}${color}
${voffset -48}${goto 82}RH${goto 100}${exec sed -n '4p' ~/.conky/weather/current}
${goto 82}BP${goto 100}${exec sed -n '6p' ~/.conky/weather/current}
${goto 82}DP${goto 100}${exec sed -n '7p' ~/.conky/weather/current}
${goto 82}FL${goto 100}${exec sed -n '8p' ~/.conky/weather/current}
${voffset 8}${font conkyweather:size=32}${color}${lua_parse conky_set_icon_current 1}${font conkywindnesw:size=32}${color}${voffset -6}${goto 64}${lua_parse conky_set_icon_wind 5}${image ~/.conky/weather/moon.gif -p 120,68 -s 50x50 -n}${font}
${voffset 4}${alignc 10}${exec sed -n '5p' ~/.conky/weather/current}
${voffset -11}${alignc -60}${exec sed -n '1p' ~/.conky/weather/moonphase | fold -s -w 9}
${voffset -22}${alignc 62}${exec sed -n '1p' ~/.conky/weather/current | fold -s -w 9}
${voffset 6}${goto 4}${font Ubuntu:size=7,weight:bold}${color ffffff}forecast
${voffset -4}${color1}${hr 1}${color2}
${font conkyweather:size=32}${lua_parse conky_set_icon 1}${color}${font}
${voffset -42}${goto 52}${if_match "Hazardous Weather Conditions" == "${exec sed -n '9p' ~/.conky/weather/current}"}${color 01bef3}${font Ubuntu:size=7,weight:bold}Hazardous Weather${color}${font}${voffset 12}${endif}#
${goto 52}${exec sed -n '1p' ~/.conky/weather/forecast | fold -s -w 28}
${voffset 2}#
${color1}${hr 1}${color2}
${font conkyweather:size=32}${lua_parse conky_set_icon 2}${color}${font}
${voffset -42}${goto 52}${exec sed -n '2p' ~/.conky/weather/forecast | fold -s -w 28}
${voffset 2}#
${color1}${hr 1}${color2}
${font conkyweather:size=32}${lua_parse conky_set_icon 3}${color}${font}
${voffset -42}${goto 52}${exec sed -n '3p' ~/.conky/weather/forecast | fold -s -w 28}
${voffset 2}#
${color1}${hr 1}${color2}
${font conkyweather:size=32}${lua_parse conky_set_icon 4}${color}${font}
${voffset -42}${goto 52}${exec sed -n '4p' ~/.conky/weather/forecast | fold -s -w 28}
${voffset 2}#
${color1}${hr 1}${color2}
${font conkyweather:size=32}${lua_parse conky_set_icon 5}${color}${font}
${voffset -42}${goto 52}${exec sed -n '5p' ~/.conky/weather/forecast | fold -s -w 28}
${voffset 2}#
${color1}${hr 1}${color3}
${font ubuntu:size=6}last update ${time %e %B %Y %H:%M}
```

---

### Post by Habitual on 2015-01-05
post your conky config file.

---

### Post by CantankRus on 2015-01-05
Wouldn't you need to use **execp** and then replace every instance of a "**\n**"
created by fold with a "**\n${goto 52}**"?
eg
```
${goto 52}${[COLOR="#FF0000"]execp[/COLOR] sed -n '1p' ~/.conky/weather/forecast | fold -s -w 28 | **[COLOR="#FF0000"]sed ':a;N;$!ba;s/\n/\n${goto 52}/g'[/COLOR]**}
```

Terminal output showing what conky would now parse...
```
[COLOR="#008000"]glen@Trusty:~$[/COLOR] **sed -n '1p' ~/.conky/weather/forecast | fold -s -w 28 | [COLOR="#FF0000"]sed ':a;N;$!ba;s/\n/\n${goto 52}/g'[/COLOR]**
This Afternoon: Occasional 
${goto 52}light snow after 5pm. 
${goto 52}Cloudy and cold, with a 
${goto 52}high near 4°.  Wind chill 
${goto 52}values as low as -13°.  
${goto 52}South wind 5 to 10 mph. 
${goto 52}Chance of precipitation is 
${goto 52}40%.
```
I don't ever recall fold working in conky as you describe.

---

### Post by mjjohanson on 2015-01-06
[**[COLOR=#000000][/COLOR]**]("http://ubuntuforums.org/member.php?u=1938181")Thank you, CantankRus, for a way to make it work. Before 14.04 I ran 12.04 and before that a 10.? and until now it has worked. Maybe it wasn't supposed to, but there ya go. Thanks, again, for the insight.

---

