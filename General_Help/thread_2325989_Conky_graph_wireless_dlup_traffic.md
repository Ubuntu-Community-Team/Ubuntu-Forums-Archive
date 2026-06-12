---
title: "Conky graph wireless dl/up traffic"
date: 2016-05-27
forum: General Help
---

### Post by fbird3 on 2016-05-27
Hello, there!
I need help configuring my conky so that it shows network traffic [download and upload figures, in real time -- kind of...]; I have it done for ethernet already, but doing the same thing for a wireless connection seems to be out of my realm.
If someone could past the configuration part for a wireless router I would be much obliged.

---

### Post by vasa1 on 2016-05-27
> **fbird3 said:**
> Hello, there!
I need help configuring my conky so that it shows network traffic [download and upload figures, in real time -- kind of...]; I have it done for ethernet already, but doing the same thing for a wireless connection seems to be out of my realm.
If someone could past the configuration part for a wireless router I would be much obliged.
It would be nice if you post your existing .conkyrc or conky.conf so that suggestions people provide will match your set-up.

And please mention your version of *buntu. Is it still "my version is Ubuntu 10.04"? Providing such information upfront will save time.

---

### Post by fbird3 on 2016-05-27
Hello, vasa1
I cannot post my .conkyrc at the moment because I am login in from a library; I will do it tomorrow.
My version of Ubuntu is 10.04.
Thank you for any assistance offered.

---

### Post by vasa1 on 2016-05-27
I suggest you should **always** mention that you're using 10.04. Otherwise, people may assume that you're using a currently supported version of *buntu and offer advice based on that assumption. I think it's fair to assume that somethings have changed between 10.04 and currently supported *buntus and that what works for 10.04 **may not work** for currently supported *buntus and vice versa.

---

### Post by fbird3 on 2016-05-28
Suggestion noted, vasa1.

Here is my .conkyrc [the character "+" was used to replace certain areas, but do not interfere with the instructions proper]:

```
# Conky, a system monitor, based on torsmo
#
# Any original torsmo code is licensed under the BSD license
#
# All code written since the fork of torsmo is licensed under the GPL
#
# Please see COPYING for details
#
# Copyright (c) 2004, Hannu Saransaari and Lauri Hakkarainen
# Copyright (c) 2005-2007 Brenden Matthews, Philip Kovacs, et. al. (see AUTHORS)
# All rights reserved.
#
# This program is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
# You should have received a copy of the GNU General Public License
# along with this program.  If not, see <http://www.gnu.org/licenses/>.
#
# $Id: conky.conf 1193 2008-06-21 20:37:58Z ngarofil $


alignment top_left
gap_x 735
gap_y 120
background yes
border_width 1
cpu_avg_samples 2
default_color black
default_outline_color black
default_shade_color black
draw_borders no
draw_graph_borders yes
draw_outline no
draw_shades no
font 6x10
minimum_size 5 5
net_avg_samples 2
no_buffers yes
out_to_console no
own_window yes
own_window_colour black
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
stippled_borders 0
update_interval 5.0
uppercase no
use_spacer right
show_graph_scale no
show_graph_range no
use_xft yes
xftfont Andale Mono:size=7
mail_spool /var/mail/+


TEXT
${scroll 55 $nodename - $sysname $kernel on $machine }
${color orange} ${hr 2}$color
${color black}Uptime:$color $uptime$alignr${color black}${time %a %d %b %Y  %H:%M}
${color black}Frequency (in GHz):$color $freq_g
${color black}RAM:$color $mem/$memmax - $memperc% ${membar 4}
${color black}Swap:$color $swap/$swapmax - $swapperc% ${swapbar 4}
${color black}CPU1 Usage:$color ${cpu cpu1}% ${cpubar cpu1}
${color black}CPU2 Usage:$color ${cpu cpu2}% ${cpubar cpu2}
${color black}Processes:$color $processes  ${color black}Running:$color $running_processes
${color black}System Mail: $alignr${new_mails /var/mail/+ 3s} new message(s)
${color red}FILE SYSTEM ${hr 2}$color
Ubuntu: $color${fs_free /} / ${fs_size /} ${fs_bar 6 /}
+:  $color${fs_free /media/+} / ${fs_size /media/+} ${fs_bar 6 /media/+}
+:  $color${fs_free /media/+} / ${fs_size /media/+} ${fs_bar 6 /media/+}
+:  $color${fs_free /media/+} / ${fs_size /media/+} ${fs_bar 6 /media/+}
+:  $color${fs_free /media/+} / ${fs_size /media/+} ${fs_bar 6 /media/+}
#+:  $color${fs_free /media/+} / ${fs_size /media/+} ${fs_bar 6 /media/+}
#+:  $color${fs_free /media/+} / ${fs_size /media/+} ${fs_bar 6 /media/+}
+:  $color${fs_free /media/+} / ${fs_size /media/+} ${fs_bar 6 /media/+}
#+:  $color${fs_free /media/+} / ${fs_size /media/+} ${fs_bar 6 /media/+}

${color black}NETWORK (${addr eth0}) ${hr 2}$color
Down: $color${downspeed eth0}/s ${alignr}Up: ${upspeed eth0}/s
${downspeedgraph eth0 25,140 000000 ff0000} ${alignr}${upspeedgraph eth0
25,140 000000 00ff00}$color
Total: ${totaldown eth0} ${alignr}Total: ${totalup eth0}
Inbound: ${tcp_portmon 1 32767 count} Outbound: ${tcp_portmon 32768
61000 count}${alignr}Total: ${tcp_portmon 1 65535 count}

${color orange} ${hr 2}$color
${color black}Name              PID    CPU%   MEM%  TIME%
${color black} ${top name 1} ${top pid 1} ${top cpu 1} ${top mem 1} ${top time 1}
${color black} ${top name 2} ${top pid 2} ${top cpu 2} ${top mem 2} ${top time 2}
${color black} ${top name 3} ${top pid 3} ${top cpu 3} ${top mem 3} ${top time 3}
${color black} ${top name 4} ${top pid 4} ${top cpu 4} ${top mem 4} ${top time 4}
${color black} ${top name 5} ${top pid 5} ${top cpu 5} ${top mem 5} ${top time 5}
${color orange} ${hr 2}$color
```

