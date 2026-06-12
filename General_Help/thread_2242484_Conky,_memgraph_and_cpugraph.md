---
title: "Conky, memgraph and cpugraph"
date: 2014-09-02
forum: General Help
---

### Post by vasa1 on 2014-09-02
The lower left corners of both memgraph and cpugraph seem incomplete, slightly nibbled away. Any idea why and how to have sharp corners?

This is my .conkyrc:```
# Conky, a system monitor, based on torsmo
#

use_spacer right
double_buffer yes
alignment top_left
background no
default_color 555555
use_xft yes
xftfont Ubuntu Mono:bold:size=16
gap_x 15
gap_y 9
minimum_size 505 150
no_buffers yes
out_to_console no
out_to_stderr no
extra_newline no
own_window yes
own_window_class Conky
own_window_type desktop
own_window_type normal 
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager  
own_window_transparent no
update_interval 1.0
uppercase no
use_spacer none

TEXT
${time %a, %d %b} ${color B3492B}${time %H:%M}$color ${utime (%H:%M)} ${acpitemp}${iconv_start UTF-8 ISO_8859-1}°${iconv_stop}C ${execpi 300 python ~/bin/chimak.py}/${execpi 3600 python ~/bin/negchs.py}/${execpi 240 python ~/bin/aes.py}/ ${memgraph 15,25 555555 555555} ${cpugraph 15,25 008000 008000}

```

---

### Post by CantankRus on 2014-09-02
I'm not seeing the same running your conky in unity.

---

### Post by vasa1 on 2014-09-02
> **CantankRus said:**
> I'm not seeing the same running your conky in unity.Lucky you! Maybe you have better graphics? Mine is "integrated"; no separate graphics card :(

For now, I've worked around the issue by making the default color the same as the background color of my desktop.

---

### Post by vasa1 on 2014-09-26
I came across **draw_graph_borders** and set that to **no**.

---

