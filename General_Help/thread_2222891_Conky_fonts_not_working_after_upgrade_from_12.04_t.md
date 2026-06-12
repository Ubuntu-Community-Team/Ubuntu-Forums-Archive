---
title: "Conky fonts not working after upgrade from 12.04 to 14.04"
date: 2014-05-08
forum: General Help
---

### Post by tmulhearn on 2014-05-08
Hello all,

Hope this is the right thread to put this. I had conky installed on 12.04 with no issues, and have upgraded today too 14.04, using the same conky settings. When i start up my PC , conky works fine and all is expected as shown by screen shot 1 , but after awhile i get screen shot 2 . No idea whats causing this.

Any help much appreciated.

[ATTACH=CONFIG]252990[/ATTACH][ATTACH=CONFIG]252991[/ATTACH]

---

### Post by Gillingham on 2014-05-08
I'd say look for a second instance of conky running, because it looks like you have overlapping text.  

David

---

### Post by tmulhearn on 2014-05-08
Any idea where too look,can't tell if conky is doubling up

---

### Post by deadflowr on 2014-05-08
> **tmulhearn said:**
> Any idea where too look,can't tell if conky is doubling up

top (command line)
or
system monitor (graphical application)

see if conky is listed more than once.

---

### Post by tmulhearn on 2014-05-08
Sadly no, already tried top and its listed once

---

### Post by Gillingham on 2014-05-08
I prefer system monitor, may be I'm not using top properly but I am deliberately running more than one instance of conky, and I'm not seeing more than one instance at a time.  I can see that which is changing does vary via the command but...

---

