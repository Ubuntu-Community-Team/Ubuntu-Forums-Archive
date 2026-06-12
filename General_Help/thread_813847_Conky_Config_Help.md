---
title: "Conky Config Help"
date: 2008-05-31
forum: General Help
---

### Post by cheesypoof on 2008-05-31
Currently my conky config goes as follows.

> double_buffer yes
background no
own_window yes
own_window_transparent yes
own_window_type normal
own_window_hints undecorate,below,sticky,skip_taskbar,skip_pager 
draw_borders no
draw_shades no
gap_x 0
gap_y 0
alignment bottom_middle
update_interval 2.5
default_color 000000
use_xft yes
xftfont bauhaus:pixelsize=11
use_spacer none
minimum_size 0 0
TEXT
${alignc}Uptime: ${color FFFFFF}${uptime_short}${color}   l   Processes: ${color FFFFFF}$processes${color}  Running: ${color FFFFFF}$running_processes${color}   l   CPUs: ${color FFFFFF}${cpu cpu1}% ${cpu cpu2}% ${cpu cpu3}% ${cpu cpu4}%${color}   l   Memory: ${color FFFFFF}$mem/$memmax${color}   l   Home: ${color FFFFFF}${fs_used /home}  / ${fs_size /home}${color}   l   Time: ${color FFFFFF}${time %a %b %d, %I:%M%P}${color}

I want to setup the config so that conky will always be on top. Just fyi, this config positions conky above my bottom panel. Desired Effect: I maximize firefox, but the conky is treated like a panel. As a result it is not maximized over.

---

### Post by john6six on 2008-05-31
Answer to your first question, change "alignment bottom_middle" to "alignment top_left" and change the numbers in "gap_x 0" and "gap_y" to move it down and to the right. You will have to experiment to get it exactly where you want it.

As to the second question, I had the same issue and the resolution was to launch conky from a script which delays the start. The problem appeared to be if conky starts before Compiz, you get the issue you are seeing.

Here's mine:

#!/bin/bash
sleep 30 &&
exec conky &
exit 

Hope this helps.

---

### Post by cheesypoof on 2008-05-31
I think you misunderstood what my intention was. This isn't your fault, I just failed to communicate effectively. Thanks for trying to help though.

Startup:
[[IMG]http://img225.imageshack.us/img225/5595/screenshotla1.th.jpg[/IMG]](http://img225.imageshack.us/my.php?image=screenshotla1.jpg)

Current State:
[[IMG]http://img61.imageshack.us/img61/5504/screenshot1hz5.th.jpg[/IMG]](http://img61.imageshack.us/my.php?image=screenshot1hz5.jpg)

Desired Effect:
[[IMG]http://img225.imageshack.us/img225/2130/screenshot2rz2.th.jpg[/IMG]](http://img225.imageshack.us/my.php?image=screenshot2rz2.jpg)

I want to have the conky stop windows from overlapping it, like how my bottom panel does. I want to be able to maximize firefox and have it not overlap that horizontal strip. I just don't know which commands I need to change to make it do that. Hopefully you understand what I mean.

---

### Post by kerry_s on 2008-05-31
try removing "below" from your conky script:

own_window_hints undecorate,below,sticky,skip_taskbar,skip_pager 
to
own_window_hints undecorate,sticky,skip_taskbar,skip_pager

hmmm, didn't work for me. can't get it to occupy it's own space to resist other windows.

---

### Post by john6six on 2008-05-31
I am sorry, guess I was reading your question wrong.

Hopefully Kerry's fix takes care of your issue.

John

---

### Post by dlm4849 on 2008-09-04
did you ever get this to work? Im looking for the same effect.

---

### Post by cheesypoof on 2008-09-13
Unfortunately I was unable to get it to occupy its own space.

---

### Post by ZeroTruths on 2009-04-15
I know of two ways to get this effect done. The first is trying to make Conky behave like a dock, but as far as I know, this is not yet possible in Conky.
The second, which is what I do/use is use a completely different window manager. Currently, Ubuntu's WM is Metacity, but the one that I use, Openbox, has support for margins. When margins are specified, Maximized windows are not allowed to extend past the margins specified. Simply put Conky under one of these margins, and you'd be golden. :)

---

