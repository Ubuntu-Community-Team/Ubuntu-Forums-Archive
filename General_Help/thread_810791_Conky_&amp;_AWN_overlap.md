---
title: "Conky &amp; AWN overlap"
date: 2008-05-28
forum: General Help
---

### Post by pAt84 on 2008-05-28
Hi everyone,

I am running AWN and conky. I configured AWN so that maximized windows do not overlap AWN, which works nicely. My problem now is that also my conky doesn't overlap AWN as well. My original idea was to place a conky left and right of the AWN to display some information that I always see, even when windows are maximzed. So how do I make conky use the free space but other windows not? Using the sleep command to start conky later than AWN does not seem to make a big difference. Sooner or later conky will just slide up again.

I attached a screenshot showing the situation.

Thanks a lot.
Pat

---

### Post by SomeGuyDude on 2008-05-28
You're gonna have to re-write the problem. I'm not sure exactly what's going on.

---

### Post by easybake on 2008-05-28
Post your conkyrc

---

### Post by Nem1976 on 2008-05-28
Lol I just reread your post and that is a good questions I will have to see if my conky gets all messed up if I enable that option for nothing to go over awn.

---

### Post by cammin on 2008-05-28
The same thing that's keeping the maximized windows from overlapping AWN is keeping Conky from overlapping it.

I haven't messed with AWN, so I don't know how it's configured. I did a quick look for info but didn't find anything.

---

### Post by pAt84 on 2008-05-29
Nah, sorry for my bad english. I was overworked. :>

Well, as for now it surprisingly works when I just use a shell script starting AWN 7 seconds (sleep 7) after conky and it also looks like it doesnt jump back. 

Nevertheless I was wondering if there is a better method.

```

background no
font Sans:size=7
#xftfont Sans:size=10
use_xft yes
xftalpha 0.9
update_interval 1.0
total_run_times 0
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
minimum_size 225 5
maximum_width 325
draw_shades yes
draw_outline no
draw_borders no
draw_graph_borders yes
default_color white
default_shade_color black
default_outline_color green
alignment bottom_left
gap_x 12
gap_y 5
no_buffers yes
uppercase no
cpu_avg_samples 2
override_utf8_locale no
uppercase no # set to yes if you want all text to be in uppercase

TEXT
Core 1: ${freq_dyn cpu1} Mhz  // ${cpu cpu1}%  ${alignr}${cpubar cpu1 5,90}
Core 2: ${freq_dyn cpu2} Mhz  // ${cpu cpu2}%  ${alignr}${cpubar cpu2 5,90}
RAM:     $mem     // $memperc%  ${alignr}${membar 5,90}
SWP:     $swap     // $swapperc%  ${alignr}${swapbar 5,90}

```

Cheers
Pat

---

### Post by Nem1976 on 2008-05-29
I just tested my setup and I have my conky loading after AWN and it loads up just find.  I use the script to have conky sleep for 10 secs then it loads.  

I tested to make sure awn does stop windows from going full screen and it's working perfectly.  

Honestly I don't see a reason to change what you have if it's working.

---

### Post by pAt84 on 2008-05-29
You let conky sleep for ten seconds and lot it after AWN? How is that supposed to work?

I let AWN load a few seconds after conky, which works often but not always. Sometimes conky gets redrawn above the maximization threshold (the highest AWN icon). 

Pat

---

