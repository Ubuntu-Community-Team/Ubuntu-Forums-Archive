---
title: "Conky problem"
date: 2015-09-04
forum: General Help
---

### Post by spinjitsu on 2015-09-04
I am new to Conky, but am having an issue that I can't find a solution to anywhere else. Not sure if this is the right forum for this, but hopefully someone can help out or point me in the right direction.

I took one of the examples from the screenshot page, which you would expect to work without much modification, from here: [http://conky.sourceforge.net/conkyrc-drphibes](http://conky.sourceforge.net/conkyrc-drphibes)

I ripped out stuff that was causing problems, some lines that I did not have (like share1) and changed hdd to sdd. After way too much time troubleshooting, I have settled on the config here:
```

total_run_times 0
alignment tl
background yes
border_width 1
cpu_avg_samples 2
default_color cornflowerblue
default_outline_color white
default_shade_color white
double_buffer yes
draw_borders no
draw_graph_borders yes
draw_outline no
draw_shades no
gap_x 2225
gap_y 30 
maximum_width 330
max_port_monitor_connections 64
max_specials 512
max_user_text 16384
minimum_size 330 10
net_avg_samples 2
no_buffers no
out_to_console no
own_window_colour black
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
own_window_transparent no
own_window_type normal
own_window yes
stippled_borders 2
update_interval 2
uppercase no
use_spacer yes
use_xft yes
xftalpha 0.8
xftfont  Bitstream Vera Sans Mono:size=9


TEXT
${color #0077ff}Uptime:$color $uptime ${color #0077ff} Load:$color $loadavg
${color #0077ff}CPU:$color ${cpu}% ${color #0077ff}${cpubar 5,85}   ${color #0077ff}Disk I/O: $color${diskio}
${color #0077ff}${cpugraph 0 32,155 104E8B 0077ff} $alignr${color #0077ff}${diskiograph 32,155 104E8B 0077ff 750}
${color #0077ff}RAM Usage:$color $mem${color #0077ff}/${color}$memmax - $memperc% ${color #0077ff}$membar
${color #0077ff}Swap Usage:$color $swap${color #0077ff}/${color}$swapmax - $swapperc% ${color #0077ff}${swapbar}
${color #0077ff}Procs:$color $processes ${color #0077ff}Run:$color $running_processes ${color #0077ff}#CPU:$color ${i2c 0-002d temp 2}${color #0077ff} MB:$color ${i2c 0-002d temp 1} ${color #0077ff}HD:$color ${hddtemp /dev/sdd}
${color #0077ff}Entropy: ${color}${entropy_avail}${color #0077ff}/${color}${entropy_poolsize} ${color #0077ff}${entropy_bar}
${color #0077ff}Net Down:$color ${downspeed eth0} k/s      ${color #0077ff}Net Up:$color ${upspeed eth0} k/s
${color #0077ff}${downspeedgraph eth0 32,155 104E8B 0077ff} $alignr${color #0077ff}${upspeedgraph eth0 32,155 104E8B 0077ff}
${color #0077ff}File systems:
 ${color #0077ff}/          $color${fs_used /}/${fs_size /}${alignr}${color #0077ff}${fs_bar 5,120 /}
 ${color #0077ff}/home      $color${fs_used /home}/${fs_size /home}${alignr}${color #0077ff}${fs_bar 5,120 /home}
 ${color #0077ff}/opt       $color${fs_used /opt}/${fs_size /opt}${alignr}${color #0077ff}${fs_bar 5,120 /opt}
 ${color #0077ff}/usr/local $color${fs_used /usr/local}/${fs_size /usr/local}${alignr}${color #0077ff}${fs_bar 5,120 /usr/local}
 ${color #0077ff}/var       $color${fs_used /var}/${fs_size /var}${alignr}${color #0077ff}${fs_bar 5,120 /var}
#${color #0077ff}/share1    $color${fs_used /share1}/${fs_size /share1}${alignr}${color #0077ff}${fs_bar 5,120 /share1}


${color #0077ff}Top Processes:
${color #0077ff}Name              PID     CPU%   MEM%
$color ${top name 1} ${top pid 1} ${top cpu 1} ${top mem 1}
$color ${top name 2} ${top pid 2} ${top cpu 2} ${top mem 2}
$color ${top name 3} ${top pid 3} ${top cpu 3} ${top mem 3}
${color #0077ff}Mem usage
$color ${top_mem name 1} ${top_mem pid 1} ${top_mem cpu 1} ${top_mem mem 1}
$color ${top_mem name 2} ${top_mem pid 2} ${top_mem cpu 2} ${top_mem mem 2}
$color ${top_mem name 3} ${top_mem pid 3} ${top_mem cpu 3} ${top_mem mem 3}
 
${color #0077ff}Port(s)${alignr}#Connections
$color Inbound: ${tcp_portmon 1 32767 count}  Outbound: ${tcp_portmon 32768 61000 count}${alignr}ALL: ${tcp_portmon 1 65535 count}
${color #0077ff}Inbound Connection ${alignr} Local Service/Port$color
 ${tcp_portmon 1 32767 rhost 0} ${alignr} ${tcp_portmon 1 32767 lservice 0}
 ${tcp_portmon 1 32767 rhost 1} ${alignr} ${tcp_portmon 1 32767 lservice 1}
 ${tcp_portmon 1 32767 rhost 2} ${alignr} ${tcp_portmon 1 32767 lservice 2}
 ${tcp_portmon 1 32767 rhost 3} ${alignr} ${tcp_portmon 1 32767 lservice 3}
 ${tcp_portmon 1 32767 rhost 4} ${alignr} ${tcp_portmon 1 32767 lservice 4}
${color #0077ff}Outbound Connection ${alignr} Remote Service/Port$color
 ${tcp_portmon 32768 61000 rhost 0} ${alignr} ${tcp_portmon 32768 61000 rservice 0}
 ${tcp_portmon 32768 61000 rhost 1} ${alignr} ${tcp_portmon 32768 61000 rservice 1}
 ${tcp_portmon 32768 61000 rhost 2} ${alignr} ${tcp_portmon 32768 61000 rservice 2}
 ${tcp_portmon 32768 61000 rhost 3} ${alignr} ${tcp_portmon 32768 61000 rservice 3}
 ${tcp_portmon 32768 61000 rhost 4} ${alignr} ${tcp_portmon 32768 61000 rservice 4}


```

This still isn't fully customized, but there's an issue I need help solving before I can do anything else with it. Currently, it shows up in a black box. If I change own_window_transparent to yes, it will become transparent, but the text will overwrite itself. There's no clear between the refresh, so the text just piles on top of itself and the whole thing becomes unreadable. Is there anyone out there that can spot anything wrong with this?

---

### Post by Habitual on 2015-09-04
I downloaded your code and ran it.
```
conky -c xrc
Conky: use_spacer should have an argument of left, right, or none.  'yes' seems to be some form of 'true', so defaulting to right.
```
I set it to use_spacer none and it ran without complaining.

Works great here on my Mint 17.1 (Ubu 14.04.1-based) Xfce4 desktop.
[ATTACH=CONFIG]264227[/ATTACH]

Can you show me a screenshot of the problem?

---

### Post by spinjitsu on 2015-09-04
Yeah, I think this script was written for an older version because that value was from one of their own examples on the sourceforge page. I tried changing it to each of the values but none of them really did anything that I could see. I forgot I left it at yes, but aside from complaining it doesn't affect the display. I get the same result as what you posted right now, but my problem is I want it to be transparent. However, when I set own_window_transparent to yes, I get what you see in the attached pic with the black background (sprayed out an ip at the top of outbound). To actually make it transparent I also have to set double buffer to no (attached). Both result in text and graphs being written on top of themselves with each refresh.

---

### Post by QDR06VV9 on 2015-09-04
I seem to get better results with
```
[COLOR=#000000][FONT=Ubuntu Mono]own_window_type override[/FONT][/COLOR]
```
For me it also make transparent look nicer.
Are you using composting?(ieCompiz)
Regards

---

### Post by spinjitsu on 2015-09-04
No compiz. I tried override also but that fails with the following:
```

Conky: desktop window (140001a) is subwindow of root window (1ec)
Conky: window type - override
Conky: drawing to created window (0x2400001)
Conky: drawing to single buffer
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  1 (X_CreateWindow)
  Serial number of failed request:  126
  Current serial number in output stream:  130

```

---

### Post by QDR06VV9 on 2015-09-04
Should be <[COLOR=#000000][FONT=Ubuntu Mono]own_window_type override>[/FONT]

[FONT=Ubuntu Mono]Edit:Without composting (Compiz) 
[/FONT][/COLOR]Try these settings


```
[FONT=Verdana]own_window_type normal
[/FONT][FONT=Verdana]own_window_transparent no[/FONT]
[FONT=Verdana]own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager[/FONT]
[FONT=Verdana]own_window_argb_visual yes[/FONT]
[FONT=Verdana]own_window_argb_value 0[/FONT]
```

When using own_window_argb_visual yes with own_window_transparent no
you can determine the transparency of the window with the own_window_argb_value setting.
ie
own_window_argb_value 0 ........... fully transparent
own_window_argb_value 255 ........ fully opaque
Hope that makes sense

---

### Post by spinjitsu on 2015-09-04
That's what it is set to right now, and what causes the error in the post above:
```

$ grep override .conkyrc
own_window_type override

```

---

### Post by QDR06VV9 on 2015-09-04
See my post above

---

### Post by spinjitsu on 2015-09-04
@[COLOR=#000000]runrickus that did the trick, thanks! I guess I should dig through more conky documentation before customizing further. [/COLOR]

---

### Post by QDR06VV9 on 2015-09-04
Nice!!
Old stinkeye show me that a couple of years ago.
Conky can be very addicting.
Cheers

---

