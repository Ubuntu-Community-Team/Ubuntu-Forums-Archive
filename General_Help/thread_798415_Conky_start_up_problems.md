---
title: "Conky start up problems"
date: 2008-05-18
forum: General Help
---

### Post by g0tanks on 2008-05-18
[http://i27.tinypic.com/6s593t.png](http://i27.tinypic.com/6s593t.png)
When I run Conky from Run Application, I get the window in the screenshot, but when I run it from terminal I get the bar at the bottom. Now I want Conky to start up when I login, so I added Conky to Sessions. But if I do that it will start up, but the window will start instead of the bar at the bottom that I want. Can anyone help me?

---

### Post by tturrisi on 2008-05-18
You need to post your conkyrc file.

---

### Post by g0tanks on 2008-05-18
```

double_buffer yes
no_buffers yes

own_window yes
own_window_transparent yes
own_window_type normal
own_window_hints undecorate,sticky,skip_taskbar,skip_pager 



draw_borders no
draw_shades no
draw_graph_borders no
draw_outline no

gap_x 1
gap_y 788

update_interval 1

minimum_size 1360  10


use_xft no
use_spacer yes
use_xft yes
xftfont HandelGotD:pixelsize=10


mpd_host localhost
mpd_port 6600

TEXT
${voffset -1}CPU: ${color E8BCA7}${font}${cpu}% ${color 292929} ${color} Processes: ${color E8BCA7}${font}${running_processes}${color 292929} ${color} RAM: ${color E8BCA7}${font}${mem}${color} | Uptime: ${color E8BCA7}${font}${uptime_short}${color E8BCA7} | ${color E8BCA7}${font}${downspeed eth0} kb/s ${color} ${totaldown eth0} down${color 292929}  ${color} ${color E8BCA7}${upspeed eth0} kb/s ${color} ${totalup eth0} up${color 292929}
```

By the way, what do I need to change to remove the border? draw_borders no
doesn't seem to do anything.

Thanks.

---

