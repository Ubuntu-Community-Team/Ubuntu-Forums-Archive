---
title: "desktop memo"
date: 2015-11-01
forum: General Help
---

### Post by trav9595 on 2015-11-01
anyone know how I can post small text reminders on my desktop screen???? and have them stay until I delete them??

---

### Post by ajgreeny on 2015-11-01
The package xpad can be setup to work this way in 14.10 onwards, but not in 14.04 as far as I can see.  Very simple and small.
Other ways to do this that I have found but are more complicated and I suppose only necessary if using 14.04, but are just interesting.

Add your text editor opening a **note.txt** file(use mousepad or leafpad depending on the Xubuntu version) to your startup applications list with command ```
mousepad /home/*username*/note,txt
```  It will open just as you want it to.  Just edit that note.txt file with your reminder message and when you don't need it again remove that command from the startup applications.

There is also another way using conky and the same note.txt file which is a bit classier looking but does exactly the same job, it just looks clever.  
Install **conky** and create a txt file in your home folder named .conkyrc as the configuration file for conky with following content.
```
alignment top_left
background no
border_width 1
cpu_avg_samples 2
default_color white
default_outline_color white
default_shade_color white
draw_borders no
draw_graph_borders yes
draw_outline no
draw_shades no
use_xft yes
xftfont DejaVu Sans Mono:size=12
gap_x 5
gap_y 60
minimum_size 5 5
net_avg_samples 2
no_buffers yes
out_to_console no
out_to_stderr no
extra_newline no
own_window yes
own_window_class Conky
own_window_type desktop
stippled_borders 0
update_interval 1.0
uppercase no
use_spacer none
show_graph_scale no
show_graph_range no
TEXT
${font Ubuntu:size=20}${exec cat /home/*username*/note.txt}
```
Just edit this to give you the text colour and position on desktop you want, and use the full pathway of the note.txt file in that bottom line.  Add command**conky -p 10** to your startup applications; the -p delays it for 10 seconds to make sure the DE is running fully.  Now the text in your note.txt file will show on the desktop and you can either remove the text from the note.txt file when you no longer need to or just remove conky from the startup applications.

I like conky a lot, and use it for a display of info on my desktop with a fairly complicated .conkyrc file. Be warned, however; conky is frustrating at times and can be a real time-waster while you try to get things displaying as you want, but it can be rewarding when it does work.

---

