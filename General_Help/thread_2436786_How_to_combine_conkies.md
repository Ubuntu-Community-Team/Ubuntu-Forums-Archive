---
title: "How to combine conkies?"
date: 2020-02-13
forum: General Help
---

### Post by shmu26 on 2020-02-13
I have a .conkyrc file with this content
[HTML]background yesuse_xft yesxftfont Liberation Sans:size=9xftalpha 1update_interval 1.0total_run_times 0own_window yesown_window_transparent yesown_window_type normal
own_window_hints undecorated,below,skip_taskbar,skip_pagerdouble_buffer yesminimum_size 700 150maximum_width 500draw_shades nodraw_outline nodraw_borders nodraw_graph_borders no
default_shade_color 000000default_outline_color 828282alignment top_middlegap_x 20gap_y 50no_buffers yesuppercase nocpu_avg_samples 2override_utf8_locale yes
default_color edf1f6color1 2da83bcolor2 2da73bcolor3 db303e
own_window_argb_value 0own_window_colour 000000

own_window_argb_visual yesTEXT#time${offset 170}${color}${font Quicksand - U:pixelsize=70}${if_match "pmfix${time %p}" == "pmfix"}${time %k:%M}${else}${time %I:%M}${endif}${font}${font}${voffset -45}${offset 10}${font Roboto-Light - U:pixelsize=35}${time %P}${font}


#date${voffset 5}${offset 100}${color2}${font Droid:pixelsize=30}${time %A}${font}${goto 275}${voffset -18}${color2}${font Droid:pixelsize=30}  ${time %x}${font}
#sys${offset 130}${font Roboto-Light:pixelsize=20}${offset 9}${offset 9}${color1}hdd ${color}${offset 9}$color${fs_used_perc /}%${offset 9}${color1}mem ${offset 9}${color}${memperc}%${offset 9}${offset 9}${color1}cpu${offset 9}${color}${cpu}%${font}
[/HTML]

I want to add a second conky:
[HTML]conky.config = {    update_interval = 1,
    double_buffer = true,
    no_buffers = true,
    text_buffer_size = 2048,
    own_window = true,
    own_window_class = 'conky',
    own_window_colour = '050505',
    own_window_transparent = yes,
    own_window_argb_visual = true,
    own_window_argb_value = 5,
    own_window_hints = 'undecorated,below,sticky,skip_taskbar,skip_pager',
    own_window_type = 'dock',
    background = false,
    gap_y = 0,
    gap_x = 1,
    alignment = 'bottom_left',
    draw_shades = false,
    draw_outline = false,
    draw_borders = false,
    use_xft = true, --needed to show font correctly
    uppercase = true
}

conky.text = [[
${font Noto:size=13}${color cccccc}${time %I}:${time %M} ]][/HTML]

How to do that?

---

### Post by Frogs Hair on 2020-02-13
If your using a conkyrc you can number them conkyrc1,conkyrc2 and so on. Below is a startup applications script sample from OMG Ubuntu though a bit dated. 
```
#!/bin/sh
sleep 5
conky -q -c /home/YOURUSERNAME/.conky/conky1/conkyrc1 &
conky -q -c /home/YOURUSERNAME/.conky/conky2/conkyrc2 & exit

```

This is mine for a single conky. Sleep delays the startup and the number can be changed. 

```
#!/bin/bash
sleep 20 && conky;
```

---

### Post by shmu26 on 2020-02-13
> **Frogs Hair said:**
> If your using a conkyrc you can number them conkyrc1,conkyrc2 and so on. Below is a startup applications script sample from OMG Ubuntu though a bit dated. 
```
#!/bin/sh
sleep 5
conky -q -c /home/YOURUSERNAME/.conky/conky1/conkyrc1 &
conky -q -c /home/YOURUSERNAME/.conky/conky2/conkyrc2 & exit

```

This is mine for a single conky. Sleep delays the startup and the number can be changed. 

```
#!/bin/bash
sleep 20 && conky;
```
Thanks. Could you please explain [COLOR=#000000][FONT=&quot]#!/bin/sh[/FONT][/COLOR] 
I guess I am meant to make a script file somewhere but I don't understand #! and how to do this exactly.

---

### Post by ajgreeny on 2020-02-13
The conky command has its own built in pause which does the same as adding sleep time to the command so
***conky -p 10*** has the same result as ***sleep 10 && conky***

I use two instances of conky on my desktop to get what is shown in my screenshot which are both added to my startup applications list.
Incidentally, the left side panel is just that, an additional autohidden xfce4-panel full of launchers.

---

### Post by Frogs Hair on 2020-02-13
There are numerous bash tutorials ,but I have linked one. You don't need a start script, but they are nice for conky startup. You create the script via text editor save it where you want, and make it executable by entering properties with right click. In the permissions tab check the executable box and add it to startup applications. For now you can copy and paste the first example I posted and work with that though I think the simple version ajgreeny would work just fine. 

[https://linuxconfig.org/bash-scripting-tutorial-for-beginners](https://linuxconfig.org/bash-scripting-tutorial-for-beginners)

---

### Post by shmu26 on 2020-02-13
@Frogs Hair thanks a lot, I am wiser now. After reading at least part of the linked article, creating scripts looks less like witchcraft and more like science...

---

