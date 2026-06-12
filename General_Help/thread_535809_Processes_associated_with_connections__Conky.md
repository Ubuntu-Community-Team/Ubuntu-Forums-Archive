---
title: "Processes associated with connections / Conky"
date: 2007-08-26
forum: General Help
---

### Post by notwen on 2007-08-26
I'm curious to upon connecting to a network via Ethernet or wireless whether a process is launched throughout the duration of that connection?  This is all due to me wanting my conky to automatically update if I connect to a wired or wireless network and pending on which connection is established I'm wanting different output.  Looking though conky's available variables I believe if I can associate either the wired or wireless connection to a process invoked once the connection is made I can have conky check to see if that process is running and in turn output the appropriate information.  Any information is appreciated and if you need more info I'll be glad to offer what I can.  Thanks again. =]

---

### Post by notwen on 2007-08-28
No one knows if the kernel or GNOME launches a process that runs the duration of a network connection, whether it be wired or wireless?  I'm simply wanting to use this info to base my conky script on.  Conky has a variable "if_process running" that I'm wanting to use.  I simply just need to find out if there is a process that is invoked once eth0(wired) or eth1(wifi) connects to a network.  In turn I would make conky output wired or wireless info on my desktop. 

 If there is not a automated process that does such a thing, are there any apps that use minimal resources that are constantly looking for an active connection(possibly even specify which eth*) to check, so I could install it and have conky use it as an association w/ eth0 or eth1 being active.

---

### Post by levele304 on 2007-08-28
I am also having trouble configuring conky to display info related to connections (I use a dell wireless 1390 WLAN)

The graphs show only a flat unchanging line and the IP addresses show all zeros.

Please Help!

---

### Post by levele304 on 2007-08-28
So i was browsing through the "POST YOUR .CONKYRSC" thread and one guy had his script for a file called ".conky_wifi"  posted.

So i took this as a clue and created the file and used his script code and started it up.

However, still no luck.

Could it be the cut values are off?

If so, how do I make them what I want to be?

Please help!

---

### Post by levele304 on 2007-08-28
I also want to mention that I DID try changing all eth0 values to ath0 and that DID NOT WORK.

Any guidance is appreciated

---

### Post by notwen on 2007-08-28
> **levele304 said:**
> I also want to mention that I DID try changing all eth0 values to ath0 and that DID NOT WORK.

Any guidance is appreciated

We are having very different issues here. =p   Have you tried eth1?  I'm wanting different output depending on which connection is currently active.  So if eth0 was active onyl info for eth0 would be displayed through conky and vice versa. =]

---

### Post by levele304 on 2007-08-28
lol in that case I apologise for hijacking your thread (although no one has responded yet)

I have indeed tried eth and that has not worked either.

---

### Post by notwen on 2007-08-28
For my laptop eth0 would be my wired connection and eth1 is wireless.

---

### Post by levele304 on 2007-08-28
Hey i finally got it working.  

It wasnt any of those but rather WLAN0.

I found this out by typing in ifconfig in the terminal.

In any case, i aplogise for taking your thread offcourse.

Thanks for the help!

---

### Post by firedrow on 2008-01-09
Notwen,

Don't know if you're still checking this thread or have found your answer yet, but I was playing with this today and got it to work.  I'll post my .conkyrc below.  Change the username in /home/drowland/ to your username, and if your wireless isn't ath0 then change it as well.  The relevant section is near the end, it looks all jumbled, but to keep my layout uniform that section has to be like that.  I have pulled the whole config from various places and ripped it apart again.

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
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer yes
use_xft no

# Update interval in seconds
update_interval 3.0

# Minimum size of text area
# minimum_size 250 5

# Draw shades?
draw_shades no

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no
font arial
uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 3

# border margins
border_margin 9

# border width
border_width 10

# Default colors and also border colors, grey90 == #e5e5e5
default_color grey

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

TEXT

$color
${color D0FE1F}SYSTEM ${hr 2}$color
$nodename $sysname $kernel on $machine

${color D0FE1F}CPU ${hr 2}$color
${freq}MHz   ${alignr}Load: ${loadavg}
$cpubar
${cpugraph cpu1 25,140 000000 D0FE1F} ${alignr}${cpugraph cpu2 25,140 000000 D0FE1F}
NAME                PID      CPU%      MEM%
${top name 1} ${top pid 1}   ${top cpu 1}    ${top mem 1}
${top name 2} ${top pid 2}   ${top cpu 2}    ${top mem 2}
${top name 3} ${top pid 3}   ${top cpu 3}    ${top mem 3}
${top name 4} ${top pid 4}   ${top cpu 4}    ${top mem 4}

${color D0FE1F}DISK / MEMORY ${hr 2}$color
Root:  ${fs_free_perc /} %   ${fs_bar 6 /}$color
RAM:   $memperc%   ${membar 6}$color
Swap:  $swapperc%   ${swapbar 6}$color

${color D0FE1F}BATTERY ${hr 2}$color
${battery_percent BAT1}% ${battery_bar BAT1}${execi 30 rm -f .conky_eth0; ifconfig -s | grep eth0 > /dev/null && ifconfig -a eth0 | grep 'inet addr:' > /dev/null && touch .conky_eth0}${execi 30 rm -f .conky_ath0; ifconfig -s | grep ath0 > /dev/null && ifconfig -a ath0 | grep 'inet addr:' > /dev/null && touch .conky_ath0}
${if_existing /home/drowland/.conky_eth0}
${color D0FE1F}NETWORK INFO (ETH0: ${addr eth0}) ${hr 2}$color
Down: ${downspeed eth0} k/s ${alignr}Up: ${upspeed eth0} k/s
${color lightgray}${downspeedgraph eth0 25,140 000000 ff0000} ${alignr}${upspeedgraph eth0
25,140 000000 00ff00}$color
Total: ${totaldown eth0} ${alignr}Total: ${totalup eth0}
Inbound: ${tcp_portmon 1 32767 count} Outbound: ${tcp_portmon 32768
61000 count}${alignr}Total: ${tcp_portmon 1 65535 count}
${endif}${if_existing /home/drowland/.conky_ath0}
${color D0FE1F}NETWORK INFO (ATH0: ${addr ath0}) ${hr 2}$color
SSID: ${wireless_essid ath0} ${alignr}Mode: ${wireless_mode ath0}
Speed: ${wireless_bitrate ath0} ${alignr}Signal: ${wireless_link_qual ath0}
${wireless_link_qual_perc ath0} ${wireless_link_bar ath0}

Down: $color${downspeed ath0} k/s ${alignr}Up: ${upspeed ath0} k/s
${downspeedgraph ath0 25,140 000000 ff0000} ${alignr}${upspeedgraph ath0
25,140 000000 00ff00}$color
Total: ${totaldown ath0} ${alignr}Total: ${totalup ath0}
Inbound: ${tcp_portmon 1 32767 count} Outbound: ${tcp_portmon 32768
61000 count}${alignr}Total: ${tcp_portmon 1 65535 count}
${endif}

```

---

