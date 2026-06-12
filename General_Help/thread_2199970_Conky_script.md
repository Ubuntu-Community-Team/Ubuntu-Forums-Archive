---
title: "Conky script"
date: 2014-01-16
forum: General Help
---

### Post by vasa1 on 2014-01-16
This is my conky script:```
# UBUNTU-CONKY

# Use Xft?
use_xft yes
xftfont Comic Sans MS:bold:size=14
xftalpha 0.8
text_buffer_size 512

# Update interval in seconds
**update_interval 30.0**
# Text stuff
draw_outline no # amplifies text if yes
draw_borders no
uppercase no # set to yes if you want all text to be in uppercase

# border margins
border_margin 0
 
# border width
border_width 0
 
# Default colors and also border colors, grey90 == #e5e5e5
default_color DimGray

# Text alignment, other possible values are commented
alignment top_left
 
# Gap between borders of screen and text
gap_x 500
gap_y -55

# stuff after 'TEXT' will be formatted on screen

TEXT
**$color**

Temp: ${acpitemp} CPU%: ${cpu cpu0}
```
I have three questions I'd appreciate help with:

I've set **update_interval 30.0** expecting changes in "CPU%" to be seen only every 30s. But changes happen more frequently.

Re. CPU%: I have a dual core (model name	: Intel(R) Core(TM)2 Duo CPU  T6400  @ 2.00GHz) but the **CPU%** value in conky seems to be of just one core when compared to what **top** run with default settings shows. Is there a way to fix **CPU%** to reflect both cpus in one value?

What does **$color** do? The only mention in **man conky** that I found is this indirect one:
>        font (font)
              Specify  a  different font. This new font will apply to the
              current line and everything following. You can use a  $font
              with  no arguments to change back to the default font (much
              like with $color)


---

### Post by tad1073 on 2014-01-17
cpu0 and cpu1

---

### Post by deadflowr on 2014-01-17
Don't know about question one or two but the $color option will signal when a color you've chosen for a specific entry will stop, and the default color will be used again.
Think of it like this, let's say you have a default color of blue, but for one particular line you want to use the color red
you would put something like this
```
${color red} ${conky stuff here}${color}
```
this will make the red line only on that one line and then revert to the default color, or another color if you choose another color.
$font works the same way.

I always brackets these things, though I guess that really isn't needed.

---

### Post by vasa1 on 2014-01-17
@deadflowr, thanks for responding. I'm totally new to conky and want it for the specific task of displaying the temp and CPU% next to my tint2 panel. So I need just the one color.

As you indicated, I could comment out the $color line so that the default_color would then be applied or I could specify a new color.

---

