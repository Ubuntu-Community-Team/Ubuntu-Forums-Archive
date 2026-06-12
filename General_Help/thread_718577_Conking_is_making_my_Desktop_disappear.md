---
title: "Conking is making my Desktop disappear"
date: 2008-03-08
forum: General Help
---

### Post by agentnixon on 2008-03-08
whenever Conky refreshes itself, stuff on my desktop disappear. I'm talking about icons of drives, files and folders. If I click and drag to highlight them, they appear again, but then disappear once conky refreshes itself. Here is my conky config:
```
background no
cpu_avg_samples 5
net_avg_samples 5
out_to_console no
font 7x13
own_window_transparent no
own_window_colour hotpink
xftalpha 1.0
update_interval 2
own_window no
double_buffer yes
minimum_size 5 5
draw_shades yes
draw_outline no
draw_borders no
stippled_borders 0
border_margin 10
border_width 1
default_color white
default_shade_color black
default_outline_color white
alignment top_right
gap_x 20
gap_y 20
use_spacer yes
no_buffers yes
uppercase no
mpd_host 192.168.1.15
mpd_port 6600
# stuff after 'TEXT' will be formatted on screen
TEXT

${color #ffffff}SYSTEM
${color white}${hr 1}
  ${color #ffffff}Kernel: ${color #ffffff}$kernel ${color #ffffff}${alignr}Uptime: ${color #ffffff}$uptime
  ${color #ffffff}CPU   : ${color #ffffff}$freq MHz   $cpu%  ${alignr}${acpitemp} C
  ${color #ffffff}        ${cpugraph 15,210 ff0000 ff00ff}
  ${color #ffffff}RAM   : ${color #ffffff}$memmax     $memperc%  ${membar 6}
  ${color #ffffff}Swap  : ${color #ffffff}$swapmax     $swapperc%  ${swapbar 6}

${color #ffffff}POWER
${color white}${hr 1}
  ${color #ffffff}AC Adapter: ${color #ffffff}$acpiacadapter
  ${color #ffffff}Battery   : ${color #ffffff}$battery $battery_time

${color #ffffff}DISK
${color white}${hr 1}
  ${color #ffffff}/     : ${color #ffffff}${fs_size /}    ${fs_used_perc /} % ${alignr}${fs_bar 6,100 /}
  ${color #ffffff}/home : ${color #ffffff}${fs_size /home}    ${fs_used_perc /home} % ${alignr}${fs_bar 6,100 /home}

${color #ffffff}PROCESSES
${color white}${hr 1}
  ${color #ffffff}Processes: ${color #ffffff}$processes  ${color #ffffff}Running: ${color #ffffff}$running_processes

  ${color #ffffff}Name             PID     CPU%   MEM%
  ${color #ffffff}${top name 1} ${top pid 1} ${top cpu 1} ${top mem 1}
  ${color #ffffff}${top name 2} ${top pid 2} ${top cpu 2} ${top mem 2}
  ${color #ffffff}${top name 3} ${top pid 3} ${top cpu 3} ${top mem 3}

  ${color #ffffff}${top_mem name 1} ${top_mem pid 1} ${top_mem cpu 1} ${top_mem mem 1}
  ${color #ffffff}${top_mem name 2} ${top_mem pid 2} ${top_mem cpu 2} ${top_mem mem 2}
  ${color #ffffff}${top_mem name 3} ${top_mem pid 3} ${top_mem cpu 3} ${top_mem mem 3}

${color #ffffff}NETWORK
${color white}${hr 1}
  ${color #ffffff}Down : ${color #ffffff}${downspeed wlan0}kb/s${color #ffffff}${alignr}Total : ${color #ffffff}${totaldown wlan0}
  ${color #ffffff}Up   : ${color #ffffff}${upspeed wlan0}kb/s${alignr}Total : ${color #ffffff}${totalup wlan1}


```

---

### Post by Bruce M. on 2008-03-08
> **agentnixon said:**
> whenever Conky refreshes itself, stuff on my desktop disappear. I'm talking about icons of drives, files and folders. If I click and drag to highlight them, they appear again, but then disappear once conky refreshes itself.

Hi agentnixon

You have:

```

own_window_colour hotpink
own_window no
own_window_transparent no

```

Try these lines:

```

own_window_colour hotpink
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
own_window_transparent no
own_window_type override
own_window yes

```

Bruce

---

### Post by agentnixon on 2008-03-08
thanks. It seems to be working now.

---

### Post by Bruce M. on 2008-03-08
> **agentnixon said:**
> thanks. It seems to be working now.

Another thing I noticed in your conky file:

You have:

```
xftalpha 1.0
```

but nothing like:

```

font Zekton:size=8
xftfont Zekton:size=8

```

Where you are using an xftfont in your conky.
Pretty safe to remove that.  :)

Take a look at:
[LIST=1]
[*][Post your .conkyrc files w/ screenshots]("http://ubuntuforums.org/showthread.php?t=281865")
[*] [Conky Weather Revisited V2]("http://ubuntuforums.org/showthread.php?t=666842")
[/LIST]

For some tips and tricks with conky and some really nice setups
Posting conky problems there will always get results too.  :)

If this answered your question you should make the thread [Solved] See: Thread Tools

Have a nice day.
Bruce

---

