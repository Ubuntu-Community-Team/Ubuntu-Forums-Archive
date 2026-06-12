---
title: "Conky Crashes In 14.04"
date: 2015-07-19
forum: General Help
---

### Post by coljohnhannibalsmith on 2015-07-19
Hello,

Conky Crashes In 14.04.

Thanks, Hannibal

---

### Post by QIII on 2015-07-19
Hello!

A description of the crash behavior and a paste of any terminal output might be helpful.

---

### Post by coljohnhannibalsmith on 2015-07-19
Thank You,

As long as I don't run any applications Conky runs fine; but as soon as I open a browser window, all the text blurs.  Conky continues to run; but I can't read the display.  There is no output from the terminal.  I usually start Conky from a desktop launcher.

Thanks, Hannibal

---

### Post by CantankRus on 2015-07-19
Post your conky config.

---

### Post by coljohnhannibalsmith on 2015-07-19
```
# UBUNTU-CONKY
# A comprehensive conky script, configured for use on
# Ubuntu / Debian Gnome, without the need for any external scripts.
#
# Based on conky-jc and the default .conkyrc.
# INCLUDES:
# - tail of /var/log/messages ############################(TRY USING TAIL VARIABLE INSTEAD OF SHELL TAIL)############################################# ######
# - netstat connections to your computer
#
# -- Pengo (conky@pengo.us)


#GENERAL STUFF
double_buffer yes
use_spacer yes
update_interval 2.0
#background yes
#out_to_console no
#total_run_times 0
#${execi 30 wmctrl -a conky}


#WINDOW STUFF
own_window yes
own_window_type override
own_window_transparent yes
#own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
#own_window_hints skip_taskbar,skip_pager


#COLOR STUFF
own_window_colour brown
default_color white #Text #Default colors and also border colors, grey90 == #e5e5e5
default_shade_color black
default_outline_color black


#TEXT AREA STUFF
#minimum_size 250 5 #Minimum size of text area
minimum_size 280 5


#BORDER STUFF
draw_outline no
draw_borders no
draw_shades no
stippled_borders 3
border_margin 9
border_width 10


#FONT STUFF
#font -*-newspaper-*-*-*-*-*-*-*-*-*-*-*-*
use_xft yes
xftfont Bitstream Vera Sans Mono:size=8
xftalpha 0.8
uppercase no


#TEXT ALIGNMENT STUFF
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right
gap_x 10 #Horizontal Gap between borders of screen and text
gap_y 10 #Vertical Gap between borders of screen and text


#TEXT TO BE DISPLAYED IN CONKY WINDOW
################################################## ################

TEXT

$color
${color magenta}SYSTEM ${hr 2}$color
$nodename $sysname $kernel on $machine
Maximum Operating Temperature: CPU 95 C, HDD 60 C
CPU Temp: ${acpitemp} #HDD Temp: ${hddtemp} 
Load: ${loadavg}

${color yellow}Core 0: ${hr 2}$color
Freq: ${freq 1}MHz
${cpubar cpu1 10,70}
${cpugraph cpu1 000000 ffffff}

${color red}Core 1: ${hr 2}$color
Freq: ${freq 2}MHz
${cpubar cpu2 10,70}
${cpugraph cpu2 000000 ffffff}

#${color yellow}Core 2: ${hr 2}$color
#Freq: ${freq 3}MHz
#${cpubar cpu3 10,70}
#${cpugraph cpu3 000000 ffffff}

#${color red}Core 3: ${hr 2}$color
#Freq: ${freq 4}MHz
#${cpubar cpu4 10,70}
#${cpugraph cpu4 000000 ffffff}

NAME             PID     CPU%   MEM%
${top name 1} ${top pid 1} ${top cpu 1} ${top mem 1}
${top name 2} ${top pid 2} ${top cpu 2} ${top mem 2}
${top name 3} ${top pid 3} ${top cpu 3} ${top mem 3}
${top name 4} ${top pid 4} ${top cpu 4} ${top mem 4}
${top name 5} ${top pid 5} ${top cpu 5} ${top mem 5}
${top name 6} ${top pid 6} ${top cpu 6} ${top mem 6}
${top name 7} ${top pid 7} ${top cpu 7} ${top mem 7}
${top name 8} ${top pid 8} ${top cpu 8} ${top mem 8}
#${top name 9} ${top pid 9} ${top cpu 9} ${top mem 9}
#${top name 10} ${top pid 10} ${top cpu 10} ${top mem 10}

${color yellow}MEMORY / DISK ${hr 2}$color
RAM: $memperc% ${membar 6}$color
Swap: $swapperc% ${swapbar 6}$color

${color yellow}NETWORK (${addr eth0}) ${hr 2}$color
Down: $color${downspeed eth0}                  Up: ${upspeed eth0}
${downspeedgraph eth0 25,140 000000 ff0000} ${alignr}${upspeedgraph eth0 25,140 000000 00ff00}$color
Total: ${totaldown eth0}                Total: ${totalup eth0} #${alignr}

Inbound: ${tcp_portmon 1 32767 count}  Outbound: ${tcp_portmon 32768 61000 count}${alignr}  Total:${tcp_portmon 1 65535 count}



#${color yellow}LOGGING ${hr 2}$color
#${execi 30 tail -n3 /var/log/messages | fold -w50}

#wlan0 eth0






```

