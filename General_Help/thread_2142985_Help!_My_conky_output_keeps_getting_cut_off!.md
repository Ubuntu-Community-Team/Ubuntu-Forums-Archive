---
title: "Help! My conky output keeps getting cut off!"
date: 2013-05-07
forum: General Help
---

### Post by Nick8 on 2013-05-07
Hello,

I have a very simple conky configuration: a long thin strip part-way accross the top of the screen. But it keeps getting cut off at the end (see attached image).

This only seems to happen when conky is displaying high CPU and RAM usage. Otherwise it's fine.

I've tried increasing 'text_buffer_size' and 'maximum_width', but these don't help.

Could it be a problem with the spacers? Is it possible to increase the spacer size?

Here is my .conkyrc file:

```

alignment top_left
background no
border_width 1
cpu_avg_samples 2
default_color white
draw_borders no
draw_outline no
draw_shades no
use_xft yes
xftfont DejaVu Sans Mono:size=10
gap_x 0
gap_y 0
minimum_size 5 5
maximum_width 1000
net_avg_samples 2
no_buffers yes
out_to_console no
out_to_stderr no
own_window yes
own_window_class Conky
own_window_type dock
double_buffer yes
update_interval 1
uppercase no
use_spacer right

TEXT
&#8595; ${downspeed eth1}  &#8593; ${upspeed eth1}    &#931;&#8595; ${totaldown eth1}  &#931;&#8593; ${totalup eth1}    RAM $memperc%    CPU $cpu%    HDD $diskio

```

Thanks for your help in advance.

Nick

---

### Post by stinkeye on 2013-05-08
As the length of each output increases it pushes those to the right, across.
Think of spaces as an invisible character, not an empty area.
Instead of using spaces to position your output, use goto xx which will fix each outputs start position.

eg 
```
&#8595; ${downspeed eth1}**${goto 100}**&#8593; ${upspeed eth1}**${goto 200}**&#931;&#8595; ${totaldown eth1}...........
```

Then fix the width of the conky window using...
```
minimum_size [COLOR="#FF0000"]670[/COLOR] 5 
maximum_width [COLOR="#FF0000"]670[/COLOR]
```
[COLOR="#FF0000"]Alter to suit your conky[/COLOR]

From man conky
> **minimum_size width (height)** 
 Minimum size of window

**maximum_width pixels** 
 Maximum width of window 

**goto x **
 The next element will be printed at position 'x'.

---

### Post by Nick8 on 2013-05-08
Thanks, I'll try this.

---

### Post by Nick8 on 2013-05-08
Great! It works.

I have a question though: After I added all the '{goto xxx}'s, I ran conky still with the minimum_size as 5 5 and the maximum width as 1280 (my screen width) and about half of it was chopped off (see screenshot). Do you know why this is?

I suppose what I'm really asking is why do I need to increase the minimum_size width. Isn't it defined by the width of what is under TEXT in .conkyrc?

Anyway, thanks for your help with this.

---

### Post by stinkeye on 2013-05-08
It should work as you expect, but if the size of the window has changed after editing your conkyrc, you need to run...
```
killall conky
```
and restart conky.

---

