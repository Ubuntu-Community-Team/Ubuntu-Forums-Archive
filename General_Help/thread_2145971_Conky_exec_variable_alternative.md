---
title: "Conky: exec variable alternative"
date: 2013-05-17
forum: General Help
---

### Post by syfluqs on 2013-05-17
So, the exec variable is a necessary evil for me. I mean it is a complete cpu hog.
I created a script to monitor some behind the scenes activity of my pc and then incorporated in conky via the exec variable. Each instance of exec uses about 3 % of CPU on my linux pc. Is there any alternative to exec variable that uses less resources??

my conkyrc:

```


# UBUNTU-CONKY
# A comprehensive conky script, configured for use on
# Ubuntu / Debian Gnome, without the need for any external scripts.
#
# Based on conky-jc and the default .conkyrc.
# INCLUDES:
# - tail of /var/log/messages 
# - netstat connections to your computer
#
# -- Pengo (conky@pengo.us)
#


# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_hints undecorated,below,skip_taskbar,skip_pager
background no


# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes


# fiddle with window
use_spacer right
use_xft yes


# Update interval in seconds
update_interval 1.0


# Minimum size of text area
minimum_size 400 5


# Draw shades?
draw_shades yes


# Text stuff
draw_outline no # amplifies text if yes
draw_borders no
draw_graph_borders no


uppercase no # set to yes if you want all text to be in uppercase


# Stippled borders?
stippled_borders 8


# border width
border_width 1


# Default colors and also border colors, grey90 == #e5e5e5
default_color white
default_shade_color black
default_outline_color white


own_window_colour brown
own_window_transparent yes


# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right


# Gap between borders of screen and text
gap_x 10
gap_y 10


# stuff after 'TEXT' will be formatted on screen


override_utf8_locale no
xftfont Terminus:size=8
xftalpha 0.8


TEXT


${offset 240}${color slate grey}${time %a, } ${color }${time %e %B %G}
${offset 240}${color slate grey}${time %Z,    }${color }${time %H:%M:%S}
${offset 240}${color slate grey}UpTime: ${color }$uptime
${offset 240}${color slate grey}CPU:${color } $cpu%
${offset 240}${cpugraph 20,130 000000 ffffff}
${offset 240}${color slate grey}Processes: ${color }$processes  
${offset 240}${color slate grey}Running:   ${color }$running_processes


${offset 240}${color slate grey}Highest CPU:
${offset 240}${color #ddaa00} ${top name 1}${top_mem cpu 1}
${offset 240}${color lightgrey} ${top name 2}${top cpu 2}
${offset 240}${color lightgrey} ${top name 3}${top cpu 3}
${offset 240}${color lightgrey} ${top name 4}${top cpu 4}


${offset 240}${color slate grey}MEM:  ${color } $memperc% $mem/$memmax
${offset 240}${membar 3,100}


${offset 240}${color slate grey}ROOT:    ${color }${fs_free /}/${fs_size /}
${offset 240}${fs_bar 3,100 /}




${offset 240}${color slate grey}NET: ${exec o neus}
${offset 240}${color}Up: ${color }${upspeed eth0} k/s
${offset 240}${upspeedgraph eth0 20,130 000000 ffffff}
${offset 240}${color}Down: ${color }${downspeed eth0}k/s${color}
${offset 240}${downspeedgraph eth0 20,130 000000 ffffff}


${offset 240}${color slate grey}Now Playing: 
${offset 240}${color}${exec deadbeef --nowplaying "%t" | cut -c1-25}
${offset 240}${color}by ${exec deadbeef --nowplaying "%a" | cut -c1-20}


```

PS-
the ${exec o neus} part displays the log.

---

### Post by anoldone on 2013-05-17
Optimise neus or add interval to it's execution.

update_interval/texeci/execi
[http://conky.sourceforge.net/variables.html](http://conky.sourceforge.net/variables.html)

---

### Post by syfluqs on 2013-05-17
@anoldone thanks for the reply...

It seems texeci or execi are no different from exec in my case.
You sure there's no other method?

From the conky manpage:

> 
exec command
              Executes a shell command and displays the output in conky. warn&#8208;
              ing:  this  takes a lot more resources than other variables. I'd
              recommend coding wanted behaviour in C and posting a patch.


What does the "coding wanted behaviour in C" means?

---

### Post by stylintile on 2013-05-17
Hello,
     Your command;
```
${exec o neus}
```
executes the script every time your conky updates, which in your config is every second.  If you replace the;
```
${exec}
```
with;
```
${execi 10}
```
the script will run every tenth conky update.  You can change the 10 to whatever interval works for you.  You could also change the update interval for the entire conky to something less frequent.
Hope this helps.

---

