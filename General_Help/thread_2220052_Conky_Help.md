---
title: "Conky Help"
date: 2014-04-26
forum: General Help
---

### Post by David_Aaron_Groves on 2014-04-26
I have a conky script that looks a bit like the Google Now launcher from Android. I have went to weather.yahoo.com and searched my city, Cincinnati, Ohio and I have gotten the number out of the URL for conky to grab my weather but conky keeps saying that the temperature is 22 degrees when it is in the 70's and Yahoo Weather says its in the 70's as well. What is going on. Ill post a screenshot and my .conkyrc config. Someone please help!



```
# Conky Google Now style #

# Conky settings #
background no
update_interval 1
double_buffer yes
no_buffers yes

# Window specifications #
own_window yes
own_window_type normal
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
own_window_title 
own_window_colour FFFFFF

minimum_size 300

# Alignment #
alignment tr
gap_x 100
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
default_color 666666

color1 0099CC
color2 9933CC
color3 669900
color4 FF8800
color5 CC0000
color6 AAAAAA
color7 DDDDDD

TEXT
${execi 300 curl -s "http://weather.yahooapis.com/forecastrss?w=2380358&u=c" -o ~/.cache/weather.xml}${font Open Sans Light:size=15}${execi 300 grep "yweather:location" ~/.cache/weather.xml | grep -o "city=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*"}, ${execi 300 grep "yweather:location" ~/.cache/weather.xml | grep -o "country=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*"}${font}
${font Open Sans Light:size=70}${alignr}${execi 300 grep "yweather:condition" ~/.cache/weather.xml | grep -o "temp=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*"}°${font}${voffset -35}
${execi 300 cp -f ~/.conky-google-now/$(grep "yweather:condition" ~/.cache/weather.xml | grep -o "code=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*").png ~/.cache/weather.png}${image ~/.cache/weather.png -p 0,45 -s 60x60}
${execi 300 grep "yweather:condition" ~/.cache/weather.xml | grep -o "text=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | tr '[a-z]' '[A-Z]'}
${image ~/.conky-google-now/wind.png -p 0,135 -s 15x15}${goto 35}${execi 300 grep "yweather:wind" ~/.cache/weather.xml | grep -o "speed=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*"}${execi 300 grep "yweather:units" ~/.cache/weather.xml | grep -o "speed=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*"}
${image ~/.conky-google-now/humidity.png -p 0,155 -s 15x15}${goto 35}${execi 300 grep "yweather:atmosphere" ~/.cache/weather.xml | grep -o "humidity=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*"}%${voffset 15}
${goto 18}${execi 300 grep "yweather:forecast" ~/.cache/weather.xml | grep -o "day=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==1' | tr '[a-z]' '[A-Z]'}${goto 88}${execi 300 grep "yweather:forecast" ~/.cache/weather.xml | grep -o "day=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==2' | tr '[a-z]' '[A-Z]'}${goto 158}${execi 300 grep "yweather:forecast" ~/.cache/weather.xml | grep -o "day=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==3' | tr '[a-z]' '[A-Z]'}${goto 228}${execi 300 grep "yweather:forecast" ~/.cache/weather.xml | grep -o "day=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==4' | tr '[a-z]' '[A-Z]'}${goto 298}${execi 300 grep "yweather:forecast" ~/.cache/weather.xml | grep -o "day=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==5' | tr '[a-z]' '[A-Z]'}
${execi 300 cp -f ~/.conky-google-now/$(grep "yweather:forecast" ~/.cache/weather.xml | grep -o "code=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==1').png ~/.cache/weather-1.png}${image ~/.cache/weather-1.png -p 0,210 -s 30x30}${execi 300 cp -f ~/.conky-google-now/$(grep "yweather:forecast" ~/.cache/weather.xml | grep -o "code=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==2').png ~/.cache/weather-2.png}${image ~/.cache/weather-2.png -p 70,210 -s 30x30}${execi 300 cp -f ~/.conky-google-now/$(grep "yweather:forecast" ~/.cache/weather.xml | grep -o "code=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==3').png ~/.cache/weather-3.png}${image ~/.cache/weather-3.png -p 140,210 -s 30x30}${execi 300 cp -f ~/.conky-google-now/$(grep "yweather:forecast" ~/.cache/weather.xml | grep -o "code=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==4').png ~/.cache/weather-4.png}${image ~/.cache/weather-4.png -p 210,210 -s 30x30}${execi 300 cp -f ~/.conky-google-now/$(grep "yweather:forecast" ~/.cache/weather.xml | grep -o "code=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==5').png ~/.cache/weather-5.png}${image ~/.cache/weather-5.png -p 280,210 -s 30x30}${voffset 20}
${goto 20}${execi 300 grep "yweather:forecast" ~/.cache/weather.xml | grep -o "high=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==1'}°${goto 90}${execi 300 grep "yweather:forecast" ~/.cache/weather.xml | grep -o "high=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==2'}°${goto 160}${execi 300 grep "yweather:forecast" ~/.cache/weather.xml | grep -o "high=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==3'}°${goto 230}${execi 300 grep "yweather:forecast" ~/.cache/weather.xml | grep -o "high=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==4'}°${goto 300}${execi 300 grep "yweather:forecast" ~/.cache/weather.xml | grep -o "high=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==5'}°
${goto 20}${execi 300 grep "yweather:forecast" ~/.cache/weather.xml | grep -o "low=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==1'}°${goto 90}${execi 300 grep "yweather:forecast" ~/.cache/weather.xml | grep -o "low=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==2'}°${goto 160}${execi 300 grep "yweather:forecast" ~/.cache/weather.xml | grep -o "low=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==3'}°${goto 230}${execi 300 grep "yweather:forecast" ~/.cache/weather.xml | grep -o "low=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==4'}°${goto 300}${execi 300 grep "yweather:forecast" ~/.cache/weather.xml | grep -o "low=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==5'}°
${color7}${hr}${color}
${if_existing /proc/net/route wlan0}
${color1}Up:${color} ${color3}${upspeed wlan0}${color}${alignr}${color1}Down:${color} ${color3}${downspeed wlan0}${color}
${upspeedgraph wlan0 75,135 FF8800 FF8800}${alignr}${downspeedgraph wlan0 75,135 FF8800 FF8800}
${color1}Sent:${color} ${color2}${totalup wlan0}${color}${alignr}${color1}Received:${color} ${color2}${totaldown wlan0}${color}
${else}${if_existing /proc/net/route wlan1}
${color1}Up:${color} ${color3}${upspeed wlan1}${color}${alignr}${color1}Down:${color} ${color3}${downspeed wlan1}${color}
${upspeedgraph wlan1 75,135 FF8800 FF8800}${alignr}${downspeedgraph wlan1 75,135 FF8800 FF8800}
${color1}Sent:${color} ${color2}${totalup wlan1}${color}${alignr}${color1}Received:${color} ${color2}${totaldown wlan1}${color}
${else}${if_existing /proc/net/route eth0}
${color1}Up:${color} ${color3}${upspeed eth0}${color}${alignr}${color1}Down:${color} ${color3}${downspeed eth0}${color}
${upspeedgraph eth0 75,135 FF8800 FF8800}${alignr}${downspeedgraph eth0 75,135 FF8800 FF8800}
${color1}Sent:${color} ${color2}${totalup eth0}${color}${alignr}${color1}Received:${color} ${color2}${totaldown eth0}${color}
${else}${if_existing /proc/net/route eth1}
${color1}Up:${color} ${color3}${upspeed eth1}${color}${alignr}${color1}Down:${color} ${color3}${downspeed eth1}${color}
${upspeedgraph eth1 75,135 FF8800 FF8800}${alignr}${downspeedgraph eth1 75,135 FF8800 FF8800}
${color1}Sent:${color} ${color2}${totalup eth1}${color}${alignr}${color1}Received:${color} ${color2}${totaldown eth1}${color}
${else}${if_existing /proc/net/route ppp0}
${color1}Up:${color} ${color3}${upspeed ppp0}${color}${alignr}${color1}Down:${color} ${color3}${downspeed ppp0}${color}
${upspeedgraph ppp0 75,135 FF8800 FF8800}${alignr}${downspeedgraph ppp0 75,135 FF8800 FF8800}
${color1}Sent:${color} ${color2}${totalup ppp0}${color}${alignr}${color1}Received:${color} ${color2}${totaldown ppp0}${color}
${else}${if_existing /proc/net/route ppp1}
${color1}Up:${color} ${color3}${upspeed ppp1}${color}${alignr}${color1}Down:${color} ${color3}${downspeed ppp1}${color}
${upspeedgraph ppp1 75,135 FF8800 FF8800}${alignr}${downspeedgraph ppp1 75,135 FF8800 FF8800}
${color1}Sent:${color} ${color2}${totalup ppp1}${color}${alignr}${color1}Received:${color} ${color2}${totaldown ppp1}${color}
${else}${if_existing /proc/net/route usb0}
${color1}Up:${color} ${color3}${upspeed usb0}${color}${alignr}${color1}Down:${color} ${color3}${downspeed usb0}${color}
${upspeedgraph usb0 75,135 FF8800 FF8800}${alignr}${downspeedgraph usb0 75,135 FF8800 FF8800}
${color1}Sent:${color} ${color2}${totalup usb0}${color}${alignr}${color1}Received:${color} ${color2}${totaldown usb0}${color}
${else}${if_existing /proc/net/route usb1}
${color1}Up:${color} ${color3}${upspeed usb1}${color}${alignr}${color1}Down:${color} ${color3}${downspeed usb1}${color}
${upspeedgraph usb1 75,135 FF8800 FF8800}${alignr}${downspeedgraph usb1 75,135 FF8800 FF8800}
${color1}Sent:${color} ${color2}${totalup usb1}${color}${alignr}${color1}Received:${color} ${color2}${totaldown usb1}${color}
${else}
Network disconnected
${color6}Connect to a network to see statistics${color}
${voffset 75}
${endif}${endif}${endif}${endif}${endif}${endif}${voffset -30}
```

