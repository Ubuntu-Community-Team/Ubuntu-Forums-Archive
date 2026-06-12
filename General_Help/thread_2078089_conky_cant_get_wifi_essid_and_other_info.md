---
title: "conky cant get wifi essid and other info"
date: 2012-10-30
forum: General Help
---

### Post by schmee2 on 2012-10-30
Conky can't get my wireless essid due to the wl kernel module and neither could my normal user account. If I did ```
sudo iwconfig wlan0
``` it was fine, and if I ran conky as root it was fine, but I don't want to do that. 

The solution was the [here]("http://stackoverflow.com/questions/12230740/linux-how-to-get-wireless-ssid-without-root-permission") more specifically [this link]("http://packetlife.net/blog/2010/mar/19/sniffing-wireshark-non-root-user/") is what I followed, and it worked great. For awhile.. Now it doesn't work anymore and I'm not sure why. 

It worked for my user acount. If I run iwconfig I see all the wireless info. If I run ```
${exec iwconfig wlan0}
``` conky spits out all the wireless info, including ssid. But using conky's built in ```
${wireless_essid wlan0}
``` returns nothing for ESSID and 'Not-Associated' for the AP MAC. 

I've tried all I can, including ```
sudo chmod u+s /sbin/iwconfig
``` (which also worked before, but now fails to work for conky)

edit: I should also clarify that I edited the udev rule to rename eth1 to wlan0, as eth1 is the standard interface name that comes up with the wl driver.

---

### Post by Habitual on 2012-10-30
```
conky -v
```

please.

---

### Post by schmee2 on 2012-10-30
```

Conky 1.9.0 compiled Mon May 21 17:53:20 UTC 2012 for Linux 2.6.24-29-server (x86_64)

Compiled in features:

System config file: /etc/conky/conky.conf
Package library path: /usr/lib/conky

 X11:
  * Xdamage extension
  * XDBE (double buffer extension)
  * Xft
  * ARGB visual

 Music detection:
  * Audacious
  * MPD
  * MOC
  * XMMS2

 General:
  * math
  * hddtemp
  * portmon
  * Curl
  * RSS
  * Weather (METAR)
  * Weather (XOAP)
  * wireless
  * config-output
  * Imlib2
  * apcupsd
  * iostats
  * ncurses
  * Lua

  Lua bindings:
   * Cairo
   * Imlib2

```

---

### Post by Habitual on 2012-10-30
Is this "you"?
[http://askubuntu.com/questions/209566/permissions-issue-with-conky-getting-essid-tried-all-the-usual](http://askubuntu.com/questions/209566/permissions-issue-with-conky-getting-essid-tried-all-the-usual)

```

sudo grep $(whoami) /etc/sudoers
ls -al /sbin/iwconfig
groups $(whoami)

``` output please. Also, post your .conkyrc file that has the code

I just noticed on my laptop (slackware14) that my sole ESSID does not show up when I used iwconfig.

It **did** show up in iwconfig *after* I used WICD to connect to the access point.

---

### Post by schmee2 on 2012-10-30
> **Habitual said:**
> Is this "you"?
[http://askubuntu.com/questions/209566/permissions-issue-with-conky-getting-essid-tried-all-the-usual](http://askubuntu.com/questions/209566/permissions-issue-with-conky-getting-essid-tried-all-the-usual)

```

sudo grep $(whoami) /etc/sudoers
ls -al /sbin/iwconfig
groups $(whoami)

``` output please. Also, post your .conkyrc file that has the code

I just noticed on my laptop (slackware14) that my sole ESSID does not show up when I used iwconfig.

It **did** show up in iwconfig *after* I used WICD to connect to the access point.

Yep, that's me. I'm using the shotgun method of problem solving ;)

sudo grep $(whoami) /etc/sudoers returns nothing, I have not modified sudoers and this is a standard 12.10 install. 

```

$ ls -al /sbin/iwconfig 
-rwxr-x--- 1 root iwconfig 27008 May  3 18:12 /sbin/iwconfig

$ groups $(whoami)
chris : chris adm cdrom sudo dip plugdev lpadmin sambashare iwconfig
```

Just for completeness: 
```

$ sudo getcap /sbin/iwconfig 
/sbin/iwconfig = cap_net_admin,cap_net_raw+eip
```

As far as I can tell I am setup correctly to use the get/setcap method.

Here is my WIP conky config:

```

