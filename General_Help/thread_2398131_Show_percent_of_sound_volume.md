---
title: "Show percent of sound volume"
date: 2018-08-07
forum: General Help
---

### Post by raleigh3 on 2018-08-07
I am trying to show the percent of my sound volume on my desktop.

  
Using 

```
amixer get Master
```

  ```
amixer: Unable to find simple control 'Master',0
  
```
pavucontrol works, but it causes the light for my webcam to be always on.
  
Any other way?

---

### Post by again? on 2018-08-08
Try...
```
amixer -c 1 -M -D pulse get Master | grep -m 1 -o -E [[:digit:]]+% | tr -d "%"
```

---

### Post by raleigh3 on 2018-08-08
Perfect.

Thanks.

---

### Post by raleigh3 on 2018-08-08
One other request.

I would like the % that is output to show right next to the percentage of the volume.

I tried to figure out the grep part, but it was too complex for me.

```
cd /home/andy/Downloads
#echo "Sound Volume is" >>  %Volume.txt
amixer -c 1 -M -D pulse get Master | grep -m 1 -o -E [[:digit:]]+% | tr -d "%" >> %Volume.txt
echo "%" >> %Volume.txt
gxmessage -fg red -font 'sans 20' -timeout 3 -file %Volume.txt -geometry "600x200"
rm %Volume.txt
```

---

### Post by again? on 2018-08-08
Remove the last piped **tr** command.
ie
```
amixer -c 1 -M -D pulse get Master | grep -m 1 -o -E [[:digit:]]+%
```
```
[B][COLOR="#006400"]glen@Bionic:~$[/COLOR] amixer -c 1 -M -D pulse get Master | grep -m 1 -o -E [[:digit:]]+%
100%
```[/B]

---

### Post by raleigh3 on 2018-08-08
Thanks.

---

### Post by again? on 2018-08-08
No problem.
FYI, conky has an inbuilt variable to display Pulseaudio's default sink volume percentage.
You can configure the conky window to be transparent and above other windows.
You can set it as a permanent desktop widget or display for a set period and then close(as in attached gif).

**.conkyrc**
```
background no
update_interval 1 
total_run_times 10

use_xft yes
xftfont Droid Sans:bold:size=12
alignment bl
xftalpha 1.0
own_window yes
own_window_type normal
own_window_transparent yes
own_window_colour blue
own_window_hints undecorated,above,skip_taskbar,skip_pager,sticky

double_buffer yes
draw_shades yes
draw_outline no
draw_borders no
#stippled_borders 10
gap_y 100
gap_x 155

#default_shade_color black
#default_outline_color purple
default_color red
use_spacer none
no_buffers yes
uppercase no



text_buffer_size 512
override_utf8_locale yes

minimum_size 50 10  
maximum_width 50
#use_spacer left


imlib_cache_size 0
imlib_cache_flush_interval 900

TEXT
${pa_sink_volume}%
```

---

### Post by raleigh3 on 2018-08-08
Thanks.

---