---

### Post by Habitual on 2014-04-26
```
curl -s "http://weather.yahooapis.com/forecastrss?w=2380358&u=c" -o ~/.cache/weather.xml
grep "temp=" ~/.cache/weather.xml
```

condition  text="Fair"  code="34"  temp="24"  date="Sat, 26 Apr 2014 12:51 pm EDT"

Offhand, I'd say that is Celsius.

[https://weather.yahoo.com/forecast/USOH0188_c.html](https://weather.yahoo.com/forecast/USOH0188_c.html) shows 75ºF

24ºC = 75.200ºF says [http://www.metric-conversions.org/temperature/celsius-to-fahrenheit.htm](http://www.metric-conversions.org/temperature/celsius-to-fahrenheit.htm)

If I 
```
curl -s "https://weather.yahoo.com/forecast/USOH0188_c.html" -o ~/.cache/weather.xml
```it has 
```
    <div class="temp">
        <span class="f"><span class="num">75</span><span class="deg">&deg;</span></span>
        <span class="c"><span class="num">24</span><span class="deg">&deg;</span></span>
```

---

### Post by David_Aaron_Groves on 2014-04-26
> **Habitual said:**
> ```
curl -s "http://weather.yahooapis.com/forecastrss?w=2380358&u=c" -o ~/.cache/weather.xml
grep "temp=" ~/.cache/weather.xml
```

condition  text="Fair"  code="34"  temp="24"  date="Sat, 26 Apr 2014 12:51 pm EDT"

Offhand, I'd say that is Celsius.

[https://weather.yahoo.com/forecast/USOH0188_c.html](https://weather.yahoo.com/forecast/USOH0188_c.html) shows 75ºF

24ºC = 75.200ºF says [http://www.metric-conversions.org/temperature/celsius-to-fahrenheit.htm](http://www.metric-conversions.org/temperature/celsius-to-fahrenheit.htm)

If I 
```
curl -s "https://weather.yahoo.com/forecast/USOH0188_c.html" -o ~/.cache/weather.xml
```it has 
```
    <div class="temp">
        <span class="f"><span class="num">75</span><span class="deg">&deg;</span></span>
        <span class="c"><span class="num">24</span><span class="deg">&deg;</span></span>
```


Ok so how do I fix it? I am so confused.

---

### Post by Habitual on 2014-04-27
Sorry, I don't know, I gave up coding conky ages ago.
Don't despair. someone will come along...

---

### Post by pj5081 on 2014-05-24
Change the C to an F.

```
[COLOR=#000000][FONT=Ubuntu Mono]curl -s "http://weather.yahooapis.com/forecastrss?w=2380358&u=f" -o ~/.cache/weather.xml[/FONT][/COLOR]
```

FWIW, I've just been playing with the Conky config mentioned [here]("http://zagortenay333.deviantart.com/art/Conky-Harmattan-426662366").  You might want to look at his code in his .conkyrc files.  I'm using the "Transparent" "God Mode" theme in Mint 17 RC.  It works, so you might want to use Harmattan's code as a template.

---

