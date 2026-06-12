---
title: "So my cousin is visiting..."
date: 2008-06-06
forum: General Help
---

### Post by lakotajames on 2008-06-06
...and I would love to show off the pure awesomeness that is Ubuntu. :P I have until about 4:00 pm Saturday to make my desktop wonderful looking. I will attach a screen shot of what it looks like now. I am mostly satisfied with it, but the desktop seems kinda empty.  I would like to put something interesting on it.  I have a large terminal launcher now, but it seems useless when I have a launcher on my dock that is much more convenient.  I have tried calenders and clocks that are suggested by the wonderful person who designed the FutureLooks theme, but I don't like them all that much. I also wouldn't mind a different icon theme (using crashbit now). Thanks for any help you may be able to give me. :D

---

### Post by Mentem on 2008-06-06
Probably not an answer you are looking for, but just try to make it look the way you want it to look.

People usually see when the OS is setuped to provide appearance over useability.

---

### Post by liquidfunk on 2008-06-06
I like the look you have. It's simple, attractive and there isn't any clutter. 

 If you want to impress him/her bring out the Wobbly-Windows, Cube, Water effects, and have some interesting animations. 

 Thats what I do ^^

---

### Post by wootah on 2008-06-06
Don't forget the fire ^^

---

### Post by Mentem on 2008-06-06
fire is what I use for minimizing a window, so that's a good hint :)

but there's also alot of effects that no-one uses, even though they look pretty, so avoid those.

---

### Post by lakotajames on 2008-06-07
thanks, liquidfunk. And I am using lots of compiz effects already ;)
But until now, I wasn't using the fire. Don't know why...

---

### Post by easybake on 2008-06-07
A nice looking conky would go well, a cube with a good skydome, an embedded terminal, Wobbly windows, pulling up corners of maximized windows. or simply how to install things just by typing "sudo apt-get install blah blah". Rainlendar is good too.

---

### Post by lakotajames on 2008-06-07
easybake: I would love to use conky, but all three times I tried it , I couldn't make it look good.  I will look into a sky dome. I don't know what an embedded terminal is, but it sounds interesting, I will look into it also.  And I don't care too much for Rainlendar.  Thanks for the suggestions.


EDIT: I now have an embedded terminal, which I love.  Thanks.

---

### Post by easybake on 2008-06-07
> **lakotajames said:**
> easybake: I would love to use conky, but all three times I tried it , I couldn't make it look good.  I will look into a sky dome. I don't know what an embedded terminal is, but it sounds interesting, I will look into it also.  And I don't care too much for Rainlendar.  Thanks for the suggestions.

This should be a start.

This is the conky i made its pretty basic. [http://img338.imageshack.us/my.php?image=screenshotra2.png]("http://img338.imageshack.us/my.php?image=screenshotra2.png")

Here's embedded terminal, I would not make it fullscreen though. [http://ubuntuforums.org/showthread.php?t=802613&highlight=embed+terminal]("http://ubuntuforums.org/showthread.php?t=802613&highlight=embed+terminal")

Here is a good skydome that I found.[http://img175.imageshack.us/my.php?image=skywk9.jpg]("http://img175.imageshack.us/my.php?image=skywk9.jpg")

My conkyrc if you want it.> 
```
use_spacer yes

#background yes

font freesans:size=8
xftfont freesans:size=8
use_xft yes

xftalpha 1

update_interval 5.0

own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

double_buffer yes
draw_shades no
minimum_size 230 5
maximum_width 155

color0 ffffff
color1 cbcbcb
color2 a6a6a6
color3 919191
color4 757575
color5 ffffff

draw_outline no

draw_borders no
draw_graph_borders no

default_color grey90

default_outline_color DarkGrey

#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

gap_x 10
gap_y 35

no_buffers yes

uppercase no

# stuff after 'TEXT' will be formatted on screen

TEXT
${color5}${font freesans:style=Bold:pixelsize=55}$alignc${time %I:%M}${font freesans:size=8}
${cpugraph 20,155 cbcbcb 757575}
${color5}CPU$alignr$cpu%
${color1}${top name 1} $alignr${top cpu 1}
${color2}${top name 2}$alignr${top cpu 2}
${color3}${top name 3}$alignr${top cpu 3}
${color4}${top name 4}$alignr${top cpu 4}

${color5}RAM${color5}$alignr$memperc%
${color3}${membar 7,155}
${color3}${fs_bar 7,155}$color
${color1}${fs_used}${color1} $alignr${fs_free}

${color0}UP${color0}${alignr}DOWN
${color2}${upspeed eth0}k/s$alignr ${color2}${downspeed eth0}k/s
${upspeedgraph eth0 20,75 cbcbcb 757575}$alignr${downspeedgraph eth0 20,75 919191 757575}
${color2}${totalup eth0} $alignr${totaldown eth0}

${color0}${font freesans:size=10}Mundelein, IL$font$alignr${color0}${offset -12}${execi 3600 python conkyforecast.py --location=USIL0823 --datatype=DW --startday=1 -w}
${color2}${font freesans:size=7}${execi 3600 python conkyforecast.py --location=USIL0823 --datatype=CC --startday=0}$font$alignr${color2}${execi 3600 python conkyforecast.py --location=USIL0823 --datatype=HT --startday=1 -i -u}/${execi 3600 python conkyforecast.py --location=USIL0823 --datatype=LT --startday=1 -i -u}
$alignr${color0}${offset -12}${execi 3600 python conkyforecast.py --location=USIL0823 --datatype=DW --startday=2 -w}
$alignr${color2}${execi 3600 python conkyforecast.py --location=USIL0823 --datatype=HT --startday=2 -i -u}/${execi 3600 python conkyforecast.py --location=USIL0823 --datatype=LT --startday=2 -i -u}
$alignr${color0}${offset -12}${execi 3600 python conkyforecast.py --location=USIL0823 --datatype=DW --startday=3 -w}
$alignr${color2}${execi 3600 python conkyforecast.py --location=USIL0823 --datatype=HT --startday=3 -i -u}/${execi 3600 python conkyforecast.py --location=USIL0823 --datatype=LT --startday=3 -i -u}
${voffset -42}${font freesans:style=Bold:size=36}${color1}${execi 3600 python conkyforecast.py --location=USIL0823 --datatype=HT -i -u}${offset -18}${font freesans:size=13}/${color2}${execi 3600 python conkyforecast.py --location=USIL0823 --datatype=LT -i -u}
```

The link to the conky weather script
[http://ubuntuforums.org/showthread.php?t=760527](http://ubuntuforums.org/showthread.php?t=760527)

---

### Post by celticbhoy on 2008-06-07
If you cant get conky to go, why not try using screenlets sysmonitor - same idea and it is only temp to show off.

---

### Post by lakotajames on 2008-06-07
thanks for the skydome.  My cousin's trip was delayed, he should be here around midnight tomorrow.

---