---

### Post by CantankRus on 2015-07-20
Your conky runs ok here in unity.
Try changing...
```
own_window_type override
```
to
```
own_window_type normal
```

Also look at your gap from the top.
Give enough for the top panel.
Change....
```
gap_y 10
```
to
```
gap_y 40
```

Other than that may be graphics issue.
Are you using proprietary drivers?
Inxi is good to get sysinfo...
```
sudo apt-get install inxi
```

Then post the output from
```
inxi -b
```

---

### Post by coljohnhannibalsmith on 2015-07-20
Additional Info,

The change to: own_window_type normal seems to have resolved the stability issue; however it puts a border around the window, which I don't like. It also puts a minimized window on the task bar; that's even uglier. I am doing the 14.04 build on an older unit and the CPU meters were getting pegged before the crash.  I suspect this unit is stealing CPU cycles for video compositing.

sophie@sophie-Inspiron-1545:~$ inxi -b
System:    Host: sophie-Inspiron-1545 Kernel: 3.16.0-43-generic x86_64 (64 bit) Desktop: Gnome Distro: Ubuntu 14.04 trusty
Machine:   System: Dell product: Inspiron 1545
           Mobo: Dell model: 0G848F Bios: Dell version: A14 date: 12/07/2009
CPU:       Dual core Pentium CPU T4400 (-MCP-) clocked at 2200.00 MHz 
Graphics:  Card: Intel Mobile 4 Series Integrated Graphics Controller 
           X.Org: 1.16.0 drivers: intel (unloaded: fbdev,vesa) Resolution: 1366x768@59.9hz 
           GLX Renderer: Mesa DRI Mobile Intel GM45 Express GLX Version: 2.1 Mesa 10.3.2
Network:   Card-1: Broadcom BCM4312 802.11b/g LP-PHY driver: wl 
           Card-2: Marvell 88E8040 PCI-E Fast Ethernet Controller driver: sky2 
Drives:    HDD Total Size: 320.1GB (2.0% used)
Info:      Processes: 176 Uptime: 1:19 Memory: 810.4/3913.9MB Client: Shell (bash) inxi: 1.9.17 
sophie@sophie-Inspiron-1545:~$ 

Thanks, Hannibal

---

### Post by CantankRus on 2015-07-20
In your config remove the "[COLOR="#FF0000"]#[/COLOR]" from...
```
[COLOR="#FF0000"]#[/COLOR]own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
```

Two changes in compizconfig-settings-manager(ccsm) you need to make
when using **own_window_type normal**

---

### Post by coljohnhannibalsmith on 2015-07-23
Thank You Sir,

Works like a charm.

Hannibal

---

