---
title: "Conky Guru: Transparent Clock"
date: 2016-10-23
forum: General Help
---

### Post by XBMC old School on 2016-10-23
I would like to make my clock transparent ~30-40% and not disappear when I use the multi desktop function.

Can any one help?
[ATTACH=CONFIG]271756[/ATTACH]

```
# Conky settings
background yes
update_interval 3
alignment mt
gap_x 750
gap_y 1500

override_utf8_locale yes

double_buffer true,
no_buffers yes
text_buffer_size 2048

# Window specifications
own_window yes
own_window_class Conky
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
own_window_transparent yes
own_window_argb_visual yes
own_window_argb_value 255

border_inner_margin 0
border_outer_margin 0

# Graphics settings
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no

# Text settings
use_xft yes
xftfont Impact:size=40
xftalpha 0.5
text_buffer_size 2048
default_color white     # grey 5f5f5f 3F3F3F

uppercase no

default_color FFFFFF

TEXT
# ${voffset 10}${font Open Sans Light:size=50}${time %A}${font}${voffset -10}
# ${voffset 10}${font Open Sans Light:size=50}${time %B} ${time %e}${font}${voffset -10}
${voffset 10}${font Open Cantarell Bold:size=65}${time %l:%M%P}${font}${voffset -10}
```

---

### Post by CantankRus on 2016-10-23
Set your window to be not transparent then use argb to determine the transparency.
Try this config where I also added these size settings for the window...
```
minimum_size 380 120 
maximum_width 400
```

```
# Conky settings
background no
update_interval 3
alignment tm
gap_x 750
gap_y 1500

override_utf8_locale yes

double_buffer yes
no_buffers yes
text_buffer_size 2048

# Window specifications
own_window yes
own_window_class Conky
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
[COLOR="#FF0000"]own_window_transparent no
own_window_argb_visual yes
own_window_argb_value 80[/COLOR]

[COLOR="#FF0000"]minimum_size 380 120 
maximum_width 400
[/COLOR]
border_inner_margin 0
border_outer_margin 0

# Graphics settings
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no

# Text settings
use_xft yes
xftfont Impact:size=40
xftalpha 0.5
text_buffer_size 2048
default_color white     # grey 5f5f5f 3F3F3F

uppercase no

default_color FFFFFF

TEXT
# ${voffset 10}${font Open Sans Light:size=50}${time %A}${font}${voffset -10}
# ${voffset 10}${font Open Sans Light:size=50}${time %B} ${time %e}${font}${voffset -10}
${voffset 10}${font Open Cantarell Bold:size=65}${time %l:%M%P}${font}${voffset -10}
```
[ATTACH=CONFIG]271759[/ATTACH]

Using a lua script it is also possible to create a semi-transparent background with rounded corners.
If you prefer this I can post details.
[ATTACH=CONFIG]271760[/ATTACH]

---

### Post by XBMC old School on 2016-10-23
Thanks for the quick response Cantankrus!!. I don't want the "Window" to be visible. I want the actual text of the clock to be 30% transparent.[[COLOR=#000000][/COLOR]]("https://ubuntuforums.org/member.php?u=1938181")

---

### Post by CantankRus on 2016-10-23
You would probably need to use the obs compiz plugin and set the entire conky opacity.
```
sudo apt install compiz-plugins compizconfig-settings-manager
```

---

### Post by XBMC old School on 2016-10-23
No dice, even after reboot, gnome compatibility enabled

---

### Post by CantankRus on 2016-10-24
You used to be able use xft to make fonts transparent as shown [**_[COLOR="#B22222"]HERE[/COLOR]_**]("http://conky.pitstop.free.fr/wiki/index.php5?title=Invisible_text_(en)")
but I haven't been able to get this to work in a while.

**[COLOR="#FF0000"]***[/COLOR]****Just noticed your thread is prefixed "[gnome]" so if your not running compiz as the window manager none of this will work**.

After installing compiz-plugins you may have to logout and back in.

Check the  settings in ccsm > obs are as shown...the obs plugin is enabled
and your conky config has the following setting...
```
own_window_class [COLOR="#FF0000"]C[/COLOR]onky
```
***Note the values are case sensitive so both must use a capital [COLOR="#FF0000"]C[/COLOR].

When using unity, once the obs plugin is enabled you can also use the terminal to create opacity matches....
```
dconf write /org/compiz/profiles/unity/plugins/obs/opacity-matches "['class=Conky']"
dconf write /org/compiz/profiles/unity/plugins/obs/opacity-values '[15]'
```
[ATTACH=CONFIG]271772[/ATTACH]


If your using compiz, but not unity run...
```
dconf watch /
```
Then use ccsm to change an opacity value and the terminal will show the path to use.
[ATTACH=CONFIG]271773[/ATTACH]

---

### Post by XBMC old School on 2016-10-25
```
***Note the values are case sensitive so both must use a capital [COLOR=#FF0000]C[/COLOR].

When using unity, once the obs plugin is enabled you can also use the terminal to create opacity matches....
     Code:
     dconf write /org/compiz/profiles/unity/plugins/obs/opacity-matches "['class=Conky']"
dconf write /org/compiz/profiles/unity/plugins/obs/opacity-values '[15]' 
[[IMG]https://ubuntuforums.org/attachment.php?attachmentid=271772&d=1477291483&thumb=1[/IMG]]("https://ubuntuforums.org/attachment.php?attachmentid=271772&d=1477291483")


If your not using conpiz but not unity run...
     Code:
     dconf watch / 
 

```

Everything was set that way already, I'm in gnome. I tinkered a bit but could get it work

I am stumped as to why this is so hard.

---

### Post by CantankRus on 2016-10-25
Everything I've said is for unity which uses compiz as the window manager. (my mistake)
Ubuntu Gnome doesn't use compiz as the window manager so none of the compiz related tweaks will work.

Maybe search for compositing tweaks in gnome-shell?
Not up with gnome-shell but I think the window manager is **mutter**, which by design doesn't
provide for much tweaking.

---

### Post by vasa1 on 2016-10-25
Maybe OP can install Compton to rig up transparency effects?

---

### Post by CantankRus on 2016-10-25
Hi vasa1,
Yeah good idea, I'm just playing around with that in gnome-flashback Metacity session.
I made a compton config 
```
opacity-rule = [ "40:name = 'Conky'" ];
```
and after turning off Metacity compositing it works.

I haven't ran gnome-shell for a while, so I'm going to download and install Ubuntu-gnome
and see how things behave.

---

### Post by CantankRus on 2016-10-25
Hello XBMC old School,
I've been playing around in gnome-shell and can set the opacity of a conky window using devilspie2.

Install devilspie2...
```
sudo apt install devilspie2
```

Make the config directory...
```
mkdir ~/.config/devilspie2
``` 

Create a config file 
```
gedit ~/.config/devilspie2/conky-opacity.lua
```

Copy and paste this into conky-opacity.lua...
```
if (get_application_name() == "**[COLOR="#FF0000"]Conky[/COLOR]**") then
    set_window_opacity(0.3)
end
```
Save and close.


Run **devilspie2** in terminal and then start your conky making sure you have the conky setting...
```
own_window_title **[COLOR="#FF0000"]Conky[/COLOR]**
```

These are the relevant conky settings I used...
```
# Window specifications
own_window yes
own_window_title Conky

own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
own_window_transparent no
own_window_argb_visual yes
own_window_argb_value 0

minimum_size 380 120 
maximum_width 400

```
Add "devilspie2" to startup applications or your startconky script.

---