# -*- conf -*-
#
# ~/.conkyrc - Conky configuration file
#
# By arpbook http://www.arpbook.com
#
# Heavily inspired by .conkyrc file of
# Henrik Brix Andersen <henrik@brixandersen.dk>
#
# Thanks to him.
#
#
# ·ë{¶«¡Çø}&#8212;æÂê®Úî&#339;ô&#8364;âÒÌÏÈ¬µÙ@©&#9830;ß~÷&#376;´É[å»ÛÁ]&#8211;ÆÅÊ¤&#376;ªï&#338;Ô¥À·ÎÍË|Óû#¢~¿¿·\± 
#######################################################################
# variables ###########################################################

# fork to background ? ################################################
background no

# font settings #######################################################
use_xft yes

#font monospace-8
xftfont Acknowledge TT BRK:size=8

#xftfont Edit Undo BRK:size=8
#xftfont Visitor TT2 BRK:size=10
uppercase yes
#override_utf8_local yes

# update every 1 secs #################################################
update_interval 1

# stay running forever ################################################
total_run_times 0

# draw to root window #################################################
own_window yes
own_window_transparent yes
own_window_type desktop

# avoid flickering ####################################################
double_buffer yes

# size ################################################################
minimum_size 1366 768
maximum_width 1366

# position ############################################################
alignment top_left

gap_x 0
gap_y 0

# colors ##############################################################
default_color white
default_shade_color white
default_outline_color black
# custom colors #######################################################
color0 FFFFFF
color1 04FF00
color2 A2AEC6
color3 696969
color4 D3D3D3
color5 6495ED
color6 87CEFA
color7 FF0000
color8 BBBBBB
color9 262729


# borders #############################################################
draw_borders no
draw_graph_borders no
stippled_borders 8
#border_margin 4
border_width 1

# shades ##############################################################
draw_shades no

# outline #############################################################
draw_outline no

# spacer ##############################################################
use_spacer false

# buffers (Substract (file system) buffers from used memory?)##########
no_buffers yes

# sampling ############################################################
cpu_avg_samples 2
net_avg_samples 2

# configuration #######################################################
TEXT
${voffset 10}${offset 120}$color8 /$color3 System$color8 /
${offset 120}$color2 $sysname$color9 -$color2 $machine
${offset 120}$color2 $kernel
${offset 120}$color2 Chris$color9 on$color2 $nodename
${offset 120}$color6 ${time %A %d/%m/%y %kh%M}
${offset 120}$color2 Uptime :$color6 $uptime
${offset 120}$color2 Load :$color6 $loadavg
${offset 120}$color4 ${loadgraph 15,125 262729 87CEFA -l}

${voffset -80}${offset 700}$color8 /$color3 LCD$color8 /
${offset 700}$color2 Brightness: $color4  ${exec echo "scale=0; $(cat /sys/class/backlight/intel_backlight/brightness) / 4882 *100" | bc -q}%

#${offset 10}$color8 /$color3 Mails$color8 /
#${offset 15}$color2 arpbook : $color4${imap_unseen mail.mac.com "adresse mac" "mot de passe mac"}
#${offset 15}$color2 larnel  : $color4${imap_unseen mail.mac.com "adresse mac" "mot de passe mac"}

${voffset -60}${offset 980}$color8 /$color3 System Logs$color8 /

${offset 980}$color2 Dmesg
${offset 980}$color2 >$color4${execi 30 /usr/bin/tail -n 5 /var/log/dmesg | cut -c 23-73 | sed -n 1p}
${offset 980}$color2 >$color4${execi 30 /usr/bin/tail -n 4 /var/log/dmesg | cut -c 23-73 | sed -n 1p}
${offset 980}$color2 >$color4${execi 30 /usr/bin/tail -n 3 /var/log/dmesg | cut -c 23-73 | sed -n 1p}
${offset 980}$color2 >$color4${execi 30 /usr/bin/tail -n 2 /var/log/dmesg | cut -c 23-73 | sed -n 1p}
${offset 980}$color2 >$color4${execi 30 /usr/bin/tail -n 1 /var/log/dmesg | cut -c 23-73 | sed -n 1p}

