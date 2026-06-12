---
title: "Conky background image"
date: 2008-06-01
forum: General Help
---

### Post by colddayinapril on 2008-06-01
Anyone know if there's a way to set conkys background to a pixmap or png file?

If it helps, here's my conky script:

```
background yes
use_xft yes
xftfont DejaVu Sans Mono:size=10
xftalpha 0.8
out_to_console no
update_interval 1.0
total_run_times 0
draw_shades no

# Create own window instead of using desktop (required in nautilus)
own_window yes

# If own_window is yes, you may use type normal, desktop or override
own_window_type desktop

# Use pseudo transparency with own_window?
own_window_transparent no

# Background color

#Alignment
alignment top_left



double_buffer yes
default_color #ffffff
alignment top_left
gap_x 2
gap_y 2
#no_buffers yes
use_spacer yes

TEXT
   CPU-1: ${cpu cpu1}% ${cpubar 8,64 cpu1}   |   Memory: $mem/ $memmax${membar 8,64}   |   Up Speed:   ${upspeed eth0}k/s ${upspeedgraph eth0 8,64}   |   Root: ${fs_used /}/ ${fs_size /}   |     ${time %l:%M %p}   
   CPU-2: ${cpu cpu2}% ${cpubar 8,64 cpu2}   |   Swap:   $swap/ $swapmax${swapbar 8,64}   |   Down Speed: ${downspeed eth0}k/s ${downspeedgraph eth0 8,64}   |   Home: ${fs_used /home}/ ${fs_size /home}   |   ${time %B %e, %G}   
```

---

### Post by jbaerbock on 2008-06-01
I've been trying to figure this out for a long time, but alas not even close yet lol.

---

### Post by w.yu on 2009-07-16
Sorry for rezzing, but in case you still want to know, now possible:-

[http://conky.linux-hardcore.com/?page_id=1154](http://conky.linux-hardcore.com/?page_id=1154)

configure conky with imlib2,

[http://conky.wikia.com/wiki/Conky_and_Images_(Imlib2)]("http://conky.wikia.com/wiki/Conky_and_Images_%28Imlib2%29")

works so far for me. now to make a translucent image. =)

---

