---
title: "Conky transparency issues"
date: 2012-11-05
forum: General Help
---

### Post by Gotti on 2012-11-05
When I start up conky, everything looks fine and dandy. However, at seemingly random times conky will lose its transparency and have a white background which looks...well...awful. Sometimes it goes back to transparent at another seemingly random time, and sometimes it doesn't.

Here's my conkyrc.

```
# maintain spacing between certain elements
use_spacer no

# set to yes if you want conky to be forked in the background
background no

use_xft yes

# Xft font when Xft is enabled
xftfont Bitstream Vera Sans Mono-7
#xftfont Andale Mono-9
#xftfont Clean-8
#xftfont cubicfive10:pixelsize=8
#xftfont squaredance10:pixelsize=14
#xftfont swf!t_v02:pixelsize=10

# Text alpha when using Xft
xftalpha 1
mail_spool $MAIL

# Update interval in seconds
update_interval 4.0

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_class Conky
own_window_type override
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager  
own_window_transparent yes

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 0 0

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline no # amplifies text

# Draw borders around text
draw_borders no




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
gap_x 20
gap_y 50

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# stuff after 'TEXT' will be formatted on screen

TEXT
${color #ff0000}System Info:
${color #FF3d3d}${execi 5 sysinfo}

${color #ff0000}Network Info:
${color #FF3d3d}${execi 5 netinfo}

${color #ff0000}Hosts Online:
${color #FF3d3d}${execi 5 cat ~/.hostsonline}
```

Thanks for any help!

---

### Post by ajgreeny on 2012-11-05
Assuming this is in Ubuntu with a nautilus drawn desktop try
 **own_window_type normal** 
instead of
 **own_window_type override** 
in the .conkyrc file.

---

