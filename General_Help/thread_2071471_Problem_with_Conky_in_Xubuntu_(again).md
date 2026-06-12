---
title: "Problem with Conky in Xubuntu (again)"
date: 2012-10-15
forum: General Help
---

### Post by M_Mynaardt on 2012-10-15
Hi!

I had a problem previously with the Conky panel in Xubuntu.  It would disappear every time I clicked the mouse on the Conky display.  I was told the following would work (per Habitual):
```
own_window yes
own_window_type desktop
#use "desktop" instead of the default of "normal"
```

And this worked.  But now it doesn't.  :p

Setting **own_window_desktop** to either dock or override didn't have my Conky display work at all.  And if I set it to normal, desktop, or panel, the Conky display looked okay for each, but would disappear again if I clicked the Conky display.  I tried this with both a single wallpaper or list of wallpapers from the desktop setting in case that made a difference, but it did not.

The only real change I made since I first had this problem and was given a solution that worked at the time was upgrade Xfce from 4.8 to 4.10.  Would that have a bearing on it?

It's not critical, but it is a bit annoying at times.

Here's my Conky settings from my **.conkyrc** file, if anyone has some suggestions of where I might be going amiss:

```
##############################################
#  Settings
##############################################
#
# ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
# performance settings
# ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
#
use_xft yes
xftalpha 1
update_interval 1.0
total_run_times 0
cpu_avg_samples 2
no_buffers yes
override_utf8_locale no
#
# ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
# window position
# ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
#
alignment top_right
gap_x 40
gap_y 70
# 40 pixels from the right and 70 from the bottom
minimum_size 355 200
# minimum_size (width),(height)
#
# ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
# other window settings
# ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
#
own_window yes
double_buffer yes
# double buffer to prevent flicker with own_window
own_window_argb_visual yes
# this needs to be set to "yes" in Xubuntu
own_window_type desktop
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
draw_borders no
border_width 8
border_inner_margin 10
# border settings, if needed
background no
own_window_colour 233d5d
# background window colour
#

```

Thanks in advance, if anyone has any ideas...

---

### Post by GreatDanton on 2012-10-15
I am using VinDsl conky and I have:```
## Create own window in instead of using desktop?
#
own_window yes
own_window_transparent yes
own_window_type normal
own_window_class conky-semi
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
####
## Some distros also require the following 2 lines.
#
own_window_argb_visual yes
own_window_argb_value 255
```Try above options and you will see =).
Hope this helps.

Regards.

---

### Post by M_Mynaardt on 2012-10-15
> **GreatDanton said:**
> I am using VinDsl conky and I have:```
## Create own window in instead of using desktop?
#
own_window yes
own_window_transparent yes
own_window_type normal
own_window_class conky-semi
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
####
## Some distros also require the following 2 lines.
#
own_window_argb_visual yes
own_window_argb_value 255
```Try above options and you will see =).
Hope this helps.

Regards.

Hi there!  Your information did the trick!  =D>

All I needed was to add
```
own_window_class conky-semi
```

Now the Conky display stays put when I click on it.

Thanks again for that!

---

