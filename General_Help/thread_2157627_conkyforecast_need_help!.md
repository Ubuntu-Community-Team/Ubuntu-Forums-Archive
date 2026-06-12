---
title: "conkyforecast need help!"
date: 2013-06-26
forum: General Help
---

### Post by Baldrick_NZ on 2013-06-26
Hi all,

After following the tutorial below, I've had great success in getting the time/date to work, but unable to get the weather part to go. 

I've used the default settings, thinking I could change them later, but even the default settings don't render results.

[http://www.pimpingthepenguin.com/2012/11/simple-time-and-weather-conky-desktop.html](http://www.pimpingthepenguin.com/2012/11/simple-time-and-weather-conky-desktop.html)

Any help to get the weather part going would be very much apprieciated!

Baldrick

---

### Post by MidnightGrey on 2013-06-26
what does it say when you run conky from terminal?

---

### Post by Baldrick_NZ on 2013-06-26
> **MidnightGrey said:**
> what does it say when you run conky from terminal?

Thanks for your reply.

```
baldrick@baldrick:~$ conky
Conky: desktop window (1200025) is subwindow of root window (99)
Conky: window type - normal
Conky: drawing to created window (0x2800001)
Conky: drawing to double buffer
ERROR: Config data file /home/baldrick/.conkyForecast.config not found, using defaults (Registration info is needed though)
Traceback (most recent call last):
  File "/usr/share/conkyforecast/conkyForecast.py", line 1698, in <module>
    main()
  File "/usr/share/conkyforecast/conkyForecast.py", line 1694, in main
    forecastinfo = ForecastInfo(options)
  File "/usr/share/conkyforecast/conkyForecast.py", line 592, in __init__
    socket.setdefaulttimeout(self.config.CONNECTION_TIMEOUT)
AttributeError: 'NoneType' object has no attribute 'CONNECTION_TIMEOUT'
ERROR: Config data file /home/baldrick/.conkyForecast.config not found, using defaults (Registration info is needed though)
Traceback (most recent call last):
  File "/usr/share/conkyforecast/conkyForecast.py", line 1698, in <module>
    main()
  File "/usr/share/conkyforecast/conkyForecast.py", line 1694, in main
    forecastinfo = ForecastInfo(options)
  File "/usr/share/conkyforecast/conkyForecast.py", line 592, in __init__
    socket.setdefaulttimeout(self.config.CONNECTION_TIMEOUT)
AttributeError: 'NoneType' object has no attribute 'CONNECTION_TIMEOUT'
ERROR: Config data file /home/baldrick/.conkyForecast.config not found, using defaults (Registration info is needed though)
Traceback (most recent call last):
  File "/usr/share/conkyforecast/conkyForecast.py", line 1698, in <module>
    main()
  File "/usr/share/conkyforecast/conkyForecast.py", line 1694, in main
    forecastinfo = ForecastInfo(options)
  File "/usr/share/conkyforecast/conkyForecast.py", line 592, in __init__
    socket.setdefaulttimeout(self.config.CONNECTION_TIMEOUT)
AttributeError: 'NoneType' object has no attribute 'CONNECTION_TIMEOUT'


```

---

### Post by MidnightGrey on 2013-06-26
can you also paste your .conkyrc file while you're at it.
Well, untill i see the .conkyrc file; the obvious problem seems to be this error:
> 

ERROR: Config data file /home/baldrick/.conkyForecast.config not found

---

### Post by Baldrick_NZ on 2013-06-26
> **MidnightGrey said:**
> can you also paste your .conkyrc file while you're at it.
Well, untill i see the .conkyrc file; the obvious problem seems to be this error:

Thanks again!

```
# Modified by RandyNose(.com) for simple desktop time and temp #
# Original code swipped from Conky Metro Clock by Satya #
# satya164.deviantart.com #


# Conky settings #
background no
update_interval 1

override_utf8_locale yes

double_buffer yes
no_buffers yes

text_buffer_size 2048

# Window specifications #
own_window yes
own_window_class conky
own_window_transparent yes
own_window_hints undecorate,below,sticky,skip_taskbar,skip_pager

border_inner_margin 0
border_outer_margin 0

alignment bl
gap_x 100
gap_y 60

# Graphics settings #
draw_shades yes
draw_outline no
draw_borders no
draw_graph_borders no

# Text settings #
use_xft yes
xftalpha 0
text_buffer_size 2048

uppercase no

default_color FFFFFF


TEXT
${voffset 10}${font Ubuntu Light:size=40}${goto 550}${execi 600 conkyForecast --location=44107 --datatype=CN --refetch}${voffset -10}
${voffset 10}${font Ubuntu Light:size=50}${goto 550}${execi 1800 conkyForecast --location=44107 --datatype=CT --refetch}${voffset -10}${goto 875}${execi 1800 conkyForecast --location=44107 -u --datatype=HT --refetch}
${voffset 10}${font Ubuntu Condensed:size=30}${time %A}${font}${voffset -10}
${voffset 10}${font Ubuntu Condensed:size=30}${time %B} ${time %e}${font}${voffset -10}
${voffset 10}${font Ubuntu Condensed:size=70}${time %R}${font}${voffset -10}
```

---

### Post by MidnightGrey on 2013-06-26
> ${execi 600 conkyForecast --location=44107 --datatype=CN --refetch}

Well the location in your/and the website's conkyrc is set to a US postcode(44107) but in the instructions for conkyforcast it looks like the syntax is something like this SFXX0007.
That is a 4 character code followed by a 4 digit code to determine location. Why dont you try to set that correctly first.
Additionally you may want to try some of the templates provided in the default installation of conkyforcast. (located here: /usr/share/conkyforecast/test).

The problem with downloading someones customised scripts is that they may work flawlessly for that person but not for you and you have no clue usually what they have done on their end.

---

### Post by Baldrick_NZ on 2013-06-27
I tried that with my local 'code' but the weather part of conky still doesn't show up on screen, just the time and date.

Here's what I get when I run in terminal...

```
baldrick@baldrick:~$ conky
Conky: desktop window (1400025) is subwindow of root window (99)
Conky: window type - normal
Conky: drawing to created window (0x2e00001)
Conky: drawing to double buffer
ERROR: Config data file /home/baldrick/.conkyForecast.config not found, using defaults (Registration info is needed though)
Traceback (most recent call last):
  File "/usr/share/conkyforecast/conkyForecast.py", line 1698, in <module>
    main()
  File "/usr/share/conkyforecast/conkyForecast.py", line 1694, in main
    forecastinfo = ForecastInfo(options)
  File "/usr/share/conkyforecast/conkyForecast.py", line 592, in __init__
    socket.setdefaulttimeout(self.config.CONNECTION_TIMEOUT)
AttributeError: 'NoneType' object has no attribute 'CONNECTION_TIMEOUT'
ERROR: Config data file /home/baldrick/.conkyForecast.config not found, using defaults (Registration info is needed though)
Traceback (most recent call last):
  File "/usr/share/conkyforecast/conkyForecast.py", line 1698, in <module>
    main()
  File "/usr/share/conkyforecast/conkyForecast.py", line 1694, in main
    forecastinfo = ForecastInfo(options)
  File "/usr/share/conkyforecast/conkyForecast.py", line 592, in __init__
    socket.setdefaulttimeout(self.config.CONNECTION_TIMEOUT)
AttributeError: 'NoneType' object has no attribute 'CONNECTION_TIMEOUT'
ERROR: Config data file /home/baldrick/.conkyForecast.config not found, using defaults (Registration info is needed though)
Traceback (most recent call last):
  File "/usr/share/conkyforecast/conkyForecast.py", line 1698, in <module>
    main()
  File "/usr/share/conkyforecast/conkyForecast.py", line 1694, in main
    forecastinfo = ForecastInfo(options)
  File "/usr/share/conkyforecast/conkyForecast.py", line 592, in __init__
    socket.setdefaulttimeout(self.config.CONNECTION_TIMEOUT)
AttributeError: 'NoneType' object has no attribute 'CONNECTION_TIMEOUT'



```

and my updated .conkyrc file...

```
# Modified by RandyNose(.com) for simple desktop time and temp #
# Original code swipped from Conky Metro Clock by Satya #
# satya164.deviantart.com #


# Conky settings #
background no
update_interval 1

override_utf8_locale yes

double_buffer yes
no_buffers yes

text_buffer_size 2048

# Window specifications #
own_window yes
own_window_class conky
own_window_transparent yes
own_window_hints undecorate,below,sticky,skip_taskbar,skip_pager

border_inner_margin 0
border_outer_margin 0

alignment bl
gap_x 100
gap_y 60

# Graphics settings #
draw_shades yes
draw_outline no
draw_borders no
draw_graph_borders no

# Text settings #
use_xft yes
xftalpha 0
text_buffer_size 2048

uppercase no

default_color FFFFFF


TEXT
${voffset 10}${font Ubuntu Light:size=40}${goto 550}${execi 600 conkyForecast --location=NZXX0667 --datatype=CN --refetch}${voffset -10}
${voffset 10}${font Ubuntu Light:size=50}${goto 550}${execi 1800 conkyForecast --location=NZXX0667 --datatype=CT --refetch}${voffset -10}${goto 875}${execi 1800 conkyForecast --location=NZXX0667 -u --datatype=HT --refetch}
${voffset 10}${font Ubuntu Condensed:size=30}${time %A}${font}${voffset -10}
${voffset 10}${font Ubuntu Condensed:size=30}${time %B} ${time %e}${font}${voffset -10}
${voffset 10}${font Ubuntu Condensed:size=70}${time %R}${font}${voffset -10}


```

I would have thought something would have shown up on screen where the weather is supposed to show - even if it was an error message?

Thanks again for your help, much appreciated!

---

### Post by Baldrick_NZ on 2013-06-27
Doing a bit of googling, it would appear my problem is related to weather.com no longer operate a free api applicable to my area. This would probably explain why it doesn't show up.

So, I now have three further questions...

1/ How hard would it be to dump references to weather.com and incorporate world weather online instead? I have an active api for them... And if that's not possible (or too hard)

2/ How can I reduce the size of the time/date conky window? I'd like to reduce/eliminate the effect in the pic attached when my desktop slideshow pic changes... It does change to the new background after 3-4secs, but would prefer it to be more instant.

3/ How can I move the time/date to the right hand side of the screen (right justified text), instead of on the left hand side?

Thanks!

---

### Post by MidnightGrey on 2013-06-27
To be honest you're probably better off asking in a forum dedicated to conky (if there is one), your questions are a bit beyond the scope of this forum (conky isn't even included in the default install of Ubuntu for instance), but to answer your questions as best as i can:

> 1/ How hard would it be to dump references to weather.com and  incorporate world weather online instead? I have an active api for  them... And if that's not possible (or too hard)
It looks like the url conkyforcast uses to pull down data is located inside this file /usr/share/conkyforcast/conkyForcast.config. How you would get it to work with world weather online i'm afraid i cant help you there.

> 
2/ How can I reduce the size of the time/date conky window? I'd like to  reduce/eliminate the effect in the pic attached when my desktop  slideshow pic changes... It does change to the new background after  3-4secs, but would prefer it to be more instant.
this has to do with your conky updates being out of sync with your wallpaper script. The best i could suggest is to try to sync them up by playing around with the *update_interval* setting? I don't use rotating wallpapers so i cant really help you there.
Also to reduce the size of your font, just play with the numbers inside .conkyrc. The 5 lines at the very bottom of the file are what gets displayed by conky.

> 3/ How can I move the time/date to the right hand side of the screen (right justified text), instead of on the left hand side?
You have to use the alignment setting (in .conkyrc) to manipulate where you want conky to be anchored. you can set the alignment like so:
```
alignment = middle_right
```
Possible choices include: <top_left,         top_right, top_middle, bottom_left, bottom_right,         bottom_middle, middle_left, middle_middle, middle_right>

---