Thanking you in advance for any assistance.

---

### Post by deadflowr on 2016-05-28
Unless I'm missing something, it should be as easy as replacing/changing this:
```
${color black}NETWORK (${addr **eth0**}) ${hr 2}$color
Down: $color${downspeed **eth0**}/s ${alignr}Up: ${upspeed **eth0**}/s
${downspeedgraph **eth0** 25,140 000000 ff0000} ${alignr}${upspeedgraph **eth0**
25,140 000000 00ff00}$color
Total: ${totaldown **eth0**} ${alignr}Total: ${totalup **eth0**}
```
with this
```
${color black}NETWORK (${addr **wlan0**}) ${hr 2}$color
Down: $color${downspeed** wlan0**}/s ${alignr}Up: ${upspeed **wlan0**}/s
${downspeedgraph** wlan0** 25,140 000000 ff0000} ${alignr}${upspeedgraph **wlan0**
25,140 000000 00ff00}$color
Total: ${totaldown **wlan0**} ${alignr}Total: ${totalup **wlan0**}
```

wlan0 is the normal wifi name, but yours might differ
I'd use:
```
ifconfig
```
to see, sometimes it might be wlan1, or something.

---

### Post by fbird3 on 2016-05-28
Thank you, vasa1
I have tried it many years ago, without success, but then I was almost always on ethernet; when I began using a wireless connection, I tried and it did not work [for whatever reason]; now I am exclusively using a wireless connection and this comes really handy.
All the best.

---

### Post by Old_Grey_Wolf on 2016-05-28
Once you get the wireless code to work you may want to use IF statements to get the conky to display wireless or wired connection graphs depending on how you are connected at the time.

```
${if_existing /sys/class/net/wlan0/operstate up}Wireless Network:
**Put code for the wireless graphs here.**
${endif}
${if_existing /sys/class/net/eth0/operstate up}Wired Network:
**Put code for the wired graphs here.**
${endif}

```

If you are connected with wired and wireless at the same time it will display both; however, conky may not fit on your screen properly depending on how your conky is sized.

---

### Post by fbird3 on 2016-05-28
Thank you, Old_Grey_Wolf
I have already added your suggestion to my .conkyrc and it works for the wireless connection I have; I am sure it will work just as well if I get a wired connection sometime in the future.
It saved me a lot of time and skulduggery.
Thank you, very much!

---

