---
title: "Conky"
date: 2008-05-05
forum: General Help
---

### Post by Tux.Ice on 2008-05-05
i need some conky help.
i have a few problems

1) need to move the whole conky config down and to the right a bit so it starts at the bottom of my top panel.

2) need to increase the size of my os info text

heres my code
```
#	.conkyrc configuration
#	original by Tristam Green, 11-21-2007
#	Revision 1.123 11-23-2007
#       MeduZa 05/05/2008

# maintain spacing between certain elements
use_spacer right

# set to yes if you want tormo to be forked in the background
#background yes

use_xft yes

# Xft font when Xft is enabled
#xftfont Vera-8
#xftfont Andale Mono-8
#xftfont Clean-8
#xftfont cubicfive10:pixelsize=8
xftfont Sans-Serif:size=9:pixelsize=11
#xftfont swf!t_v02:pixelsize=11

# Text alpha when using Xft
xftalpha 1
#mail_spool $MAIL

# Update interval in seconds
update_interval 1.0

# Create own window instead of using desktop (required in nautilus) normal desktop or override
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

#own_window_hints below

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 150
maximum_width 240

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline no # amplifies text

# Draw borders around text
draw_borders no

# Stippled borders?
stippled_borders 3

# border margins
border_margin 5

# border widt5
border_width 6

# Default colors and also border colors, grey90 == #e5e5e5
default_color grey90
default_shade_color black
default_outline_color DarkGrey

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 24
gap_y 24

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

TEXT

${font OpenLogos:regular:size=18}${color #ffa500}u${font jet:regular:size 18}os info${font}
${color #ffd700}${hr 1}${font}${color}

```

Thnx:popcorn:

---

### Post by K.Mandla on 2008-05-05
Moved to Desktop Effects and Customization.

---

### Post by BLTicklemonster on 2008-05-05
If memory serves me, 

# Gap between borders of screen and text
gap_x 24
gap_y 24

will need to be tinkered with. I had it at bottom right at one time, but that was ages ago, and I don't remember what I did.

Hey, look at these

[http://ubuntuforums.org/showthread.php?t=281865](http://ubuntuforums.org/showthread.php?t=281865)

and I bet you can get an idea where to head with this!

Good luck!!!

(and post back with your solution!!)

---

