---
title: "Conky location not right on login?"
date: 2014-05-06
forum: General Help
---

### Post by RallyDarkstrike on 2014-05-06
Hi again folks,

A quick question with Conky - I have it set up on two different machines, my Linux Mint 14 netbook, and my fresh-install Xubuntu 14.04 LTS desktop.

All is fine on my desktop, however, I've noticed something odd on my netbook [COLOR=#ff0000](EDIT - and the Xubuntu desktop, apparently)[/COLOR] with it. When I login, Conky starts just fine after it's delay as I have it set to do with a bash script. However, when it starts after login, it is not in the same place I tell it to be with it's .conkyrc file....

What I mean by this is, when I log in, my Conky display is PRETTY MUCH in the right place, but moved over to the left and down slightly by 20-30 pixels. If I were to then open the .conkyrc file and re-save it WITHOUT MODIFYING IT AT ALL, Conky would re-load as it should, and then be in the right place I had it set to by changing the gap-x and gap-y in the .conkyrc file.

Any ideas why Conky is loading at startup but not to the place I have specified in it's .conkyrc file until I re-load it?

Cheers and thanks!

[COLOR=#ff0000]EDIT - it seems like this phenomenon IS happening on both of my machines...why is Conky moving from where it is set to be...? I first thought maybe it had to do with a resolution change, but both machines stay in the same resolution after login that they were at on the login screen, so that can't be it...thoughts and suggestions?[/COLOR]

---

### Post by deadflowr on 2014-05-06
It's because conky is fighting with everything else that's loading during start up.
It happens a lot, to most users, I find it regardless if the user is on xfce,gnome,unity, or kde.

The simple solution is to delay conky.
Luckily conky has a pause option, where normally you would use the sleep command.
try 
```
conky -p 20
```
This will delay conky from starting for 20 seconds.
You can set it to as long a delay as you want.
If using a separate conkyrc, I've seen the -p option used before and after that
Both
```
conky -c ~/somefile -p 20
```
and 
```
conky -p 20 -c ~/somefile
```

---

### Post by RallyDarkstrike on 2014-05-06
Thanks for the suggestion, however, that is exactly what my bash script is doing....delaying the startup of Conky by something like 30 seconds. I'll try upping the delay and see if that makes any difference I guess...?

[COLOR=#ff0000]EDIT - Ok,changed my Bash script as a test to a LONG delay of 90 seconds just to see what would happen....same issue, Conky does not load in the proper place even though everything else has long since loaded by then.

Going to try using Conky's built-in pause feature and see if that makes any difference instead...[/COLOR]

---

### Post by ajgreeny on 2014-05-06
Can you show us the positioning parts of your .conkyrc just in case there is anything there that gives a clue to what is going on.
As an example mine shows as
```
# Text alignment, other possible values are commented
#alignment top_left
#alignment top_right
#alignment bottom_left
alignment bottom_right
#alignment none

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 25
gap_y 50
```
and it always starts in exactly the same place, as it should from those settings, whether on cold boot, or a logout/login, or if I edit the file and re-save it.
I also use **conky -p 20** in my autostart applications command list in Xubuntu 12.04, though with xfce-4.10 instead of xfce-4.8

---

### Post by RallyDarkstrike on 2014-05-06
My Conky file is a slightly (mostly colors and some text) modified version of the Harmattan theme.

Location section (as far as I can find) is as follows:

```
# Conky settings #
background yes
update_interval 1
double_buffer yes
no_buffers yes
imlib_cache_size 10

# Window specifications #
gap_x 775
gap_y 2
minimum_size 268 620
maximum_width 268
own_window yes
own_window_type normal  # other options are: override/dock/desktop/panel
own_window_transparent yes
own_window_hints undecorate,sticky,skip_taskbar,skip_pager,below
border_inner_margin 0
border_outer_margin 0
#alignment middle_middle
#own_window_argb_visual yes
#own_window_argb_value 0

# Graphics settings #
draw_shades no
default_shade_color AAAAAA
draw_outline no
default_outline_color AAAAAA
draw_borders no
draw_graph_borders no
default_graph_size 26 80
show_graph_scale no
show_graph_range no
```

Probably more than you need there, but hopefully that will help...I can send the whole thing if necessary. Thanks for the help! :) For the record, I use **conky -p 60** on both machines (probably overkill).

---

### Post by ajgreeny on 2014-05-07
The only possible problem that might be related to this is that your only positioning line except for the gap_x and gap_y is commented out so will have no effect.
```
#alignment middle_middle
```
Try removing the # from the start of that line and see if anything  changes, though you may need to edit the two gap lines to more  appropriate figures to get the alignment you want.

Note that in my file there are several alignment lines and the one for the position I want, bottom_right, is uncommented and therefore used by conky; all others are ignored.

---

### Post by RallyDarkstrike on 2014-05-07
Alright - uncommented out the alignment line and changed it's settings to middle_right, as that is where I want my Conky setup to be. Then I re-adjusted the gaps to get it back where I want.

Same issue though. On login, it's still slightly in the wrong place until I open and re-save the .conkyrc file :(

Any other thoughts? :)

---

### Post by ajgreeny on 2014-05-07
No, sorry but I can not figure out why that is happening.

---