${offset 980}$color2 Security
${offset 980}$color2 >$color4${execi 30 /usr/bin/tail -n 5 /var/log/auth.log | cut -c 23-73 | sed -n 1p}
${offset 980}$color2 >$color4${execi 30 /usr/bin/tail -n 4 /var/log/auth.log | cut -c 23-73 | sed -n 1p}
${offset 980}$color2 >$color4${execi 30 /usr/bin/tail -n 3 /var/log/auth.log | cut -c 23-73 | sed -n 1p}
${offset 980}$color2 >$color4${execi 30 /usr/bin/tail -n 2 /var/log/auth.log | cut -c 23-73 | sed -n 1p}
${offset 980}$color2 >$color4${execi 30 /usr/bin/tail -n 1 /var/log/auth.log | cut -c 23-73 | sed -n 1p}

${offset 980}$color2 System
${offset 980}$color2 >$color4${execi 30 /usr/bin/tail -n 5 /var/log/syslog | cut -c 23-73 | sed -n 1p}
${offset 980}$color2 >$color4${execi 30 /usr/bin/tail -n 4 /var/log/syslog | cut -c 23-73 | sed -n 1p}
${offset 980}$color2 >$color4${execi 30 /usr/bin/tail -n 3 /var/log/syslog | cut -c 23-73 | sed -n 1p}
${offset 980}$color2 >$color4${execi 30 /usr/bin/tail -n 2 /var/log/syslog | cut -c 23-73 | sed -n 1p}
${offset 980}$color2 >$color4${execi 30 /usr/bin/tail -n 1 /var/log/syslog | cut -c 23-73 | sed -n 1p}

#${voffset -100}${offset 980}$color8 /$color3 Ubuntu Planet RSS$color8 /
#${offset 985}$color2 >$color4${rss http://planet.ubuntu-fr.org/feed/tag/Accueil/rss2 60 item_title 0}
#${offset 990}$color2 >$color4${rss http://planet.ubuntu-fr.org/feed/tag/Accueil/rss2 60 item_title 1}
#${offset 1000}$color2 >$color4${rss http://planet.ubuntu-fr.org/feed/tag/Accueil/rss2 60 item_title 2}
#${offset 1005}$color2 >$color4${rss http://planet.ubuntu-fr.org/feed/tag/Accueil/rss2 60 item_title 3}
#${offset 1010}$color2 >$color4${rss http://planet.ubuntu-fr.org/feed/tag/Accueil/rss2 60 item_title 4}


#${offset 1040}$color8 /$color3 DYP RSS$color8 /
#${offset 1045}$color2 >$color4${rss http://yaen.pujol.free.fr/dotclear/rss 60 item_title 0}
#${offset 1045}$color2 >$color4${rss http://yaen.pujol.free.fr/dotclear/rss 60 item_title 1}
#${offset 1045}$color2 >$color4${rss http://yaen.pujol.free.fr/dotclear/rss 60 item_title 2}
#${offset 1045}$color2 >$color4${rss http://yaen.pujol.free.fr/dotclear/rss 60 item_title 3}
#${offset 1045}$color2 >$color4${rss http://yaen.pujol.free.fr/dotclear/rss 60 item_title 4}

${voffset -180}${offset 130}$color8 /$color3 CPU Core 1$color8 /
${offset 130}$color2 Temperature :$color4 ${execi 10 sensors | grep 'Core 0' | cut -c18-23 }C  -  $color2 Frequency : $color4${freq 1}$color2 MHz
${offset 130}$color2 Load: $color9 ${cpubar cpu1 6,220} $color4${cpu cpu1}$color2 %
${offset 130}$color4 ${cpugraph cpu1 15,255 262729 87CEFA}
${offset 130}$color8 /$color3 CPU Core 2$color8 /
${offset 130}$color2 Temperature :$color4 ${execi 10 sensors | grep 'Core 1' | cut -c18-23}C  -  $color2 Frequency : $color4${freq 2}$color2 MHz 
${offset 130}$color2 Load: $color9 ${cpubar cpu2 6,220} $color4${cpu cpu2}$color2 %
${offset 130}$color4 ${cpugraph cpu2 15,255 262729 87CEFA}

#${voffset -80}${offset 1040}$color8 /$color3 CrunchBang RSS$color8 /
#${offset 1045}$color2 >$color4${rss http://crunchbang.org/feed/ 60 item_title 0}
#${offset 1045}$color2 >$color4${rss http://crunchbang.org/feed/ 60 item_title 1}
#${offset 1045}$color2 >$color4${rss http://crunchbang.org/feed/ 60 item_title 2}

