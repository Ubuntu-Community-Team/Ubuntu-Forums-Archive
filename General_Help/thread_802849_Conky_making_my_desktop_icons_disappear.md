---
title: "Conky making my desktop icons disappear"
date: 2008-05-21
forum: General Help
---

### Post by eberndl on 2008-05-21
Hi,

I'm playing with conky, and although I have several problems, this is my greatest:  When Conky loads, my shared drive and terminal icons disappear.  I can see them again if I hover the mouse over them (see attached image), but they disappear again after a couple seconds.

Here's the screen shot: 
[IMG]http://farm3.static.flickr.com/2058/2511978123_79782fc3ef_b.jpg[/IMG]

and here's my conky:
> # UBUNTU-CONKY
# A comprehensive conky script, configured for use on
# Ubuntu / Debian Gnome, without the need for any external scripts.
#
# 
#

# Create own window instead of using desktop (required in nautilus)
own_window no
#own_window_type override
#own_window_transparent yes
#own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer yes
use_xft no

# Update interval in seconds
update_interval 3.0

# Minimum size of text area
# minimum_size 250 5

# Draw shades?
draw_shades no

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no
font arial
uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 3

# border margins
border_margin 9

# border width
border_width 10

# Default colors and also border colors, grey90 == #e5e5e5
default_color white
default_outline_color black

own_window_colour brown
own_window_transparent yes

# Text alignment, other possible values are commented
#alignment top_left
alignment top_middle
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 9
gap_y 20

# stuff after 'TEXT' will be formatted on screen

TEXT
$color
${alignc}$nodename has been up for $uptime ${freq}MHz   Load: ${loadavg}   

${alignc}NAME             PID       CPU%      MEM%
${alignc}${top name 1} ${top pid 1}   ${top cpu 1}    ${top mem 1}
${alignc}${top name 2} ${top pid 2}   ${top cpu 2}    ${top mem 2}

${alignc}RAM: $memperc% | Swap: $swapperc% | Root:  ${fs_free_perc /}% 



Anyone have an idea what I can do so my icons show up again??

Thanks!!!

---

### Post by mondayrocks on 2008-05-21
I just installed conky and had a similar problem. It looks like the formatting of your conky file simply puts it over the icons. You should just move the icons from out from under it or move the transparent conky to the side or something?

---

### Post by ShodanjoDM on 2008-05-21
Try this:

```
# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
own_window_transparent yes
#own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
```

---

### Post by rnjn.sinha on 2008-05-22
From conky FAQ

> 
Conky is designed to draw to the root desktop window. However, there are several other applications which like drawing to the root desktop window. 

Nautilus is one of them. Hence as one of the reply already states, you will have to run conky in its own window.

---

### Post by kerry_s on 2008-05-22
you need to set the size of the area around the text:

```
# Minimum size of text area
# minimum_size 250 5

```

you have it commented out, so it uses the full space on both sides of the text.

---

