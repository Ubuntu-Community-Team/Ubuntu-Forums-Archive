---
title: "Conky and weather forecast"
date: 2013-06-03
forum: General Help
---

### Post by Myst1234 on 2013-06-03
Greetings all,

 I've been reading up on, and messing around with conky for the last few days. I've been through countless threads on here about conky, and I still have 3 issues. 

1. I need to change the overall color of the set up

2. I need to move the entire setup down some

3. I cannot get the weather working with conkyforecast. All the docs I've seen point me to a specific page that does not load, and is "Not Found" through the main site.

. This was the main thread I was going through [http://ubuntuforums.org/showthread.php?t=867076&highlight=TO%3A+Beginners+Guide+Setting+Conky](http://ubuntuforums.org/showthread.php?t=867076&highlight=TO%3A+Beginners+Guide+Setting+Conky)  and this one for weather [http://ubuntuforums.org/showthread.php?t=869328](http://ubuntuforums.org/showthread.php?t=869328)

Just so the basics are out of the way -

I installed conky with 

> sudo apt-get install conky-all

Got the repository, conkyforecast and installed the appropriate fonts.

I have a Conky dir in my Home dir
inside that I have a conkymain file 

This is my conkyrc (conkymain)

> # Cherries
# by londonali1010

background no
update_interval 1
total_run_times 0
own_window yes
own_window_transparent yes
own_window_class Conky
own_window_hints undecorate,sticky,skip_pager,skip_taskbar,below
double_buffer yes
no_buffers yes
text_buffer_size 2048
cpu_avg_samples 2
net_avg_samples 2
override_utf8_locale yes
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders yes
use_spacer none
minimum_size 1000 0
alignment top_left
gap_x 12
gap_y 12
uppercase no
use_xft yes
xftfont DejaVu Sans:size=12
xftalpha 0.8
default_color d9b2ad

TEXT
${voffset 300}${font DejaVu Sans:size=24}${time %A}, ${time %d} ${time %B} ${time %Y}${font}
${battery_bar 8,720 BAT0}    
${voffset -8}${fs_bar 8,720 /}
${voffset -8}${goto 400}${cpubar 8,310 cpu}
${voffset -8}${goto 400}${font saxMono:size=9}${top pid 1}${font DejaVu Sans:size=8}${voffset -1} ${top name 1}${voffset 1}${goto 660}${font saxMono:size=9}${top cpu 1}
${goto 400}${font saxMono:size=9}${top pid 2}${font DejaVu Sans:size=8}${voffset -1} ${top name 2}${voffset 1}${goto 650}${font saxMono:size=9}${top cpu 2}
${goto 400}${font saxMono:size=9}${top pid 3}${font DejaVu Sans:size=8}${voffset -1} ${top name 3}${voffset 1}${goto 640}${font saxMono:size=9}${top cpu 3}
${goto 400}${font saxMono:size=9}${top pid 4}${font DejaVu Sans:size=8}${voffset -1} ${top name 4}${voffset 1}${goto 620}${font saxMono:size=9}${top cpu 4}
${goto 400}${membar 8, 260}
${goto 400}${font saxMono:size=9}${top_mem pid 1}${font DejaVu Sans:size=8}${voffset -1} ${top_mem name 1}${voffset 1}${goto 620}${font saxMono:size=9}${top_mem mem 1}
${goto 400}${font saxMono:size=9}${top_mem pid 2}${font DejaVu Sans:size=8}${voffset -1} ${top_mem name 2}${voffset 1}${goto 630}${font saxMono:size=9}${top_mem mem 2}
${goto 400}${font saxMono:size=9}${top_mem pid 3}${font DejaVu Sans:size=8}${voffset -1} ${top_mem name 3}${voffset 1}${goto 640}${font saxMono:size=9}${top_mem mem 3}
${goto 400}${font saxMono:size=9}${top_mem pid 4}${font DejaVu Sans:size=8}${voffset -1} ${top_mem name 4}${voffset 1}${goto 650}${font saxMono:size=9}${top_mem mem 4}${font}
${voffset -90}${font route3:size=160}${time %k}${font route3:size=100}${voffset -80}${goto 230}${time %M}${font}
${voffset -500}${execpi 360 conkyForecast --location=location id put in --template=/usr/share/conkyforecast/conkyForecast.template}


 I actually had a lot more errors, but as I was trying to explain them in this post, I figured them out, or read a solution. These left are the ones I cannot seem to figure or find out.

---

### Post by Myst1234 on 2013-06-03
Bump.

This was marked as solved as I figured things out, but have now come to ACTUAL issues I cannot solve.

**EDIT:** Figured out the color, working on moving the setup.

Any help on the weather would be great. Maybe an alternative to conkyforecadt? Or and updated link to a page to get the necessary ID?

**2ND EDIT: ** Thread closed. Answer is you can no longer get the forecast data for free. Unless you are willing to pay for it (monthly I think) conkyforecast is useless

---

### Post by Habitual on 2013-06-04
> **Myst1234 said:**
> conkyforecast is useless

Mine still works.
I keep weather as a separate conky 'widget' so it doesn't mess up my main conky layout.
It's difficult but not impossible. details on my c-li script are [here...]("http://www.bournetoraiseshell.com/article.php/20101101123337204")

```
Forecast for Wed, Jun 5 2013            Forecast for Thu, Jun 6 2013
----------------------------            ----------------------------
Low:           61°F                     Low:            61°F
High:          81°F                     High:           72°F
Humidity:      49%                      Humidity:       72%
Partly Cloudy                           Light Rain
Precipitation: 20%                      Precipitation:  60%
Sunrise:       5:51 AM                  Sunrise:        5:51 AM
Sunset:        8:52 PM                  Sunset:         8:52 PM
Daylight:      15:01                    Daylight:       15:01

Forecast for Fri, Jun 7 2013            Forecast for Sat, Jun 8 2013
----------------------------            ----------------------------
Low:           61°F                     Low:            55°F
High:          73°F                     High:           73°F
Humidity:      72%                      Humidity:       69%
Scattered Thunderstorms                 Cloudy
Precipitation: 40%                      Precipitation:  10%
Sunrise:       5:51 AM                  Sunrise:        5:51 AM
Sunset:        8:53 PM                  Sunset:         8:53 PM
Daylight:      15:02                    Daylight:       15:02
```
But I found an Xfce "Dev" XOAP_LICENCE_KEY
and have used it since at least 2012-10-21.

I think this XOAP_LICENCE_KEY is used for the Xfce weather applet(s).

[http://ubuntuforums.org/showthread.php?t=1156383](http://ubuntuforums.org/showthread.php?t=1156383)
[http://crunchbang.org/forums/viewtopic.php?id=19235](http://crunchbang.org/forums/viewtopic.php?id=19235)
and finally, the authoritative source
[http://conky.pitstop.free.fr/wiki/index.php5?title=ConkyForecast_help_%28en%29](http://conky.pitstop.free.fr/wiki/index.php5?title=ConkyForecast_help_%28en%29)

Good luck.

---

### Post by mörgæs on 2013-06-04
> **Myst1234 said:**
> 

**2ND EDIT: ** Thread closed. Answer is you can no longer get the forecast data for free. Unless you are willing to pay for it (monthly I think) conkyforecast is useless

Changed to SOLVED. Closing a thread has another meaning.

---