${if_existing /sys/class/net/wlan0/operstate up} 
${voffset 30}${offset 40}$color8 /$color3 Wifi (wlan0) $color8 /
#${exec iwconfig wlan0}
${offset 40}$color2 Proxy : ${execpi 30 ~/scripts/checkproxy}
${offset 40}$color2 essid : $color4${wireless_essid wlan0}$color2 - MAC : $color4${wireless_ap wlan0}
${offset 40}$color2 Wifi Level : $color4${wireless_link_qual wlan0}$color2 /$color4 ${wireless_link_qual_max wlan0}$color2 - Quality: $color4 ${wireless_link_qual_perc wlan0}
${offset 40}$color2 IPv4 : $color4${addr wlan0}$color2 -$color4 ${execi 1800 curl ifconfig.me}
${offset 40}$color2 Inbound: $color4${tcp_portmon 1 32767 count}$color2 Outbound:$color4 ${tcp_portmon 32768 61000 count}$color2 Total:$color4 ${tcp_portmon 1 65535 count}
${offset 40}$color2 Down : $color4 ${downspeed wlan0}$color2 kb/s - Total: $color4${totaldown wlan0}
${offset 40}$color4 ${downspeedgraph wlan0 15,250 262729 87CEFA}
${offset 40}$color2 Up : ${offset 6} $color4 ${upspeed wlan0}$color2 kb/s - Total:$color4 ${totalup wlan0}
${offset 40}$color4 ${upspeedgraph wlan0 15,250 262729 87CEFA}
${offset 40} $color2 IN 1:$color4 ${tcp_portmon 1 32767 lport 0} ${tcp_portmon 1 32767 rhost 0} ${tcp_portmon 1 32767 rip 0} ${tcp_portmon 1 32767 rport 0}
${offset 40}$color2 OUT 1:$color4 ${tcp_portmon 32768 61000 lport 0} ${tcp_portmon 32768 61000 rhost 0} ${tcp_portmon 32768 61000 rip 0} ${tcp_portmon 32768 61000 rport 0}

${else}
${if_existing /sys/class/net/eth0/operstate up} 
${voffset 30}${offset 40}$color8 /$color3 Wired (eth0)$color8 /
${offset 40}$color2 Proxy : ${execpi 30 ~/scripts/checkproxy}
${offset 40}$color2 IPv4 : $color4${addr eth0}$color2 -$color4 ${execi 1800 curl ifconfig.me}
${offset 40}$color2 Inbound: $color4${tcp_portmon 1 32767 count}$color2 Outbound:$color4 ${tcp_portmon 32768 61000 count}$color2 Total:$color4 ${tcp_portmon 1 65535 count}
${offset 40}$color2 Down : $color4 ${downspeed eth0}$color2 kb/s - Total: $color4${totaldown eth0}
${offset 40}$color4 ${downspeedgraph eth0 15,250 262729 87CEFA}
${offset 40}$color2 Up : ${offset 6} $color4 ${upspeed eth0}$color2 kb/s - Total:$color4 ${totalup eth0}
${offset 40}$color4 ${upspeedgraph eth0 15,250 262729 87CEFA}
${offset 40}$color2 IN 1:$color4 ${tcp_portmon 1 32767 lport 0} ${tcp_portmon 1 32767 rhost 0} ${tcp_portmon 1 32767 rip 0} ${tcp_portmon 1 32767 rport 0}
${offset 40}$color2 OUT 1:$color4 ${tcp_portmon 32768 61000 lport 0} ${tcp_portmon 32768 61000 rhost 0} ${tcp_portmon 32768 61000 rip 0} ${tcp_portmon 32768 61000 rport 0}
${else}
${voffset 30}${offset 40}$color8 /$color3 No Network Connection$color8 /
${offset 40}
${offset 40}
${offset 40}
${offset 40}
${offset 40}
${offset 40}
${offset 40}
${endif}${endif}


${voffset -100}${offset 1100}$color8 /$color3 Power$color8 /
${offset 1100}$color2 ${acpiacadapter ACAD}$color4  ${battery BAT1}
${offset 1100}$color2 Time Left :$color4  ${battery_time BAT1}
${offset 1100}$color9 ${battery_bar 6,160 BAT1}

