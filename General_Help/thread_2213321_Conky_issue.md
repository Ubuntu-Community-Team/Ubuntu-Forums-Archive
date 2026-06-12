---
title: "Conky issue"
date: 2014-03-26
forum: General Help
---

### Post by a8j8i8t8 on 2014-03-26
I'm on Ubuntu 13.10 64 bit with following output of "dpkg -l | grep conky"
  ```

  conky-all                                      1.9.0-3                                 amd64        highly configurable system monitor (all features enabled)
  conky-manager                             1.2.0.1                                 amd64        Simple tool for managing conky scripts
```

Following is the configuration in .conkyrc
```

background no
update_interval 1
double_buffer yes

own_window yes
own_window_class conky
own_window_type override
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
own_window_title
own_window_transparent yes

minimum_size 250

alignment tr
gap_x 50
gap_y 100

border_inner_margin 15
border_outer_margin 0

draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no

use_xft yes
xftalpha 0
xftfont Open Sans Light:size=10

override_utf8_locale yes

imlib_cache_size 0
```

Whenever I do "Show Desktop" + "right-click" on desktop, transparency vanishes.
My conky windows fills with gray background.
Below are "Before" and "After" images.
[ATTACH=CONFIG]251477[/ATTACH][ATTACH=CONFIG]251476[/ATTACH]

Thanks in advance.

---

### Post by deadflowr on 2014-03-26
Well it's hard to see the difference, as both pictures show the same thing. Maybe it's the forums software or something.
But anyway, the setting
```
own_window_type override
```
when set overrides the setting set in the very next line
```
own_window_hints <other stuff listed here>
```
so maybe try changing the type to normal
```
own_window_type normal
```
see if that does anything.

---

### Post by a8j8i8t8 on 2014-03-26
Thanks for reply.
Actually difference between two images is, first one is transparent while next one isn't, next one is with gray background.
I tried "normal" instead of "override". But with "normal", I get borders which I don't want.

---

### Post by ajgreeny on 2014-03-26
Try **own_window_type desktop** as the other available option
None of those options seem to make any difference to the appearance of my conky display, however, so it may be some other part of the config.
I do not have conky-manager installed so I don't know if it could make any difference between out two situations.

---

### Post by wgarcia on 2014-03-26
The thing of the frame around the conky window can be solved by:


 1.   Start the CompizConfig Settings Manager
 2.   Select Effects > Window Decoration
 3.   Go into Shadow windows box and after the value any add & !(class=Conky) to apply this rule to all windows except Conky

In general for your issues take a look at:

[http://askubuntu.com/questions/259290/strange-conky-background-behavior](http://askubuntu.com/questions/259290/strange-conky-background-behavior)

---

### Post by grumblebum2 on 2014-03-26
...and if you want **wgarcia's** fix to work delete the line in your config...
```
own_window_class conky
```

own_window_class defaults to **[COLOR="#FF0000"]C[/COLOR]onky** with a capital "C" and the compiz fix wont work when you set **own_window_class [COLOR="#FF0000"]c[/COLOR]onky** without the capital.

---

### Post by a8j8i8t8 on 2014-03-26
[FONT=system]grumblebum2  and wgarcia, many many thanks for the solution.
It worked like a gem :-)[/FONT]

---

