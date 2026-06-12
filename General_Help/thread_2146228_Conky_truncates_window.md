---
title: "Conky truncates window"
date: 2013-05-17
forum: General Help
---

### Post by SASDOE2 on 2013-05-17
Hi all, 

I found this conky config on internet and changed it a bit but now it seems to cut the window for some reason. I have tried changing every single parameter to no avail. Here it is:

```
# — SETTINGS — #
background no
update_interval 1
cpu_avg_samples 2
net_avg_samples 2
double_buffer yes
no_buffers yes
text_buffer_size 1024
imlib_cache_size 0

# — WINDOW — #
# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_transparent yes #when set to 'no' conky appears against a black background
own_window_type dock
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
#These values set true transparancy
own_window_argb_visual yes
own_window_argb_value 100

# — BORDER — #
border_inner_margin 1
border_outer_margin 1
border_width 1

# — SIZE — #
minimum_size 800
maximum_width 2000
default_bar_size 800 40

# — ALIGNMENT — #
alignment left
gap_x 800
gap_y 10

# — GRAPHIC — #
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders yes
#default_shade_color
#default_outline_color 909090
#own_window_colour 808080

# — TEXT — #
use_xft yes
xftfont Dejavu Sans:size=8
xftalpha 1.0
uppercase no
override_utf8_locale yes
default_color 666

# — LUA — #
#lua_load ~/Conky/bgcolor/bg.lua
#lua_draw_hook_pre conky_draw_bg

# — Colors — #
color1 C18C24
color2 696969
color3 F0F8FF

TEXT

${voffset -3}${font Poky:size=20}M${goto 35}${font Impact:size=16}${voffset -3}$color1${memperc}$color${goto 65}%${font}${goto 90}${voffset -8}$color1${mem}$color${voffset 9}${goto 90}${membar 3,40}${voffset -8}
${voffset 12}${goto 5}${font StyleBats:size=14}i${font}${voffset -3} SWAP » $color1${swapperc}%$color  -  $color1$swap$color
${voffset -4}
```


Any ideas how I could fix this ?

Cheers !

---

### Post by SASDOE2 on 2013-05-18
I even copy pasted everything exluding the TEXT section from another config working perfectly, but still have the same result. What could be causing this ?

---

### Post by Cheesemill on 2013-05-18
Can you post a screenshot so we can see what your issue is please.

---

### Post by Habitual on 2013-05-18
> **SASDOE2 said:**
> I even copy pasted everything exluding the TEXT section from another config working perfectly is [QUOTE=]What could be causing this ?[/QUOTE] IMO. Every conkyrc I ever had, I had to go through it line by line with an open gedit and a couple of hundred ctrl+s (saves).

try ```
text_buffer_size 2048
```

---

### Post by SASDOE2 on 2013-05-19
Ok here comes the [screenshot]("http://neohomeserver.no-ip.org/cloud/public.php?service=files&t=5dc14efd2708a557a07f2ba4f30a3371") (I have different conky instances for different items on the desktop, the one giving me trouble is bottom left. It has the same exact "header" as the top right one.

I'll give text buffer a try and come back to you.

Also don't hesitate to tell me what you think of my desktop. Any ideas ? :)

---

### Post by Cheesemill on 2013-05-19
Try removing the ${voffset -4} line from the end of your file. It isn't doing anything except maybe causing your issue.

---

### Post by SASDOE2 on 2013-05-19
Cheers Cheesemill and Habitual, the ${voffset -4} was the culprit, works like a charm now!

---

### Post by SASDOE2 on 2013-05-19
Scratch that, I did a bit more tweaking (haven't finished getting it to my preference), and broke it again. Problem is I see no trailing voffset this time.. I am inclined to think i have another extra parameter somewhere but can't see where

---