${voffset 80}${offset 20}$color8 /$color3 Volumes$color8 /
${offset 35}$color2 !-root :  $color4 ${fs_used_perc /}% - ${fs_used /} + ${fs_free /} = ${fs_size /}
${offset 35}$color9 ${fs_bar 6,320 /}
${offset 50}$color2 !-home :  $color4 ${fs_used_perc /home}% - ${fs_used /home} + ${fs_free /home} = ${fs_size /home}
${offset 50}$color9 ${fs_bar 6,320 /home}
#${offset 65}$color2 hardy-root : $color4 ${fs_used_perc /media/hardy-system}% - ${fs_used /media/hardy-system} + ${fs_free /media/hardy-system} = ${fs_size /media/hardy-system}
#${offset 65}$color9 ${fs_bar 6,320 /media/hardy-system}
#${offset 80}$color2 hardy-home : $color4 ${fs_used_perc /media/hardy-home}% - ${fs_used /media/hardy-home} + ${fs_free /media/hardy-home} = ${fs_size /media/hardy-home}
#${offset 80}$color9 ${fs_bar 6,320 /media/hardy-home}
#${offset 95}$color2 mac :   $color4 ${fs_used_perc /media/macbook-hd}% - ${fs_used /media/macbook-hd} + ${fs_free /media/macbook-hd} = ${fs_size /media/macbook-hd}
#${offset 95}$color9 ${fs_bar 6,320 /media/macbook-hd}

${voffset 0}${offset 600}$color8 /$color3 Memory$color8 /
${offset 605}$color2 RAM: ${offset 0} $color9 ${membar 6,200}$color4 $mem ($memperc%)
${offset 610}$color2 Swap: $color9 ${swapbar 6,200}$color4 $swap ($swapperc%)

${voffset -90}${offset 1100}$color8 /$color3 Activity$color8 /
#${offset 1095}$color2 Hdd Temp:$color4 ${hddtemp /dev/sda}
${offset 1090}$color2 Read/Write: $color4 $diskio
${offset 1080}$color2 Process :$color4 $running_processes$color2 /$color4 $processes
${offset 1080}$color6 ${top name 1}$alignr$color4 ${top cpu 1}%
${offset 1080}$color5 ${top name 2}$alignr$color4 ${top cpu 2}%
${offset 1080}$color5 ${top name 3}$alignr$color4 ${top cpu 3}%
${offset 1080}$color5 ${top name 4}$alignr$color4 ${top cpu 4}%
${offset 1080}$color5 ${top name 5}$alignr$color4 ${top cpu 5}%
${offset 1080} ${diskiograph 15,180 262729 87CEFA}

```

---

### Post by Habitual on 2012-10-30
Chris:

[I've tried all I can, including     sudo chmod u+s /sbin/iwconfig (which also worked before]("http://askubuntu.com/questions/209566/permissions-issue-with-conky-getting-essid-tried-all-the-usual") ...

before what?

JJ

---

### Post by schmee2 on 2012-10-30
Before last night, when I didn't read the warnings about tasksel very well and it uninstalled half of the packages on my system. I re-installed ubuntu-desktop along with everything else I could think of, but it didn't work. So I re installed Ubuntu (using wubi again) but that still didn't fix it. 

The only thing I can think of is that when wubi 'uninstalled' the old version of ubuntu it didn't erase the old files but I find that very very unlikely.

---

### Post by Habitual on 2012-10-30
Chris:

Yeah, that wubi stuff is not anything I have any experience in.
conky yes, wubi no.

Sorry.

JJ

---

### Post by schmee2 on 2012-10-30
> **Habitual said:**
> Chris:

Yeah, that wubi stuff is not anything I have any experience in.
conky yes, wubi no.

Sorry.

JJ

Not a problem, I appreciate your help :)

---

### Post by schmee2 on 2012-11-01
Alright, so the solution for anyone else that ends up here:

sudo setcap cap_net_raw,cap_net_admin=eip /usr/bin/conky

Details are [here]("http://packetlife.net/blog/2010/mar/19/sniffing-wireshark-non-root-user/") but basically you need to give conky permissions to use the network interface.

---

### Post by Habitual on 2012-11-01
Chris:

Good follow-up.

Glad you got it working!

+1

---

