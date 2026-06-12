---
title: "small conky issue"
date: 2008-04-11
forum: General Help
---

### Post by olafthekid on 2008-04-11
Hi!

I just added conky to my desktop.
I found a nice configuration at gnome look but I have one small "problem".
If you take a look at this screenshot of my desktop:
[IMG]http://image.bayimg.com/majndaabf.jpg[/IMG]

you se there's a square character at the end. So I need some help to remove this.

here's the .conkyrc:
```
#avoid flicker
double_buffer yes

#own window to run simultanious 2 or more conkys
own_window  yes
own_window_transparent no
own_window_type normal
own_window_hints undecorate,sticky,skip_taskbar,skip_pager 

#borders
draw_borders no
border_margin 1

#shades
draw_shades no

#position
gap_x 0
gap_y 3
alignment top_left

#behaviour
update_interval 1

#colour
default_color  8f8f8f
#default_shade_color 000000
own_window_colour 262626

#font
use_xft yes
xftfont bauhaus:pixelsize=10

#to prevent window from moving
use_spacer no
minimum_size 1268 0

TEXT
${voffset -1} ${offset 200} CPU: ${color e0e0e0}${font}${cpu}% ${color} MEM: ${color e0e0e0}${font}${mem} ${color} | ${color} Up: ${color 
e0e0e0}${font}${uptime_short}${color}  | ${color} Net: ${color e0e0e0}${font}${downspeed eth0} Kb/s ${color} ${totaldown eth0} downloaded${color} | ${color} ${color e0e0e0}${upspeed eth0} Kb/s ${color} ${totalup eth0} uploaded${color}  |  ${color}DSK: ${color e0e0e0}${font}${fs_free /}

```

thanks!

---

### Post by kerry_s on 2008-04-11
did you add a finishing line, 1 blank line at the bottom of the text.

---

### Post by olafthekid on 2008-04-11
i've tried that but it just adds another line with a square char.

---

### Post by kerry_s on 2008-04-11
okay go to the end of the conky line and backspace,retype the the last character an hit enter to return ending that line.

if that don't work copy it as conky.txt and attache it and i'll see if i can fix it on my desktop.

---

### Post by olafthekid on 2008-04-11
nope didn't work.
here's the config file.

thanks.

---

### Post by kerry_s on 2008-04-11
alright try it.

---

### Post by olafthekid on 2008-04-11
hmm now there's no squares but there is a double line instead of one. and if i remove the extra return the square is back. could it be the editor i use to edit the config file? i use nano.

---

### Post by kerry_s on 2008-04-11
no, i don't think so. nano should be fine, i used mcedit from mc. you need the 1 blank line at the end of the file, else it's incomplete.

can you put another screen shot, just a regular attachment not like your first huge 1. :)

like this->

---

### Post by kerry_s on 2008-04-11
try this 1.

---

### Post by olafthekid on 2008-04-11
thanks! that did the trick.
how did you add the blank line at the end?

---

### Post by kerry_s on 2008-04-11
> **olafthekid said:**
> thanks! that did the trick.
how did you add the blank line at the end?

that's good news, there was actually 2 extra lines, i'm guessing from your first 2 attempts to fix it or i added a extra. don't matter as long as it works for ya. :)

---

