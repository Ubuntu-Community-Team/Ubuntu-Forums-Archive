---
title: "looking for simple digital clock, stand alone, low resource usage"
date: 2013-11-05
forum: General Help
---

### Post by Dreamer Fithp Apprentice on 2013-11-05
I'm experimenting with ultra-light-weight set ups. I've got one system built from the Saucy mini.iso with openbox, lightdm, a greeter, pcmanfm, lxterminal, xscreensaver, and very little else. I use the openbox menu, which contains the Debian menu as a sub-menu and no desktop and no panels at all. I'm planning to build a similar system starting with the Precise mini.iso.

The only thing I miss from lxpanel is the clock. I can install an lxpanel, put only the clock on it, and shrink it to fit. But that seems rather inelegant. It uses about 15 mb of RAM and it is a little more awkward to move about than an ordinary window.

Dclock uses only about 2 mb and it is still overkill for what I want to do. So it should be possible to get a stand alone clock, that will show hh:mm:ss in a font, color, and size of my choosing without using any more than 3 mb at the most. I don't need any other functions. I've considered using a bash script to show time in a small lxterminal window but that uses about the same amount of RAM as an lxpanel. Dclock's display is locked into a cutesy simulation of an led clock and insist on displaying the seconds in a smaller font.  If I can choose a font for legibility, and keep the simple hh:mm:ss format uniform for size I should be able to get a usable (i.e., legible) clock that doesn't take up nearly as much screen real estate.

I anticipate the pragmatic response "Who cares about 15 mb? That's NOTHING!". Well, yes, that is probably true. But, it does all all add up. I do have a truly ancient box I'd like to put a working system on in addition to my main machine.  A window I can easily drag around really would be more functional than a panel.  And finally, using a panel for such a limited purpose on a system built on such minimalistic principles feels like, to put it bluntly, bad art. Inelegant.

Any suggestions?

---

### Post by ajgreeny on 2013-11-05
You could use conky (sudo apt-get install conky-all) then add it to your startup applications and with an appropriate hidden .conkyrc file in your home have just the time showing.

Here's an example .conkyrc file to try out.
```
# set to yes if you want Conky to be forked in the background
background yes

# Use Xft?
use_xft yes

# Xft font when Xft is enabled
xftfont Trebuchet MS:size=11

# Text alpha when using Xft
xftalpha 0.9

# Update interval in seconds
update_interval 2.0

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window yes

# If own_window is yes, you may use type normal, desktop or override
own_window_type normal

# Use pseudo transparency with own_window?
own_window_transparent yes

# If own_window is yes, these window manager hints may be used
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 280

# Maximum width
maximum_width 280

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Draw borders around graphs
draw_graph_borders yes

# Stippled borders?
# stippled_borders 8

# border margins
# border_margin 2

# border width
# border_width 1

# Default colors and also border colors
default_color white
default_shade_color red
default_outline_color green

# Text alignment, other possible values are commented
#alignment top_left
#alignment top_right
alignment bottom_left
#alignment bottom_right
#alignment none

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 30
gap_y 50

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# number of cpu samples to average
# set to 1 to disable averaging
cpu_avg_samples 1

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale no

# variable is given either in format $variable or in ${variable}

# stuff after 'TEXT' will be formatted on screen

TEXT
${font Trebuchet MS:size=50} ${alignc}${time %k:%M}${font Trebuchet MS:size=11}
${font Trebuchet MS:size=30}  ${alignc}${time %a %b %d %Y}${font Trebuchet MS:size=11}
 
```

---

### Post by Habitual on 2013-11-05
and yet another conky digital clock
```
background yes
use_xft yes
xftfont DejaVu Sans:size=8
xftalpha 1
#text_buffer_size 2048
update_interval 1.0
total_run_times 0
own_window yes
own_window_transparent no
own_window_type override
#own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
minimum_size 210 113
maximum_width 210
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no
default_color red
default_shade_color black
default_outline_color white
alignment tr
gap_x 5
gap_y 64
no_buffers yes
uppercase no
cpu_avg_samples 2
override_utf8_locale yes


TEXT
${font Digital Readout Thick Upright:size=24}${color 2E940A}${time %l:%M:%S %p}$font
```

font is [here...]("http://www.fedoraforum.org/forum/attachment.php?attachmentid=20070&d=1284066376")[ATTACH=CONFIG]247600[/ATTACH]

---

### Post by Dreamer Fithp Apprentice on 2013-11-06
AJ; Habitual,
Thanks, guys! That does the trick very nicely.

 Studying  conky has been on my 2do list for a few weeks and I'm glad this pushed  me to it. Looks like the kind of thing I'll find lots of other uses for  as well.

I made the window "normal" and that made it draggable. All I  have left to do to make this perfect is figure out why my  ~/.config/openbox/rc.xml section```

    <application name="Conky (ubuntu)">
     <decor>no</decor>     
    </application>
```isn't effective in undecorating the window.

-------------------------------------------
Added by edit a few hours later:

OK, I need to pay more "attention to details" like Habitual's sig talks about. Both of your example conkyrc files had the answer:```
own_window_hints undecorated
```I still don't know why my openbox rc.xml didn't do it. [see additional comment added below*] There must be something about that file's syntax I don't understand because this is not the first time it didn't do what I expected it to. But anyway, in this case I don't need it. Now my clock IS perfect. Thanks a bunch, guys. I'm a very happy camper now.
----------------
Added laterer:
* Now I know. Well, sorta. Despite the fact that Openbox puts "Conky (ubuntu)" in the title bar (damfino y), it ignores an entry beginning> <application name="Conky (ubuntu)">but for some reason I haven't penetrated prefers> <application name="Conky">
So now I've made it always on top (after all I can drag it anywhere) and it is even perfecter.

---

### Post by Habitual on 2013-11-06
Glad it worked out!

---

