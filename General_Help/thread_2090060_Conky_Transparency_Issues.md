---
title: "Conky Transparency Issues"
date: 2012-12-01
forum: General Help
---

### Post by tarun86 on 2012-12-01
Conky has gone all crazy and transparency is not working the way it should be working !!! 


**If I use argb option it makes image(album cover) go all white sort of mosaic. Below is the conky script and screen shot **

> background yes
update_interval 1

alignment top_left
gap_x 40
gap_y 100
minimum_size 300 100
maximum_width 500

draw_shades no 
draw_borders no 

own_window yes
own_window_type normal
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
own_window_transparent yes
own_window_argb_visual yes
own_window_argb_value 100

double_buffer yes
no_buffers yes

override_utf8_locale yes
use_xft yes
xftfont caviar dreams:size=8
xftalpha 0.5
uppercase no

imlib_cache_size 400

default_color FF0000
color1 76EE00	#DDDDDD
color2 7171C6	#AAAAAA
color3 888888
color4 EF5A29
color5 104E8B

#default_shade_color FFFFFF	# Black
TEXT
${if_mpd_playing}
${image /home/mysterio86/.conky/mpd-track-cover -s 100x100 -p 1,1}
${image /home/mysterio86/.conky/frame.png -s 102x102}
${offset 106}${font xftfont caviar dreams:size=8}${color5}${mpd_artist} - ${mpd_title}
${offset 106}${font xftfont caviar dreams:size=10}${color4}${mpd_album} 
${offset 106}${color3}${mpd_bar 3, 200}
${offset 112}${font xftfont caviar dreams:size=8}${color2}${mpd_elapsed}/${mpd_length}
${exec /home/mysterio86/.conky/extract_cover.sh}
${else}
${image /home/mysterio86/.conky/nomusic.jpg -s 100x100 -p 1,1}
${image /home/mysterio86/.conky/frame.png -s 102x102}
${endif}



[IMG]http://i.imgur.com/wC7kf.png[/IMG]


*If I dont use argb option it shows a black box with perfectly okie album cover *

> From the above script remove the argb options for the own_window 

[IMG]http://i.imgur.com/KQcuo.png[/IMG]



_PS: I have tried all sort of options from changing window type to changing argb options. Compositor is on, and system is Xubuntu 12.10. There is no issue with the album cover extraction _

Some help will be really appreciated ! Thanks !

---

### Post by tarun86 on 2012-12-03
Anyone ? Any Ideas ? Any Thoughts ? Doesnt have to be concrete just random thoughts :)

---

### Post by zealibib slaughter on 2012-12-03
own_window_transparent yes
should give you a transparent window however see this webpage for an explanation of how it works.  [http://conky.sourceforge.net/faq.html](http://conky.sourceforge.net/faq.html)
you may need to set your background with feh

own_window_argb_visual yes
own_window_argb_value 100
works only with a composite manager like compiz.

Either way I think it is a problem with how xfce is displaying your desktop background.

---

### Post by figure002 on 2013-06-18
I don't think this has anything to do with XFCE. It also happens in Gnome. This is a known bug in Conky and I've reported the problem back in 2010, see [https://sourceforge.net/p/conky/bugs/317/](https://sourceforge.net/p/conky/bugs/317/)

---