### Post by tmulhearn on 2014-05-09
System monitor also shows the one instance :(

---

### Post by deadflowr on 2014-05-09
Next step is to post the conkyrc...

---

### Post by tmulhearn on 2014-05-09
Here it is

```
# Conky settings #
background no
update_interval 1


cpu_avg_samples 2
net_avg_samples 2


override_utf8_locale yes


double_buffer yes
no_buffers yes


text_buffer_size 2048
#imlib_cache_size 0


temperature_unit fahrenheit


# Window specifications #


own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorate,sticky,skip_taskbar,skip_pager,below


border_inner_margin 0
border_outer_margin 0


minimum_size 200 250
maximum_width 200


alignment tr
gap_x 35
gap_y 55


# Graphics settings #
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no


# Text settings #
use_xft yes
xftfont caviar dreams:size=8
xftalpha 0.5


uppercase no


temperature_unit celsius




default_color Tan1




TEXT
${voffset 8}${color Tan1}${font caviar dreams:size=16}${time %A}${font}${voffset -8}${alignr 50}${color Tan1}${font caviar dreams:size=38}${time %e}${font}
${color FFFFFF}${voffset -30}${color Tan1}${font caviar dreams:size=18}${time %b}${font}${voffset -3} ${color Tan1}${font caviar dreams:size=20}${time %Y}${font}${color DarkSlateGray}${hr 2}


${color DimGray}
${font Arial:bold:size=10}${color Tan1}WEATHER ${color DarkSlateGray} ${hr 2}
$font${color DimGray}London${alignr}${weather [http://weather.noaa.gov/pub/data/observations/metar/stations/](http://weather.noaa.gov/pub/data/observations/metar/stations/) LQBK temperature temperature 30} °C${font}
# $font${color DimGray}Kuala Lumpur${alignr}$font${weather [http://weather.noaa.gov/pub/data/observations/metar/stations/](http://weather.noaa.gov/pub/data/observations/metar/stations/) WMKK temperature temperature 30} °C${font} #




${font Arial:bold:size=10}${color Tan1}SYSTEM ${color DarkSlateGray} ${hr 2}
$font${color DimGray}$sysname $kernel $alignr $machine
Intel® Core&#8482; i7-3537U $alignr${freq_g cpu0}Ghz
OS $alignr${pre_exec cat /etc/issue.net}($machine)
User $alignr${nodename}
Uptime $alignr${uptime}
File System $alignr${fs_type}
Temp $alignr${acpitemp} °C


${font Arial:bold:size=10}${color Tan1}PROCESSORS ${color DarkSlateGray}${hr 2}
$font${color DimGray}cpu1  ${cpu cpu1}% $font${color DarkSlateGray}${cpubar cpu1}
$font${color DimGray}cpu2  ${cpu cpu2}% $font${color DarkSlateGray}${cpubar cpu2}
$font${color DimGray}cpu3  ${cpu cpu3}% $font${color DarkSlateGray}${cpubar cpu3}
$font${color DimGray}cpu4  ${cpu cpu4}% $font${color DarkSlateGray}${cpubar cpu4}
$font${color DimGray}${exec sensors |grep -i temp1} 
${exec sensors |grep -i temp2} 


${font Arial:bold:size=10}${color Tan1}MEMORY ${color DarkSlateGray}${hr 2}
$font${color DimGray}Ram $alignc $mem / $memmax $alignr $memperc%
$font${color DarkSlateGray}$membar
$font${color DimGray}Swap $alignc $swap / $swapmax $alignr $swapperc%
$font${color DarkSlateGray}$swapbar


${font Arial:bold:size=10}${color Tan1}FILE SYSTEM ${color DarkSlateGray}${hr 2}
$font${color DimGray}/ 
${fs_used /} / ${fs_size /} $alignr ${fs_free_perc /}% Free
$font${color DarkSlateGray}${fs_bar /}${goto 60}${if_existing /media/tim/External1TB}
$font${color DimGray}External1TB 
${fs_used /media/tim/External1TB} / ${fs_size /media/tim/External1TB} $alignr ${fs_free_perc /media/tim/External1TB}% Free
$font${color DarkSlateGray}${fs_bar /media/tim/External1TB}${else}
External1TB ${color #FF0000}not mounted${endif}${goto 60}


${font Arial:bold:size=10}${color Tan1}BATTERY (${battery_short BAT0}) ${color DarkSlateGray}${hr 2}
$font${color DimGray}Remaining (${battery_short BAT0})  $alignr${battery_time}
$font${color DarkSlateGray}${battery_bar}


${font Arial:bold:size=10}${color Tan1}TOP PROCESSES ${color DarkSlateGray}${hr 2}
${color DimGray}$font${top_mem name 1}${alignr}(${top_mem pid 1})${top mem 1} %
$font${top_mem name 2}${alignr}(${top_mem pid 2})${top mem 2} %
$font${top_mem name 3}${alignr}(${top_mem pid 3})${top mem 3} %
$font${top_mem name 4}${alignr}(${top_mem pid 4})${top mem 4} %
$font${top_mem name 5}${alignr}(${top_mem pid 5})${top mem 5} %
${processes} (running:${running_processes})


${font Arial:bold:size=10}${color Tan2}NETWORK ${color DarkSlateGray}${hr 2}
$font${color DimGray}Internal ip $alignr ${addr wlan0}
$font${color DimGray}External ip $alignr ${exec wget -q -O - checkip.dyndns.org | sed -e 's/.*Current IP Address: //' -e 's/<.*$//'}
Down $alignr ${downspeed wlan0} kb/s
Up $alignr ${upspeed wlan0} kb/s
Downloaded: $alignr  ${totaldown wlan0}
Uploaded: $alignr  ${totalup wlan0}
```

---

### Post by Roo8choo on 2014-06-30
I was playing with conky as well on my test laptop which is also running on Ubuntu 14.04 and I have the same issue with the font. I think it is compiz related.

---

### Post by tmulhearn on 2014-07-01
Possibly, not too sure and am still facing the issue.

---

### Post by deadflowr on 2014-07-01
Maybe try changing this
```
own_window_type override
```
to this
```
own_window_type normal
```
The thing is, the override option makes it so that those hints, two line below it, are pointless.
From man conky
 > 
own_window_type
              if  own_window  is  yes,  you  may specify type normal, desktop,
              dock, panel or override (default: normal).  Desktop windows  are
              special windows that have no window decorations; are always vis&#8208;
              ible on your desktop; do not appear in your  pager  or  taskbar;
              and  are  sticky  across  all  workspaces. Panel windows reserve
              space along a desktop edge, just like panels and taskbars,  pre&#8208;
              venting  maximized  windows  from  overlapping them. The edge is
              chosen based on the alignment option. [B]Override windows  are  not
              under the control of the window manager. *Hints are ignored*.[/B] This
              type of window can be useful for certain situations.
see if that helps.

---

### Post by tmulhearn on 2014-07-01
Thanks for the tip, changing it now and will let conky run for a bit and post an update tomorrow ;)

---

### Post by tmulhearn on 2014-07-02
> **deadflowr said:**
> Maybe try changing this
```
own_window_type override
```
to this
```
own_window_type normal
```
The thing is, the override option makes it so that those hints, two line below it, are pointless.
From man conky
 
see if that helps.

Conky has been running for a good couple of hours and the font is still showing correctly. Thanks for the tip, its seems to have done the job. Much appreciated :p

---

