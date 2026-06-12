---
title: "[SOLVED] customizing ~/.conkyrc"
date: 2008-07-06
forum: General Help
---

### Post by tjwoosta on 2008-07-06
i have been trying to make a custom .conkyrc by editing one i found


my first problem is i cant seem to make my text black

and my second problem is..
i have used gconf-editor to make my nautilus not show the desktop (that way i can set and use four different wallpapers on my cube in compiz)

now even when i make conky transparent it shows a box with a piece of the first wallpaper on all the other workspaces (see the attached thumbnails)


heres my ~/.conkyrc so far
```
background yes
use_xft yes
xftfont HandelGotD:size=8
xftalpha 0.1
update_interval 0.5
total_run_times 0
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
minimum_size 200 5
maximum_width 200
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no
default_color black
default_shade_color black
default_outline_color black
alignment top_right
gap_x 18
gap_y 48
no_buffers yes
uppercase no
cpu_avg_samples 2
net_avg_samples 1
override_utf8_locale no
use_spacer yes

TEXT
$sysname $kernel $alignr $machine
Intel Pentium Dual $alignr${freq_g cpu0}Ghz
$alignr
${cpugraph cpu0 16,200 ffffff ffffff}
CPU:1  ${cpu cpu1}% ${cpubar cpu1}
CPU:2  ${cpu cpu2}% ${cpubar cpu2}

MEM $alignc $mem / $memmax $alignr $memperc%
$membar

/home $alignc ${fs_used /home} / ${fs_size /home} $alignr ${fs_free_perc /home}%
${fs_bar /home}
/fat $alignc ${fs_used /media/fat} / ${fs_size /media/fat} $alignr ${fs_free_perc /media/fat}%
${fs_bar /media/fat}

Disk i/o ${diskiograph 16,200} 

Processes 
$alignr $running_processes Running 
$alignr $processes Sleeping

Top Processes

CPU $alignr CPU% MEM%

${top name 1}$alignr${top cpu 1}${top mem 1}
${top name 2}$alignr${top cpu 2}${top mem 2}
${top name 3}$alignr${top cpu 2}${top mem 3}

MEM $alignr CPU% MEM%

${top_mem name 1}$alignr${top_mem cpu 1}${top_mem mem 1}
${top_mem name 2}$alignr${top_mem cpu 2}${top_mem mem 2}
${top_mem name 3}$alignr${top_mem cpu 3}${top_mem mem 3}

IP on wlan0 $alignr ${addr wlan0}

Down $alignr ${downspeed wlan0} kb/s
${downspeedgraph wlan0}
Up $alignr ${upspeed wlan0} kb/s
${upspeedgraph wlan0 16,200}

Connections ${tcp_portmon 32768 61000 count} ${alignr} Service/Port

${tcp_portmon 32768 61000 rhost 0} ${alignr} ${tcp_portmon 32768 61000 rservice 0}
${tcp_portmon 32768 61000 rhost 1} ${alignr} ${tcp_portmon 32768 61000 rservice 1}
${tcp_portmon 32768 61000 rhost 2} ${alignr} ${tcp_portmon 32768 61000 rservice 2}
${tcp_portmon 32768 61000 rhost 3} ${alignr} ${tcp_portmon 32768 61000 rservice 3}
${tcp_portmon 32768 61000 rhost 4} ${alignr} ${tcp_portmon 32768 61000 rservice 4}
${tcp_portmon 32768 61000 rhost 5} ${alignr} ${tcp_portmon 32768 61000 rservice 5}
```

any ideas about either problem?

---

### Post by nkri on 2008-07-06
OK, to make the text black, add "${color black}" without the quotes before each line after TEXT.  For example, to make the system identifier line black, it would be:
> ${color black}$sysname $kernel $alignr $machine
Just copy and paste this into the beginning of each line you want to be black.  For reference, this is my .conkyrc:

> # THIS CONFIG RELIES ON 2 SCRIPTS, CPUSPEED AND CPUTEMP
# YOUR SYSTEM MAY NOT REQUIRE THEM, REPLACE AS DESIRED

# maintain spacing between certain elements
use_spacer yes

# set to yes if you want conky to be forked in the background
background no

use_xft yes

# Xft font when Xft is enabled
#xftfont Bitstream Vera Sans Mono-7
#xftfont Andale Mono-9
#xftfont Clean-8
#xftfont cubicfive10:pixelsize=8
#xftfont squaredance10:pixelsize=14
xftfont swf!t_v02:pixelsize=10

# Text alpha when using Xft
xftalpha 6
mail_spool $MAIL

# Update interval in seconds
update_interval 1.0

# Create own window instead of using desktop (required in nautilus)
own_window yes

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 280 5

# Draw shades?
draw_shades yes

# Draw outlines?
draw_outline no # amplifies text

# Draw borders around text
draw_borders no

# Stippled borders?
stippled_borders 0

# border margins
border_margin 9

# border width
border_width 1

# Default colors and also border colors, grey90 == #e5e5e5
default_color grey90
default_shade_color black
default_outline_color DarkGrey

# Text alignment, other possible values are commented
alignment top_left
#alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 400
gap_y 150

# Subtract file system buffers from used memory?
no_buffers no

# set to yes if you want all text to be in uppercase
uppercase no

# stuff after 'TEXT' will be formatted on screen

TEXT
${color #0077ff}$sysname $kernel $machine - $nodename 
${color #ffcb48}UPTIME:$color $uptime
${color #ffcb48}PROCESSING$color ${stippled_hr }
   ${color #98c2c7}CPU:$color     ${execi 5 cpuspeed}MHz       $cpu% 
   ${execi 5 cputemp}Â°C
   ${color #78af78}$cpubar
   ${color #78af78}${cpugraph 78af78 a3a3a3}
 
   ${color #98c2c7}NAME             PID       CPU%      MEM%
   ${color #e5e5e5}${top name 1} ${top pid 1}   ${top cpu 1}    ${top mem 1}
   ${color #c4c4c4}${top name 2} ${top pid 2}   ${top cpu 2}    ${top mem 2}
   ${color #a3a3a3}${top name 3} ${top pid 3}   ${top cpu 3}    ${top mem 3}
   ${color #828282}${top name 4} ${top pid 4}   ${top cpu 4}    ${top mem 4}

${offset 0}${color #ffcb48}MEMORY AND STORAGE:$color ${stippled_hr }
   ${color grey}File systems:
   / $color${fs_free /}/${fs_size /} 
   ${fs_bar 3,150 /}
   ${offset 0}${color #98c2c7}RAM:
   ${offset 0}${color }$memperc% $mem/$memmax
   ${offset 0}${membar 3,150}
   ${offset 0}${color #98c2c7}SWAP:
   ${offset 0}${color }$swapperc% $swap/$swapmax
   ${offset 0}${swapbar 3,150}
   ${offset 0}${color #98c2c7}ROOT:
   ${offset 0}${color }${fs_used /}/${fs_size /}
   ${offset 0}${fs_bar 3,150 /}
   ${offset 0}${color #98c2c7}HOME:
   ${offset 0}${color }${fs_used /home}/${fs_size /home}
   ${offset 0}${fs_bar 3,150 /home}

Good luck!
-nkri

---

### Post by tjwoosta on 2008-07-06
ok now i have this
```

background yes
use_xft yes
xftfont HandelGotD:size=8
xftalpha 0.1
update_interval 0.5
total_run_times 0
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
minimum_size 200 5
maximum_width 200
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no
default_color black
default_shade_color black
default_outline_color black
alignment top_right
gap_x 18
gap_y 48
no_buffers yes
uppercase no
cpu_avg_samples 2
net_avg_samples 1
override_utf8_locale no
use_spacer yes

TEXT
${color black}$sysname $kernel $alignr $machine
${color black}Intel Pentium Dual $alignr${freq_g cpu0}Ghz
${color black}$alignr
${color black}${cpugraph cpu0 16,200 ffffff ffffff}
${color black}CPU:1  ${cpu cpu1}% ${cpubar cpu1}
${color black}CPU:2  ${cpu cpu2}% ${cpubar cpu2}

${color black}MEM $alignc $mem / $memmax $alignr $memperc%
${color black}$membar

${color black}/home $alignc ${fs_used /home} / ${fs_size /home} $alignr ${color black}${fs_free_perc /home}%
${color black}${fs_bar /home}
${color black}/fat $alignc ${fs_used /media/fat} / ${fs_size /media/fat} ${color black}$alignr ${fs_free_perc /media/fat}%
${color black}${fs_bar /media/fat}

${color black}Disk i/o ${diskiograph 16,200} 

${color black}Processes 
${color black}$alignr $running_processes Running 
${color black}$alignr $processes Sleeping

${color black}Top Processes

${color black}CPU $alignr CPU% MEM%

${color black}${top name 1}$alignr${top cpu 1}${top mem 1}
${color black}${top name 2}$alignr${top cpu 2}${top mem 2}
${color black}${top name 3}$alignr${top cpu 2}${top mem 3}

${color black}MEM $alignr CPU% MEM%

${color black}${top_mem name 1}$alignr${top_mem cpu 1}${top_mem mem 1}
${color black}${top_mem name 2}$alignr${top_mem cpu 2}${top_mem mem 2}
${color black}${top_mem name 3}$alignr${top_mem cpu 3}${top_mem mem 3}

${color black}IP on wlan0 $alignr ${addr wlan0}

${color black}Down $alignr ${downspeed wlan0} kb/s
${color black}${downspeedgraph wlan0}
${color black}Up $alignr ${upspeed wlan0} kb/s
${color black}${upspeedgraph wlan0 16,200}

${color black}Connections ${tcp_portmon 32768 61000 count} ${alignr} Service/Port

${color black}${tcp_portmon 32768 61000 rhost 0} ${alignr} ${tcp_portmon 32768 61000 rservice 0}
${color black}${tcp_portmon 32768 61000 rhost 1} ${alignr} ${tcp_portmon 32768 61000 rservice 1}
${color black}${tcp_portmon 32768 61000 rhost 2} ${alignr} ${tcp_portmon 32768 61000 rservice 2}
${color black}${tcp_portmon 32768 61000 rhost 3} ${alignr} ${tcp_portmon 32768 61000 rservice 3}
${color black}${tcp_portmon 32768 61000 rhost 4} ${alignr} ${tcp_portmon 32768 61000 rservice 4}
${color black}${tcp_portmon 32768 61000 rhost 5} ${alignr} ${tcp_portmon 32768 61000 rservice 5}
```

everything still looks like it did before (nothing changed)

what am i doing wrong?

also about the 4 different wallpapers, do you think it work if i unsticky conky and just have four seperate instances of conky (one on each desktop)

---

### Post by nkri on 2008-07-06
Ok, figured it out.  You had two conflicting instances of Xft fonts, and since they counteract each other they made wierd things happen.  I just removed one line and now it looks great!
```
background yes
use_xft yes
xftfont HandelGotD:size=8
update_interval 0.5
total_run_times 0
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
minimum_size 200 5
maximum_width 200
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no
default_color black
default_shade_color black
default_outline_color black
alignment top_right
gap_x 18
gap_y 48
no_buffers yes
uppercase no
cpu_avg_samples 2
net_avg_samples 1
override_utf8_locale no
use_spacer yes

TEXT
${color black}$sysname $kernel $alignr $machine
${color black}Intel Pentium Dual $alignr${freq_g cpu0}Ghz
${color black}$alignr
${color black}${cpugraph cpu0 16,200 ffffff ffffff}
${color black}CPU:1  ${cpu cpu1}% ${cpubar cpu1}
${color black}CPU:2  ${cpu cpu2}% ${cpubar cpu2}

${color black}MEM $alignc $mem / $memmax $alignr $memperc%
${color black}$membar

${color black}/home $alignc ${fs_used /home} / ${fs_size /home} $alignr ${color black}${fs_free_perc /home}%
${color black}${fs_bar /home}
${color black}/fat $alignc ${fs_used /media/fat} / ${fs_size /media/fat} ${color black}$alignr ${fs_free_perc /media/fat}%
${color black}${fs_bar /media/fat}

${color black}Disk i/o ${diskiograph 16,200} 

${color black}Processes 
${color black}$alignr $running_processes Running 
${color black}$alignr $processes Sleeping

${color black}Top Processes

${color black}CPU $alignr CPU% MEM%

${color black}${top name 1}$alignr${top cpu 1}${top mem 1}
${color black}${top name 2}$alignr${top cpu 2}${top mem 2}
${color black}${top name 3}$alignr${top cpu 2}${top mem 3}

${color black}MEM $alignr CPU% MEM%

${color black}${top_mem name 1}$alignr${top_mem cpu 1}${top_mem mem 1}
${color black}${top_mem name 2}$alignr${top_mem cpu 2}${top_mem mem 2}
${color black}${top_mem name 3}$alignr${top_mem cpu 3}${top_mem mem 3}

${color black}IP on wlan0 $alignr ${addr wlan0}

${color black}Down $alignr ${downspeed wlan0} kb/s
${color black}${downspeedgraph wlan0}
${color black}Up $alignr ${upspeed wlan0} kb/s
${color black}${upspeedgraph wlan0 16,200}

${color black}Connections ${tcp_portmon 32768 61000 count} ${alignr} Service/Port

${color black}${tcp_portmon 32768 61000 rhost 0} ${alignr} ${tcp_portmon 32768 61000 rservice 0}
${color black}${tcp_portmon 32768 61000 rhost 1} ${alignr} ${tcp_portmon 32768 61000 rservice 1}
${color black}${tcp_portmon 32768 61000 rhost 2} ${alignr} ${tcp_portmon 32768 61000 rservice 2}
${color black}${tcp_portmon 32768 61000 rhost 3} ${alignr} ${tcp_portmon 32768 61000 rservice 3}
${color black}${tcp_portmon 32768 61000 rhost 4} ${alignr} ${tcp_portmon 32768 61000 rservice 4}
${color black}${tcp_portmon 32768 61000 rhost 5} ${alignr} ${tcp_portmon 32768 61000 rservice 5}
```

As for the different desktops, I'm not sure (I use one wallpaper so I've never had to deal with this), but I think it should work.  If it doesn't, it probably won't damage or crash your system, so it's worth a try:).

Good luck!
-nkri

---

### Post by tjwoosta on 2008-07-06
thanks nkri for all your help, it looks great

(i cant try the multiple instances yet because i just upgraded my compiz and now i cant have 4 different wallpapers anymore, so i need to uninstall the new compiz and reinstall my old one first)

---

### Post by nkri on 2008-07-06
No problem!  Glad I could help!

---

### Post by tjwoosta on 2008-07-07
ok, so back to the 4 different wallpapers

is there any way of opening 4 seperate instances of conky at login and have each one automatically go onto its own workspace?

---

### Post by sayakb on 2008-07-07
More **conkyrc**s, see: [http://ubuntuforums.org/showthread.php?t=281865&highlight=conkyrc](http://ubuntuforums.org/showthread.php?t=281865&highlight=conkyrc)

---

### Post by chalewa on 2008-07-07
quick question about conky...

i have it set to autostart when i turn on my computer, but for some reason instead of being transparent against the desktop background, it is opaque and covers up part of my panel at the top of my screen (i will edit this post when i get home with a screen shot). what is bizarre is that i just have to give a ```
killall conky
``` in the terminal, and then another ```
conky
``` to start it, and it is fine. 

ideas?

---

### Post by SkonesMickLoud on 2008-07-07
> **chalewa said:**
> quick question about conky...

i have it set to autostart when i turn on my computer, but for some reason instead of being transparent against the desktop background, it is opaque and covers up part of my panel at the top of my screen (i will edit this post when i get home with a screen shot). what is bizarre is that i just have to give a ```
killall conky
``` in the terminal, and then another ```
conky
``` to start it, and it is fine. 

ideas?

Are you using compiz?

In your Session >> Startup Programs menu, edit your conky  entry to  say:

```
sleep 10 && conky
```

This will make conky hold for 10 seconds until it starts, giving your panels time to load and will prevent compiz from drawing shadows around it.  If 10 doesn't work, try 15.

---

### Post by kaivalagi on 2008-07-07
> **tjwoosta said:**
> ok, so back to the 4 different wallpapers

is there any way of opening 4 seperate instances of conky at login and have each one automatically go onto its own workspace?

Running 4 seperate conky's is easy, create 4 separate conkyrc files e.g. conky1, conky2, conky3 and conky4

Each conky instance can be started using the -c option e.g. "conky -c ~/conky1". You can then create a script to fire them all off like so:

```
#!/bin/sh
conky -c ~/conky1 &
conky -c ~/conky2 &
conky -c ~/conky3 &
conky -c ~/conky4 &
```

Not sure about the different conkys on each desktop. Plasma_NZ did figure out how to get a conky running on 1 desktop rather than all 4. That might be a start... His post's about it and the responses are on my conky weather forecast thread here: [http://ubuntuforums.org/showthread.php?p=5254653#post5254653](http://ubuntuforums.org/showthread.php?p=5254653#post5254653)

If you figure anything out, please let us all know :)

Hope that helps

---

### Post by kaivalagi on 2008-07-07
> **SkonesMickLoud said:**
> Are you using compiz?

In your Session >> Startup Programs menu, edit your conky entry to  say:

```
sleep 10 && conky
```

This will make conky hold for 10 seconds until it starts, giving your panels time to load and will prevent compiz from drawing shadows around it.  If 10 doesn't work, try 15.

I've been playing with a script to delay until the time is right, it works most of the time:

```
#!/bin/sh

	# Wait for gnome-session/notification-area-applet to load before starting anything else
	echo "waiting for gnome-session to be present before starting applications..."

	while true; do

	    #if [ $(pgrep -u,mark notification-ar) > 0 ]; then
	    if [ $(pgrep -u,mark gnome-session) > 0 ]; then

			# wait an extra 10 seconds just in case
			sleep 10

			conky &

			break;
	    else
			sleep 1;
	    fi

	done 
```

If anyone knows of improvements that can be made let me know :)
Is there a process better suited to check for before allowing conky to run?

---

### Post by chalewa on 2008-07-07
> **SkonesMickLoud said:**
> Are you using compiz?

In your Session >> Startup Programs menu, edit your conky  entry to  say:

```
sleep 10 && conky
```

This will make conky hold for 10 seconds until it starts, giving your panels time to load and will prevent compiz from drawing shadows around it.  If 10 doesn't work, try 15.

> **kaivalagi said:**
> I've been playing with a script to delay until the time is right, it works most of the time:

```
	# Wait for gnome-session/notification-area-applet to load before starting anything else
	echo "waiting for gnome-session to be present before starting applications..."

	while true; do

	    #if [ $(pgrep -u,mark notification-ar) > 0 ]; then
	    if [ $(pgrep -u,mark gnome-session) > 0 ]; then

			# wait an extra 10 seconds just in case
			sleep 10

			conky &

			break;
	    else
			sleep 1;
	    fi

	done 
```

If anyone knows of improvements that can be made let me know :)
Is there a process better suited to check for before allowing conky to run?

ah ok thanks a lot guys

---

### Post by tad1073 on 2008-07-07
conky is causing my desktop icons to disappear

```
# conky configuration
# edited by darcon@gmail.com

# set to yes if you want Conky to be forked in the background
background yes

# X font when Xft is disabled, you can pick one with program xfontsel
#font 5x7
#font 6x10
#font 7x13
#font 8x13
#font 9x15
#font *mintsmild.se*
#font -*-*-*-*-*-*-34-*-*-*-*-*-*-*


# Use Xft?
use_xft yes

# Xft font when Xft is enabled
#xftfont Bitstream Vera Sans Mono:size=8
xftfont Veranda:size=8

# Text alpha when using Xft
xftalpha 0.8

# Print everything to console?
# out_to_console no

# mail spool
#mail_spool $MAIL

# Update interval in seconds
update_interval 0.5

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window no

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 1680 12

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Stippled borders?
stippled_borders 8

# border margins
border_margin 4

# border width
border_width 1

# Default colors and also border colors
default_color white
default_shade_color black
default_outline_color white

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 0
gap_y 5

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# number of cpu samples to average
# set to 1 to disable averaging
cpu_avg_samples 2

# number of net samples to average
# set to 1 to disable averaging
net_avg_samples 2

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale no
draw_graph_borders no

# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer right
#Note: doesn't work in conky 1.2 =(

#   mldonkey_hostname     Hostname for mldonkey stuff, defaults to localhost
#   mldonkey_port         Mldonkey port, 4001 default
#   mldonkey_login        Mldonkey login, default none
#   mldonkey_password     Mldonkey password, default none


# Possible variables to be used:
#
#      Variable         Arguments                  Description                

# 	addr              (interface)   IP address for an interface
# 	acpiacadapter                   ACPI ac adapter state.                   
# 	acpifan                         ACPI fan state                           
# 	acpitemp                        ACPI temperature.                        
# 	adt746xcpu                      CPU temperature from therm_adt746x       
# 	adt746xfan                      Fan speed from therm_adt746x             
# 	alignr            (num)         Right-justify text, with space of N
# 	alignc                          Align text to centre
# 	battery           (num)         Remaining capasity in ACPI or APM        
# 					battery. ACPI battery number can be      
# 					given as argument (default is BAT0).     
# 	buffers                         Amount of memory buffered                
# 	cached                          Amount of memory cached                  
# 	color             (color)       Change drawing color to color            
# 	cpu                             CPU usage in percents                    
# 	cpubar            (height)      Bar that shows CPU usage, height is      
# 					bar's height in pixels                 
# 	cpugraph          (height),(width) (gradient colour 1) (gradient colour 2)
# 					CPU usage graph, with optional colours in hex,
# 					minus the #.
# 	downspeed         net           Download speed in kilobytes              
# 	downspeedf        net           Download speed in kilobytes with one     
# 					decimal                                  
# 	downspeedgraph    net (height),(width) (gradient colour 1) (gradient colour 2)
# 					Download speed graph, colours defined in
# 					hex, minus the #.
# 	exec              shell command Executes a shell command and displays    
# 					the output in conky. warning: this      
# 					takes a lot more resources than other    
# 					variables. I'd recommend coding wanted   
# 					behaviour in C and posting a patch :-).  
# 	execbar           shell command Same as exec, except if the first value
# 					return is a value between 0-100, it
# 					will use that number for a bar.
# 					The size for the bar is currently fixed,
# 					but that may change in the future.
# 	execgraph         shell command Same as execbar, but graphs values
# 	execi             interval, shell command
#  					Same as exec but with specific interval. 
# 					Interval can't be less than              
# 					update_interval in configuration.        
#	font		  font		Specify a different font.  Only applies
#					to one line.
# 	fs_bar            (height), (fs)Bar that shows how much space is used on 
# 					a file system. height is the height in   
# 					pixels. fs is any file on that file      
# 					system.                                  
# 	fs_free           (fs)          Free space on a file system available    
# 					for users.                               
# 	fs_free_perc      (fs)          Free percentage of space on a file       
# 					system available for users.              
# 	fs_size           (fs)          File system size                         
# 	fs_used           (fs)          File system used space                   
# 	hr                (height)      Horizontal line, height is the height in 
# 					pixels                                   
# 	i2c               (dev), type, n  I2C sensor from sysfs (Linux 2.6). dev   
# 					may be omitted if you have only one I2C  
# 					device. type is either in (or vol)       
# 					meaning voltage, fan meaning fan or
# 					temp/tempf (first in C, second in F)
# 					meaning temperature. n is number of the  
# 					sensor. See /sys/bus/i2c/devices/ on     
# 					your local computer.                     
# 	if_running        (process)     if PROCESS is running, display
# 					everything if_running and the matching $endif
# 	if_existing       (file)        if FILE exists, display everything between
# 					if_existing and the matching $endif
# 	if_mounted        (mountpoint)  if MOUNTPOINT is mounted, display everything between
# 					if_mounted and the matching $endif
# 	else                            Text to show if any of the above are not true
# 	kernel                          Kernel version                          
# 	linkstatus        (interface)   Get the link status for wireless connections
# 	loadavg           (1), (2), (3) System load average, 1 is for past 1     
# 					minute, 2 for past 5 minutes and 3 for   
# 					past 15 minutes.                         
# 	machine                         Machine, i686 for example                
# 	mails                           Mail count in mail spool. You can use    
# 					program like fetchmail to get mails from 
# 					some server using your favourite         
# 					protocol. See also new_mails.            
# 	mem                             Amount of memory in use                  
# 	membar            (height)      Bar that shows amount of memory in use   
# 	memmax                          Total amount of memory                   
# 	memperc                         Percentage of memory in use
# 	
# 	metar_ob_time
# 	metar_temp
# 	metar_tempf                     Temp in F
# 	metar_windchill
# 	metar_dew_point                 There are a bunch of these
# 	metar_rh                        and they are self-explanatory
# 	metar_windspeed
# 	metar_winddir
# 	metar_swinddir
# 	metar_cloud
# 	metar_u2d_time
# 	
# 	ml_upload_counter               total session upload in mb
# 	ml_download_counter             total session download in mb
# 	ml_nshared_files                number of shared files
# 	ml_shared_counter               total session shared in mb, buggy
# 					in some mldonkey versions
# 	ml_tcp_upload_rate              tcp upload rate in kb/s
# 	ml_tcp_download_rate            tcp download rate in kb/s
# 	ml_udp_upload_rate              udp upload rate in kb/s
# 	ml_udp_download_rate            udp download rate in kb/s
# 	ml_ndownloaded_files            number of completed files
# 	ml_ndownloading_files           number of downloading files
# 	
# 	mpd_artist			Artist in current MPD song
# 					(must be enabled at compile)
# 	mpd_album			Album in current MPD song
# 	mpd_bar           (height)      Bar of mpd's progress
# 	mpd_bitrate                     Bitrate of current song
# 	mpd_status                      Playing, stopped, et cetera.
# 	mpd_title			Title of current MPD song
# 	mpd_vol				MPD's volume
# 	mpd_elapsed                     Song's elapsed time
# 	mpd_length                      Song's length
# 	mpd_percent                     Percent of song's progress
# 	new_mails                       Unread mail count in mail spool.         
# 	nodename                        Hostname                                 
# 	outlinecolor      (color)       Change outline color                     
# 	pre_exec          shell command Executes a shell command one time before 
# 					conky displays anything and puts output 
# 					as text.                                 
# 	processes                       Total processes (sleeping and running)   
# 	running_processes               Running processes (not sleeping),        
# 					requires Linux 2.6                       
# 	shadecolor        (color)       Change shading color                     
# 	stippled_hr       (space),      Stippled (dashed) horizontal line        
# 			(height)        
# 	swapbar           (height)      Bar that shows amount of swap in use     
# 	swap                            Amount of swap in use                    
# 	swapmax                         Total amount of swap                     
# 	swapperc                        Percentage of swap in use                
# 	sysname                         System name, Linux for example           
# 	offset            pixels        Move text over by N pixels
# 	tail              logfile, lines (interval)
# 					Displays last N lines of supplied text
# 					text file.  If interval is not supplied,
# 					Conky assumes 2x Conky's interval.
# 					Max of 30 lines.
# 					Max of 30 lines can be displayed.
# 	time              (format)      Local time, see man strftime to get more 
# 					information about format                 
# 	totaldown         net           Total download, overflows at 4 GB on     
# 					Linux with 32-bit arch and there doesn't 
# 					seem to be a way to know how many times  
# 					it has already done that before conky   
# 					has started.                            
# 	top               type, num     This takes arguments in the form:
# 					top <name> <number>
# 					Basically, processes are ranked from 
# 					highest to lowest in terms of cpu
# 					usage, which is what <num> represents.
# 					The types are: "name", "pid", "cpu", and
# 					"mem".
# 					There can be a max of 10 processes listed.
# 	top_mem           type, num     Same as top, except sorted by mem usage
# 					instead of cpu
# 	totalup           net           Total upload, this one too, may overflow 
# 	updates                         Number of updates (for debugging)        
# 	upspeed           net           Upload speed in kilobytes                
# 	upspeedf          net           Upload speed in kilobytes with one       
# 					decimal                                  
# 	upspeedgraph      net (height),(width)  (gradient colour 1) (gradient colour 2)
# 					Upload speed graph, colours defined in
# 					hex, minus the #.
# 	uptime                          Uptime                                   
# 	uptime_short                    Uptime in a shorter format               
# 	
# 	seti_prog                       Seti@home current progress
# 	seti_progbar      (height)      Seti@home current progress bar
# 	seti_credit                     Seti@hoome total user credit


# variable is given either in format $variable or in ${variable}. Latter
# allows characters right after the variable and must be used in network
# stuff because of an argument

# stuff after 'TEXT' will be formatted on screen
	
TEXT
      ${time %a, } ${color }${time %e %B %G} ${time %Z,    }${color }${time %H:%M:%S}|${machine} ${sysname} kernel ${kernel}|CPU:${color}${cpu}% ${cpugraph cpu0 12,75} ${color} @${freq cpu0} Mhz|MEM: ${color}${mem} ${color}|${color} UP: ${color}${uptime}${color}|${color} NET:${color} ${downspeedgraph ath0 12,75} ${downspeed ath0} Kb/s ${color} ${totaldown ath0}down${upspeedgraph ath0 12,75} ${upspeed ath0} Kb/s ${color} ${totalup ath0}${color}up|Swap:${swap}|Root: ${color}${fs_free /} ${color}|Home: ${color }${font}${fs_free /home} ${color}|Media: ${color }${font}${fs_free /media/disk} ${color}|Top Prc ${color}${top name 1} 
	 
```

---

### Post by easybake on 2008-07-07
> **tad1073 said:**
> conky is causing my desktop icons to disappear


Put this anywhere above TEXT ```
window_type override
```

---

### Post by nkri on 2008-07-07
You have to either disable double buffer (may flicker depending on your system) or give conky its own window (uglier, but works without a doubt).

Window:
```
# conky configuration
# edited by darcon@gmail.com

# set to yes if you want Conky to be forked in the background
background yes

# X font when Xft is disabled, you can pick one with program xfontsel
#font 5x7
#font 6x10
#font 7x13
#font 8x13
#font 9x15
#font *mintsmild.se*
#font -*-*-*-*-*-*-34-*-*-*-*-*-*-*


# Use Xft?
use_xft yes

# Xft font when Xft is enabled
#xftfont Bitstream Vera Sans Mono:size=8
xftfont Veranda:size=8

# Text alpha when using Xft
xftalpha 0.8

# Print everything to console?
# out_to_console no

# mail spool
#mail_spool $MAIL

# Update interval in seconds
update_interval 0.5

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window yes

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 1680 12

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Stippled borders?
stippled_borders 8

# border margins
border_margin 4

# border width
border_width 1

# Default colors and also border colors
default_color white
default_shade_color black
default_outline_color white

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 0
gap_y 5

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# number of cpu samples to average
# set to 1 to disable averaging
cpu_avg_samples 2

# number of net samples to average
# set to 1 to disable averaging
net_avg_samples 2

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale no
draw_graph_borders no

# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer right
#Note: doesn't work in conky 1.2 =(

#   mldonkey_hostname     Hostname for mldonkey stuff, defaults to localhost
#   mldonkey_port         Mldonkey port, 4001 default
#   mldonkey_login        Mldonkey login, default none
#   mldonkey_password     Mldonkey password, default none


# Possible variables to be used:
#
#      Variable         Arguments                  Description                

# 	addr              (interface)   IP address for an interface
# 	acpiacadapter                   ACPI ac adapter state.                   
# 	acpifan                         ACPI fan state                           
# 	acpitemp                        ACPI temperature.                        
# 	adt746xcpu                      CPU temperature from therm_adt746x       
# 	adt746xfan                      Fan speed from therm_adt746x             
# 	alignr            (num)         Right-justify text, with space of N
# 	alignc                          Align text to centre
# 	battery           (num)         Remaining capasity in ACPI or APM        
# 					battery. ACPI battery number can be      
# 					given as argument (default is BAT0).     
# 	buffers                         Amount of memory buffered                
# 	cached                          Amount of memory cached                  
# 	color             (color)       Change drawing color to color            
# 	cpu                             CPU usage in percents                    
# 	cpubar            (height)      Bar that shows CPU usage, height is      
# 					bar's height in pixels                 
# 	cpugraph          (height),(width) (gradient colour 1) (gradient colour 2)
# 					CPU usage graph, with optional colours in hex,
# 					minus the #.
# 	downspeed         net           Download speed in kilobytes              
# 	downspeedf        net           Download speed in kilobytes with one     
# 					decimal                                  
# 	downspeedgraph    net (height),(width) (gradient colour 1) (gradient colour 2)
# 					Download speed graph, colours defined in
# 					hex, minus the #.
# 	exec              shell command Executes a shell command and displays    
# 					the output in conky. warning: this      
# 					takes a lot more resources than other    
# 					variables. I'd recommend coding wanted   
# 					behaviour in C and posting a patch :-).  
# 	execbar           shell command Same as exec, except if the first value
# 					return is a value between 0-100, it
# 					will use that number for a bar.
# 					The size for the bar is currently fixed,
# 					but that may change in the future.
# 	execgraph         shell command Same as execbar, but graphs values
# 	execi             interval, shell command
#  					Same as exec but with specific interval. 
# 					Interval can't be less than              
# 					update_interval in configuration.        
#	font		  font		Specify a different font.  Only applies
#					to one line.
# 	fs_bar            (height), (fs)Bar that shows how much space is used on 
# 					a file system. height is the height in   
# 					pixels. fs is any file on that file      
# 					system.                                  
# 	fs_free           (fs)          Free space on a file system available    
# 					for users.                               
# 	fs_free_perc      (fs)          Free percentage of space on a file       
# 					system available for users.              
# 	fs_size           (fs)          File system size                         
# 	fs_used           (fs)          File system used space                   
# 	hr                (height)      Horizontal line, height is the height in 
# 					pixels                                   
# 	i2c               (dev), type, n  I2C sensor from sysfs (Linux 2.6). dev   
# 					may be omitted if you have only one I2C  
# 					device. type is either in (or vol)       
# 					meaning voltage, fan meaning fan or
# 					temp/tempf (first in C, second in F)
# 					meaning temperature. n is number of the  
# 					sensor. See /sys/bus/i2c/devices/ on     
# 					your local computer.                     
# 	if_running        (process)     if PROCESS is running, display
# 					everything if_running and the matching $endif
# 	if_existing       (file)        if FILE exists, display everything between
# 					if_existing and the matching $endif
# 	if_mounted        (mountpoint)  if MOUNTPOINT is mounted, display everything between
# 					if_mounted and the matching $endif
# 	else                            Text to show if any of the above are not true
# 	kernel                          Kernel version                          
# 	linkstatus        (interface)   Get the link status for wireless connections
# 	loadavg           (1), (2), (3) System load average, 1 is for past 1     
# 					minute, 2 for past 5 minutes and 3 for   
# 					past 15 minutes.                         
# 	machine                         Machine, i686 for example                
# 	mails                           Mail count in mail spool. You can use    
# 					program like fetchmail to get mails from 
# 					some server using your favourite         
# 					protocol. See also new_mails.            
# 	mem                             Amount of memory in use                  
# 	membar            (height)      Bar that shows amount of memory in use   
# 	memmax                          Total amount of memory                   
# 	memperc                         Percentage of memory in use
# 	
# 	metar_ob_time
# 	metar_temp
# 	metar_tempf                     Temp in F
# 	metar_windchill
# 	metar_dew_point                 There are a bunch of these
# 	metar_rh                        and they are self-explanatory
# 	metar_windspeed
# 	metar_winddir
# 	metar_swinddir
# 	metar_cloud
# 	metar_u2d_time
# 	
# 	ml_upload_counter               total session upload in mb
# 	ml_download_counter             total session download in mb
# 	ml_nshared_files                number of shared files
# 	ml_shared_counter               total session shared in mb, buggy
# 					in some mldonkey versions
# 	ml_tcp_upload_rate              tcp upload rate in kb/s
# 	ml_tcp_download_rate            tcp download rate in kb/s
# 	ml_udp_upload_rate              udp upload rate in kb/s
# 	ml_udp_download_rate            udp download rate in kb/s
# 	ml_ndownloaded_files            number of completed files
# 	ml_ndownloading_files           number of downloading files
# 	
# 	mpd_artist			Artist in current MPD song
# 					(must be enabled at compile)
# 	mpd_album			Album in current MPD song
# 	mpd_bar           (height)      Bar of mpd's progress
# 	mpd_bitrate                     Bitrate of current song
# 	mpd_status                      Playing, stopped, et cetera.
# 	mpd_title			Title of current MPD song
# 	mpd_vol				MPD's volume
# 	mpd_elapsed                     Song's elapsed time
# 	mpd_length                      Song's length
# 	mpd_percent                     Percent of song's progress
# 	new_mails                       Unread mail count in mail spool.         
# 	nodename                        Hostname                                 
# 	outlinecolor      (color)       Change outline color                     
# 	pre_exec          shell command Executes a shell command one time before 
# 					conky displays anything and puts output 
# 					as text.                                 
# 	processes                       Total processes (sleeping and running)   
# 	running_processes               Running processes (not sleeping),        
# 					requires Linux 2.6                       
# 	shadecolor        (color)       Change shading color                     
# 	stippled_hr       (space),      Stippled (dashed) horizontal line        
# 			(height)        
# 	swapbar           (height)      Bar that shows amount of swap in use     
# 	swap                            Amount of swap in use                    
# 	swapmax                         Total amount of swap                     
# 	swapperc                        Percentage of swap in use                
# 	sysname                         System name, Linux for example           
# 	offset            pixels        Move text over by N pixels
# 	tail              logfile, lines (interval)
# 					Displays last N lines of supplied text
# 					text file.  If interval is not supplied,
# 					Conky assumes 2x Conky's interval.
# 					Max of 30 lines.
# 					Max of 30 lines can be displayed.
# 	time              (format)      Local time, see man strftime to get more 
# 					information about format                 
# 	totaldown         net           Total download, overflows at 4 GB on     
# 					Linux with 32-bit arch and there doesn't 
# 					seem to be a way to know how many times  
# 					it has already done that before conky   
# 					has started.                            
# 	top               type, num     This takes arguments in the form:
# 					top <name> <number>
# 					Basically, processes are ranked from 
# 					highest to lowest in terms of cpu
# 					usage, which is what <num> represents.
# 					The types are: "name", "pid", "cpu", and
# 					"mem".
# 					There can be a max of 10 processes listed.
# 	top_mem           type, num     Same as top, except sorted by mem usage
# 					instead of cpu
# 	totalup           net           Total upload, this one too, may overflow 
# 	updates                         Number of updates (for debugging)        
# 	upspeed           net           Upload speed in kilobytes                
# 	upspeedf          net           Upload speed in kilobytes with one       
# 					decimal                                  
# 	upspeedgraph      net (height),(width)  (gradient colour 1) (gradient colour 2)
# 					Upload speed graph, colours defined in
# 					hex, minus the #.
# 	uptime                          Uptime                                   
# 	uptime_short                    Uptime in a shorter format               
# 	
# 	seti_prog                       Seti@home current progress
# 	seti_progbar      (height)      Seti@home current progress bar
# 	seti_credit                     Seti@hoome total user credit


# variable is given either in format $variable or in ${variable}. Latter
# allows characters right after the variable and must be used in network
# stuff because of an argument

# stuff after 'TEXT' will be formatted on screen
	
TEXT
      ${time %a, } ${color }${time %e %B %G} ${time %Z,    }${color }${time %H:%M:%S}|${machine} ${sysname} kernel ${kernel}|CPU:${color}${cpu}% ${cpugraph cpu0 12,75} ${color} @${freq cpu0} Mhz|MEM: ${color}${mem} ${color}|${color} UP: ${color}${uptime}${color}|${color} NET:${color} ${downspeedgraph ath0 12,75} ${downspeed ath0} Kb/s ${color} ${totaldown ath0}down${upspeedgraph ath0 12,75} ${upspeed ath0} Kb/s ${color} ${totalup ath0}${color}up|Swap:${swap}|Root: ${color}${fs_free /} ${color}|Home: ${color }${font}${fs_free /home} ${color}|Media: ${color }${font}${fs_free /media/disk} ${color}|Top Prc ${color}${top name 1}
```

Buffer:
```
# conky configuration
# edited by darcon@gmail.com

# set to yes if you want Conky to be forked in the background
background yes

# X font when Xft is disabled, you can pick one with program xfontsel
#font 5x7
#font 6x10
#font 7x13
#font 8x13
#font 9x15
#font *mintsmild.se*
#font -*-*-*-*-*-*-34-*-*-*-*-*-*-*


# Use Xft?
use_xft yes

# Xft font when Xft is enabled
#xftfont Bitstream Vera Sans Mono:size=8
xftfont Veranda:size=8

# Text alpha when using Xft
xftalpha 0.8

# Print everything to console?
# out_to_console no

# mail spool
#mail_spool $MAIL

# Update interval in seconds
update_interval 0.5

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window no

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer no

# Minimum size of text area
minimum_size 1680 12

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Stippled borders?
stippled_borders 8

# border margins
border_margin 4

# border width
border_width 1

# Default colors and also border colors
default_color white
default_shade_color black
default_outline_color white

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 0
gap_y 5

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# number of cpu samples to average
# set to 1 to disable averaging
cpu_avg_samples 2

# number of net samples to average
# set to 1 to disable averaging
net_avg_samples 2

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale no
draw_graph_borders no

# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer right
#Note: doesn't work in conky 1.2 =(

#   mldonkey_hostname     Hostname for mldonkey stuff, defaults to localhost
#   mldonkey_port         Mldonkey port, 4001 default
#   mldonkey_login        Mldonkey login, default none
#   mldonkey_password     Mldonkey password, default none


# Possible variables to be used:
#
#      Variable         Arguments                  Description                

# 	addr              (interface)   IP address for an interface
# 	acpiacadapter                   ACPI ac adapter state.                   
# 	acpifan                         ACPI fan state                           
# 	acpitemp                        ACPI temperature.                        
# 	adt746xcpu                      CPU temperature from therm_adt746x       
# 	adt746xfan                      Fan speed from therm_adt746x             
# 	alignr            (num)         Right-justify text, with space of N
# 	alignc                          Align text to centre
# 	battery           (num)         Remaining capasity in ACPI or APM        
# 					battery. ACPI battery number can be      
# 					given as argument (default is BAT0).     
# 	buffers                         Amount of memory buffered                
# 	cached                          Amount of memory cached                  
# 	color             (color)       Change drawing color to color            
# 	cpu                             CPU usage in percents                    
# 	cpubar            (height)      Bar that shows CPU usage, height is      
# 					bar's height in pixels                 
# 	cpugraph          (height),(width) (gradient colour 1) (gradient colour 2)
# 					CPU usage graph, with optional colours in hex,
# 					minus the #.
# 	downspeed         net           Download speed in kilobytes              
# 	downspeedf        net           Download speed in kilobytes with one     
# 					decimal                                  
# 	downspeedgraph    net (height),(width) (gradient colour 1) (gradient colour 2)
# 					Download speed graph, colours defined in
# 					hex, minus the #.
# 	exec              shell command Executes a shell command and displays    
# 					the output in conky. warning: this      
# 					takes a lot more resources than other    
# 					variables. I'd recommend coding wanted   
# 					behaviour in C and posting a patch :-).  
# 	execbar           shell command Same as exec, except if the first value
# 					return is a value between 0-100, it
# 					will use that number for a bar.
# 					The size for the bar is currently fixed,
# 					but that may change in the future.
# 	execgraph         shell command Same as execbar, but graphs values
# 	execi             interval, shell command
#  					Same as exec but with specific interval. 
# 					Interval can't be less than              
# 					update_interval in configuration.        
#	font		  font		Specify a different font.  Only applies
#					to one line.
# 	fs_bar            (height), (fs)Bar that shows how much space is used on 
# 					a file system. height is the height in   
# 					pixels. fs is any file on that file      
# 					system.                                  
# 	fs_free           (fs)          Free space on a file system available    
# 					for users.                               
# 	fs_free_perc      (fs)          Free percentage of space on a file       
# 					system available for users.              
# 	fs_size           (fs)          File system size                         
# 	fs_used           (fs)          File system used space                   
# 	hr                (height)      Horizontal line, height is the height in 
# 					pixels                                   
# 	i2c               (dev), type, n  I2C sensor from sysfs (Linux 2.6). dev   
# 					may be omitted if you have only one I2C  
# 					device. type is either in (or vol)       
# 					meaning voltage, fan meaning fan or
# 					temp/tempf (first in C, second in F)
# 					meaning temperature. n is number of the  
# 					sensor. See /sys/bus/i2c/devices/ on     
# 					your local computer.                     
# 	if_running        (process)     if PROCESS is running, display
# 					everything if_running and the matching $endif
# 	if_existing       (file)        if FILE exists, display everything between
# 					if_existing and the matching $endif
# 	if_mounted        (mountpoint)  if MOUNTPOINT is mounted, display everything between
# 					if_mounted and the matching $endif
# 	else                            Text to show if any of the above are not true
# 	kernel                          Kernel version                          
# 	linkstatus        (interface)   Get the link status for wireless connections
# 	loadavg           (1), (2), (3) System load average, 1 is for past 1     
# 					minute, 2 for past 5 minutes and 3 for   
# 					past 15 minutes.                         
# 	machine                         Machine, i686 for example                
# 	mails                           Mail count in mail spool. You can use    
# 					program like fetchmail to get mails from 
# 					some server using your favourite         
# 					protocol. See also new_mails.            
# 	mem                             Amount of memory in use                  
# 	membar            (height)      Bar that shows amount of memory in use   
# 	memmax                          Total amount of memory                   
# 	memperc                         Percentage of memory in use
# 	
# 	metar_ob_time
# 	metar_temp
# 	metar_tempf                     Temp in F
# 	metar_windchill
# 	metar_dew_point                 There are a bunch of these
# 	metar_rh                        and they are self-explanatory
# 	metar_windspeed
# 	metar_winddir
# 	metar_swinddir
# 	metar_cloud
# 	metar_u2d_time
# 	
# 	ml_upload_counter               total session upload in mb
# 	ml_download_counter             total session download in mb
# 	ml_nshared_files                number of shared files
# 	ml_shared_counter               total session shared in mb, buggy
# 					in some mldonkey versions
# 	ml_tcp_upload_rate              tcp upload rate in kb/s
# 	ml_tcp_download_rate            tcp download rate in kb/s
# 	ml_udp_upload_rate              udp upload rate in kb/s
# 	ml_udp_download_rate            udp download rate in kb/s
# 	ml_ndownloaded_files            number of completed files
# 	ml_ndownloading_files           number of downloading files
# 	
# 	mpd_artist			Artist in current MPD song
# 					(must be enabled at compile)
# 	mpd_album			Album in current MPD song
# 	mpd_bar           (height)      Bar of mpd's progress
# 	mpd_bitrate                     Bitrate of current song
# 	mpd_status                      Playing, stopped, et cetera.
# 	mpd_title			Title of current MPD song
# 	mpd_vol				MPD's volume
# 	mpd_elapsed                     Song's elapsed time
# 	mpd_length                      Song's length
# 	mpd_percent                     Percent of song's progress
# 	new_mails                       Unread mail count in mail spool.         
# 	nodename                        Hostname                                 
# 	outlinecolor      (color)       Change outline color                     
# 	pre_exec          shell command Executes a shell command one time before 
# 					conky displays anything and puts output 
# 					as text.                                 
# 	processes                       Total processes (sleeping and running)   
# 	running_processes               Running processes (not sleeping),        
# 					requires Linux 2.6                       
# 	shadecolor        (color)       Change shading color                     
# 	stippled_hr       (space),      Stippled (dashed) horizontal line        
# 			(height)        
# 	swapbar           (height)      Bar that shows amount of swap in use     
# 	swap                            Amount of swap in use                    
# 	swapmax                         Total amount of swap                     
# 	swapperc                        Percentage of swap in use                
# 	sysname                         System name, Linux for example           
# 	offset            pixels        Move text over by N pixels
# 	tail              logfile, lines (interval)
# 					Displays last N lines of supplied text
# 					text file.  If interval is not supplied,
# 					Conky assumes 2x Conky's interval.
# 					Max of 30 lines.
# 					Max of 30 lines can be displayed.
# 	time              (format)      Local time, see man strftime to get more 
# 					information about format                 
# 	totaldown         net           Total download, overflows at 4 GB on     
# 					Linux with 32-bit arch and there doesn't 
# 					seem to be a way to know how many times  
# 					it has already done that before conky   
# 					has started.                            
# 	top               type, num     This takes arguments in the form:
# 					top <name> <number>
# 					Basically, processes are ranked from 
# 					highest to lowest in terms of cpu
# 					usage, which is what <num> represents.
# 					The types are: "name", "pid", "cpu", and
# 					"mem".
# 					There can be a max of 10 processes listed.
# 	top_mem           type, num     Same as top, except sorted by mem usage
# 					instead of cpu
# 	totalup           net           Total upload, this one too, may overflow 
# 	updates                         Number of updates (for debugging)        
# 	upspeed           net           Upload speed in kilobytes                
# 	upspeedf          net           Upload speed in kilobytes with one       
# 					decimal                                  
# 	upspeedgraph      net (height),(width)  (gradient colour 1) (gradient colour 2)
# 					Upload speed graph, colours defined in
# 					hex, minus the #.
# 	uptime                          Uptime                                   
# 	uptime_short                    Uptime in a shorter format               
# 	
# 	seti_prog                       Seti@home current progress
# 	seti_progbar      (height)      Seti@home current progress bar
# 	seti_credit                     Seti@hoome total user credit


# variable is given either in format $variable or in ${variable}. Latter
# allows characters right after the variable and must be used in network
# stuff because of an argument

# stuff after 'TEXT' will be formatted on screen
	
TEXT
      ${time %a, } ${color }${time %e %B %G} ${time %Z,    }${color }${time %H:%M:%S}|${machine} ${sysname} kernel ${kernel}|CPU:${color}${cpu}% ${cpugraph cpu0 12,75} ${color} @${freq cpu0} Mhz|MEM: ${color}${mem} ${color}|${color} UP: ${color}${uptime}${color}|${color} NET:${color} ${downspeedgraph ath0 12,75} ${downspeed ath0} Kb/s ${color} ${totaldown ath0}down${upspeedgraph ath0 12,75} ${upspeed ath0} Kb/s ${color} ${totalup ath0}${color}up|Swap:${swap}|Root: ${color}${fs_free /} ${color}|Home: ${color }${font}${fs_free /home} ${color}|Media: ${color }${font}${fs_free /media/disk} ${color}|Top Prc ${color}${top name 1}
```

Good luck!
-nkri

---

### Post by SkonesMickLoud on 2008-07-08
This thread is quickly turning into this one:

[http://ubuntuforums.org/showthread.php?t=281865](http://ubuntuforums.org/showthread.php?t=281865)

We don't need 2 threads, do we?

---

### Post by kaivalagi on 2008-07-08
> **SkonesMickLoud said:**
> This thread is quickly turning into this one:

[http://ubuntuforums.org/showthread.php?t=281865](http://ubuntuforums.org/showthread.php?t=281865)

We don't need 2 threads, do we?

+1

I totally agree, anything and everything about conky can be found there

---

### Post by tjwoosta on 2008-07-08
> 

I totally agree, anything and everything about conky can be found there

except for the answer to my question (the reason i started this thread)

how can i make 4 seperate conky's open at login with each automatically assigned to its own desktop

see attached thubnails and read  my first post for more info

---

### Post by kaivalagi on 2008-07-08
> **tjwoosta said:**
> except for the answer to my question (the reason i started this thread)

how can i make 4 seperate conky's open at login with each automatically assigned to its own desktop

see attached thubnails and read  my first post for more info

I'll rephrase, "almost anything and everything" :)

Sounds like you've already been through the thread reading what people have figured out.

It would still make sense to post your question into that thread, where a lot of people who know conky well are subscribed. More chance of getting answers to your questions.

Did you see my post on suggestions for what you're after, it's a start...

Also, what desktop manager are you running? That, I am certain, will be the determining factor.

Hope that helps

---

### Post by tad1073 on 2008-07-08
> **easybake said:**
> Put this anywhere above TEXT ```
window_type override
```

> **nkri said:**
> You have to either disable double buffer (may flicker depending on your system) or give conky its own window (uglier, but works without a doubt).

Window:
```
# conky configuration
# edited by darcon@gmail.com

# set to yes if you want Conky to be forked in the background
background yes

# X font when Xft is disabled, you can pick one with program xfontsel
#font 5x7
#font 6x10
#font 7x13
#font 8x13
#font 9x15
#font *mintsmild.se*
#font -*-*-*-*-*-*-34-*-*-*-*-*-*-*


# Use Xft?
use_xft yes

# Xft font when Xft is enabled
#xftfont Bitstream Vera Sans Mono:size=8
xftfont Veranda:size=8

# Text alpha when using Xft
xftalpha 0.8

# Print everything to console?
# out_to_console no

# mail spool
#mail_spool $MAIL

# Update interval in seconds
update_interval 0.5

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window yes

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 1680 12

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Stippled borders?
stippled_borders 8

# border margins
border_margin 4

# border width
border_width 1

# Default colors and also border colors
default_color white
default_shade_color black
default_outline_color white

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 0
gap_y 5

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# number of cpu samples to average
# set to 1 to disable averaging
cpu_avg_samples 2

# number of net samples to average
# set to 1 to disable averaging
net_avg_samples 2

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale no
draw_graph_borders no

# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer right
#Note: doesn't work in conky 1.2 =(

#   mldonkey_hostname     Hostname for mldonkey stuff, defaults to localhost
#   mldonkey_port         Mldonkey port, 4001 default
#   mldonkey_login        Mldonkey login, default none
#   mldonkey_password     Mldonkey password, default none


# Possible variables to be used:
#
#      Variable         Arguments                  Description                

# 	addr              (interface)   IP address for an interface
# 	acpiacadapter                   ACPI ac adapter state.                   
# 	acpifan                         ACPI fan state                           
# 	acpitemp                        ACPI temperature.                        
# 	adt746xcpu                      CPU temperature from therm_adt746x       
# 	adt746xfan                      Fan speed from therm_adt746x             
# 	alignr            (num)         Right-justify text, with space of N
# 	alignc                          Align text to centre
# 	battery           (num)         Remaining capasity in ACPI or APM        
# 					battery. ACPI battery number can be      
# 					given as argument (default is BAT0).     
# 	buffers                         Amount of memory buffered                
# 	cached                          Amount of memory cached                  
# 	color             (color)       Change drawing color to color            
# 	cpu                             CPU usage in percents                    
# 	cpubar            (height)      Bar that shows CPU usage, height is      
# 					bar's height in pixels                 
# 	cpugraph          (height),(width) (gradient colour 1) (gradient colour 2)
# 					CPU usage graph, with optional colours in hex,
# 					minus the #.
# 	downspeed         net           Download speed in kilobytes              
# 	downspeedf        net           Download speed in kilobytes with one     
# 					decimal                                  
# 	downspeedgraph    net (height),(width) (gradient colour 1) (gradient colour 2)
# 					Download speed graph, colours defined in
# 					hex, minus the #.
# 	exec              shell command Executes a shell command and displays    
# 					the output in conky. warning: this      
# 					takes a lot more resources than other    
# 					variables. I'd recommend coding wanted   
# 					behaviour in C and posting a patch :-).  
# 	execbar           shell command Same as exec, except if the first value
# 					return is a value between 0-100, it
# 					will use that number for a bar.
# 					The size for the bar is currently fixed,
# 					but that may change in the future.
# 	execgraph         shell command Same as execbar, but graphs values
# 	execi             interval, shell command
#  					Same as exec but with specific interval. 
# 					Interval can't be less than              
# 					update_interval in configuration.        
#	font		  font		Specify a different font.  Only applies
#					to one line.
# 	fs_bar            (height), (fs)Bar that shows how much space is used on 
# 					a file system. height is the height in   
# 					pixels. fs is any file on that file      
# 					system.                                  
# 	fs_free           (fs)          Free space on a file system available    
# 					for users.                               
# 	fs_free_perc      (fs)          Free percentage of space on a file       
# 					system available for users.              
# 	fs_size           (fs)          File system size                         
# 	fs_used           (fs)          File system used space                   
# 	hr                (height)      Horizontal line, height is the height in 
# 					pixels                                   
# 	i2c               (dev), type, n  I2C sensor from sysfs (Linux 2.6). dev   
# 					may be omitted if you have only one I2C  
# 					device. type is either in (or vol)       
# 					meaning voltage, fan meaning fan or
# 					temp/tempf (first in C, second in F)
# 					meaning temperature. n is number of the  
# 					sensor. See /sys/bus/i2c/devices/ on     
# 					your local computer.                     
# 	if_running        (process)     if PROCESS is running, display
# 					everything if_running and the matching $endif
# 	if_existing       (file)        if FILE exists, display everything between
# 					if_existing and the matching $endif
# 	if_mounted        (mountpoint)  if MOUNTPOINT is mounted, display everything between
# 					if_mounted and the matching $endif
# 	else                            Text to show if any of the above are not true
# 	kernel                          Kernel version                          
# 	linkstatus        (interface)   Get the link status for wireless connections
# 	loadavg           (1), (2), (3) System load average, 1 is for past 1     
# 					minute, 2 for past 5 minutes and 3 for   
# 					past 15 minutes.                         
# 	machine                         Machine, i686 for example                
# 	mails                           Mail count in mail spool. You can use    
# 					program like fetchmail to get mails from 
# 					some server using your favourite         
# 					protocol. See also new_mails.            
# 	mem                             Amount of memory in use                  
# 	membar            (height)      Bar that shows amount of memory in use   
# 	memmax                          Total amount of memory                   
# 	memperc                         Percentage of memory in use
# 	
# 	metar_ob_time
# 	metar_temp
# 	metar_tempf                     Temp in F
# 	metar_windchill
# 	metar_dew_point                 There are a bunch of these
# 	metar_rh                        and they are self-explanatory
# 	metar_windspeed
# 	metar_winddir
# 	metar_swinddir
# 	metar_cloud
# 	metar_u2d_time
# 	
# 	ml_upload_counter               total session upload in mb
# 	ml_download_counter             total session download in mb
# 	ml_nshared_files                number of shared files
# 	ml_shared_counter               total session shared in mb, buggy
# 					in some mldonkey versions
# 	ml_tcp_upload_rate              tcp upload rate in kb/s
# 	ml_tcp_download_rate            tcp download rate in kb/s
# 	ml_udp_upload_rate              udp upload rate in kb/s
# 	ml_udp_download_rate            udp download rate in kb/s
# 	ml_ndownloaded_files            number of completed files
# 	ml_ndownloading_files           number of downloading files
# 	
# 	mpd_artist			Artist in current MPD song
# 					(must be enabled at compile)
# 	mpd_album			Album in current MPD song
# 	mpd_bar           (height)      Bar of mpd's progress
# 	mpd_bitrate                     Bitrate of current song
# 	mpd_status                      Playing, stopped, et cetera.
# 	mpd_title			Title of current MPD song
# 	mpd_vol				MPD's volume
# 	mpd_elapsed                     Song's elapsed time
# 	mpd_length                      Song's length
# 	mpd_percent                     Percent of song's progress
# 	new_mails                       Unread mail count in mail spool.         
# 	nodename                        Hostname                                 
# 	outlinecolor      (color)       Change outline color                     
# 	pre_exec          shell command Executes a shell command one time before 
# 					conky displays anything and puts output 
# 					as text.                                 
# 	processes                       Total processes (sleeping and running)   
# 	running_processes               Running processes (not sleeping),        
# 					requires Linux 2.6                       
# 	shadecolor        (color)       Change shading color                     
# 	stippled_hr       (space),      Stippled (dashed) horizontal line        
# 			(height)        
# 	swapbar           (height)      Bar that shows amount of swap in use     
# 	swap                            Amount of swap in use                    
# 	swapmax                         Total amount of swap                     
# 	swapperc                        Percentage of swap in use                
# 	sysname                         System name, Linux for example           
# 	offset            pixels        Move text over by N pixels
# 	tail              logfile, lines (interval)
# 					Displays last N lines of supplied text
# 					text file.  If interval is not supplied,
# 					Conky assumes 2x Conky's interval.
# 					Max of 30 lines.
# 					Max of 30 lines can be displayed.
# 	time              (format)      Local time, see man strftime to get more 
# 					information about format                 
# 	totaldown         net           Total download, overflows at 4 GB on     
# 					Linux with 32-bit arch and there doesn't 
# 					seem to be a way to know how many times  
# 					it has already done that before conky   
# 					has started.                            
# 	top               type, num     This takes arguments in the form:
# 					top <name> <number>
# 					Basically, processes are ranked from 
# 					highest to lowest in terms of cpu
# 					usage, which is what <num> represents.
# 					The types are: "name", "pid", "cpu", and
# 					"mem".
# 					There can be a max of 10 processes listed.
# 	top_mem           type, num     Same as top, except sorted by mem usage
# 					instead of cpu
# 	totalup           net           Total upload, this one too, may overflow 
# 	updates                         Number of updates (for debugging)        
# 	upspeed           net           Upload speed in kilobytes                
# 	upspeedf          net           Upload speed in kilobytes with one       
# 					decimal                                  
# 	upspeedgraph      net (height),(width)  (gradient colour 1) (gradient colour 2)
# 					Upload speed graph, colours defined in
# 					hex, minus the #.
# 	uptime                          Uptime                                   
# 	uptime_short                    Uptime in a shorter format               
# 	
# 	seti_prog                       Seti@home current progress
# 	seti_progbar      (height)      Seti@home current progress bar
# 	seti_credit                     Seti@hoome total user credit


# variable is given either in format $variable or in ${variable}. Latter
# allows characters right after the variable and must be used in network
# stuff because of an argument

# stuff after 'TEXT' will be formatted on screen
	
TEXT
      ${time %a, } ${color }${time %e %B %G} ${time %Z,    }${color }${time %H:%M:%S}|${machine} ${sysname} kernel ${kernel}|CPU:${color}${cpu}% ${cpugraph cpu0 12,75} ${color} @${freq cpu0} Mhz|MEM: ${color}${mem} ${color}|${color} UP: ${color}${uptime}${color}|${color} NET:${color} ${downspeedgraph ath0 12,75} ${downspeed ath0} Kb/s ${color} ${totaldown ath0}down${upspeedgraph ath0 12,75} ${upspeed ath0} Kb/s ${color} ${totalup ath0}${color}up|Swap:${swap}|Root: ${color}${fs_free /} ${color}|Home: ${color }${font}${fs_free /home} ${color}|Media: ${color }${font}${fs_free /media/disk} ${color}|Top Prc ${color}${top name 1}
```

Buffer:
```
# conky configuration
# edited by darcon@gmail.com

# set to yes if you want Conky to be forked in the background
background yes

# X font when Xft is disabled, you can pick one with program xfontsel
#font 5x7
#font 6x10
#font 7x13
#font 8x13
#font 9x15
#font *mintsmild.se*
#font -*-*-*-*-*-*-34-*-*-*-*-*-*-*


# Use Xft?
use_xft yes

# Xft font when Xft is enabled
#xftfont Bitstream Vera Sans Mono:size=8
xftfont Veranda:size=8

# Text alpha when using Xft
xftalpha 0.8

# Print everything to console?
# out_to_console no

# mail spool
#mail_spool $MAIL

# Update interval in seconds
update_interval 0.5

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window no

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer no

# Minimum size of text area
minimum_size 1680 12

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Stippled borders?
stippled_borders 8

# border margins
border_margin 4

# border width
border_width 1

# Default colors and also border colors
default_color white
default_shade_color black
default_outline_color white

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 0
gap_y 5

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# number of cpu samples to average
# set to 1 to disable averaging
cpu_avg_samples 2

# number of net samples to average
# set to 1 to disable averaging
net_avg_samples 2

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale no
draw_graph_borders no

# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer right
#Note: doesn't work in conky 1.2 =(

#   mldonkey_hostname     Hostname for mldonkey stuff, defaults to localhost
#   mldonkey_port         Mldonkey port, 4001 default
#   mldonkey_login        Mldonkey login, default none
#   mldonkey_password     Mldonkey password, default none


# Possible variables to be used:
#
#      Variable         Arguments                  Description                

# 	addr              (interface)   IP address for an interface
# 	acpiacadapter                   ACPI ac adapter state.                   
# 	acpifan                         ACPI fan state                           
# 	acpitemp                        ACPI temperature.                        
# 	adt746xcpu                      CPU temperature from therm_adt746x       
# 	adt746xfan                      Fan speed from therm_adt746x             
# 	alignr            (num)         Right-justify text, with space of N
# 	alignc                          Align text to centre
# 	battery           (num)         Remaining capasity in ACPI or APM        
# 					battery. ACPI battery number can be      
# 					given as argument (default is BAT0).     
# 	buffers                         Amount of memory buffered                
# 	cached                          Amount of memory cached                  
# 	color             (color)       Change drawing color to color            
# 	cpu                             CPU usage in percents                    
# 	cpubar            (height)      Bar that shows CPU usage, height is      
# 					bar's height in pixels                 
# 	cpugraph          (height),(width) (gradient colour 1) (gradient colour 2)
# 					CPU usage graph, with optional colours in hex,
# 					minus the #.
# 	downspeed         net           Download speed in kilobytes              
# 	downspeedf        net           Download speed in kilobytes with one     
# 					decimal                                  
# 	downspeedgraph    net (height),(width) (gradient colour 1) (gradient colour 2)
# 					Download speed graph, colours defined in
# 					hex, minus the #.
# 	exec              shell command Executes a shell command and displays    
# 					the output in conky. warning: this      
# 					takes a lot more resources than other    
# 					variables. I'd recommend coding wanted   
# 					behaviour in C and posting a patch :-).  
# 	execbar           shell command Same as exec, except if the first value
# 					return is a value between 0-100, it
# 					will use that number for a bar.
# 					The size for the bar is currently fixed,
# 					but that may change in the future.
# 	execgraph         shell command Same as execbar, but graphs values
# 	execi             interval, shell command
#  					Same as exec but with specific interval. 
# 					Interval can't be less than              
# 					update_interval in configuration.        
#	font		  font		Specify a different font.  Only applies
#					to one line.
# 	fs_bar            (height), (fs)Bar that shows how much space is used on 
# 					a file system. height is the height in   
# 					pixels. fs is any file on that file      
# 					system.                                  
# 	fs_free           (fs)          Free space on a file system available    
# 					for users.                               
# 	fs_free_perc      (fs)          Free percentage of space on a file       
# 					system available for users.              
# 	fs_size           (fs)          File system size                         
# 	fs_used           (fs)          File system used space                   
# 	hr                (height)      Horizontal line, height is the height in 
# 					pixels                                   
# 	i2c               (dev), type, n  I2C sensor from sysfs (Linux 2.6). dev   
# 					may be omitted if you have only one I2C  
# 					device. type is either in (or vol)       
# 					meaning voltage, fan meaning fan or
# 					temp/tempf (first in C, second in F)
# 					meaning temperature. n is number of the  
# 					sensor. See /sys/bus/i2c/devices/ on     
# 					your local computer.                     
# 	if_running        (process)     if PROCESS is running, display
# 					everything if_running and the matching $endif
# 	if_existing       (file)        if FILE exists, display everything between
# 					if_existing and the matching $endif
# 	if_mounted        (mountpoint)  if MOUNTPOINT is mounted, display everything between
# 					if_mounted and the matching $endif
# 	else                            Text to show if any of the above are not true
# 	kernel                          Kernel version                          
# 	linkstatus        (interface)   Get the link status for wireless connections
# 	loadavg           (1), (2), (3) System load average, 1 is for past 1     
# 					minute, 2 for past 5 minutes and 3 for   
# 					past 15 minutes.                         
# 	machine                         Machine, i686 for example                
# 	mails                           Mail count in mail spool. You can use    
# 					program like fetchmail to get mails from 
# 					some server using your favourite         
# 					protocol. See also new_mails.            
# 	mem                             Amount of memory in use                  
# 	membar            (height)      Bar that shows amount of memory in use   
# 	memmax                          Total amount of memory                   
# 	memperc                         Percentage of memory in use
# 	
# 	metar_ob_time
# 	metar_temp
# 	metar_tempf                     Temp in F
# 	metar_windchill
# 	metar_dew_point                 There are a bunch of these
# 	metar_rh                        and they are self-explanatory
# 	metar_windspeed
# 	metar_winddir
# 	metar_swinddir
# 	metar_cloud
# 	metar_u2d_time
# 	
# 	ml_upload_counter               total session upload in mb
# 	ml_download_counter             total session download in mb
# 	ml_nshared_files                number of shared files
# 	ml_shared_counter               total session shared in mb, buggy
# 					in some mldonkey versions
# 	ml_tcp_upload_rate              tcp upload rate in kb/s
# 	ml_tcp_download_rate            tcp download rate in kb/s
# 	ml_udp_upload_rate              udp upload rate in kb/s
# 	ml_udp_download_rate            udp download rate in kb/s
# 	ml_ndownloaded_files            number of completed files
# 	ml_ndownloading_files           number of downloading files
# 	
# 	mpd_artist			Artist in current MPD song
# 					(must be enabled at compile)
# 	mpd_album			Album in current MPD song
# 	mpd_bar           (height)      Bar of mpd's progress
# 	mpd_bitrate                     Bitrate of current song
# 	mpd_status                      Playing, stopped, et cetera.
# 	mpd_title			Title of current MPD song
# 	mpd_vol				MPD's volume
# 	mpd_elapsed                     Song's elapsed time
# 	mpd_length                      Song's length
# 	mpd_percent                     Percent of song's progress
# 	new_mails                       Unread mail count in mail spool.         
# 	nodename                        Hostname                                 
# 	outlinecolor      (color)       Change outline color                     
# 	pre_exec          shell command Executes a shell command one time before 
# 					conky displays anything and puts output 
# 					as text.                                 
# 	processes                       Total processes (sleeping and running)   
# 	running_processes               Running processes (not sleeping),        
# 					requires Linux 2.6                       
# 	shadecolor        (color)       Change shading color                     
# 	stippled_hr       (space),      Stippled (dashed) horizontal line        
# 			(height)        
# 	swapbar           (height)      Bar that shows amount of swap in use     
# 	swap                            Amount of swap in use                    
# 	swapmax                         Total amount of swap                     
# 	swapperc                        Percentage of swap in use                
# 	sysname                         System name, Linux for example           
# 	offset            pixels        Move text over by N pixels
# 	tail              logfile, lines (interval)
# 					Displays last N lines of supplied text
# 					text file.  If interval is not supplied,
# 					Conky assumes 2x Conky's interval.
# 					Max of 30 lines.
# 					Max of 30 lines can be displayed.
# 	time              (format)      Local time, see man strftime to get more 
# 					information about format                 
# 	totaldown         net           Total download, overflows at 4 GB on     
# 					Linux with 32-bit arch and there doesn't 
# 					seem to be a way to know how many times  
# 					it has already done that before conky   
# 					has started.                            
# 	top               type, num     This takes arguments in the form:
# 					top <name> <number>
# 					Basically, processes are ranked from 
# 					highest to lowest in terms of cpu
# 					usage, which is what <num> represents.
# 					The types are: "name", "pid", "cpu", and
# 					"mem".
# 					There can be a max of 10 processes listed.
# 	top_mem           type, num     Same as top, except sorted by mem usage
# 					instead of cpu
# 	totalup           net           Total upload, this one too, may overflow 
# 	updates                         Number of updates (for debugging)        
# 	upspeed           net           Upload speed in kilobytes                
# 	upspeedf          net           Upload speed in kilobytes with one       
# 					decimal                                  
# 	upspeedgraph      net (height),(width)  (gradient colour 1) (gradient colour 2)
# 					Upload speed graph, colours defined in
# 					hex, minus the #.
# 	uptime                          Uptime                                   
# 	uptime_short                    Uptime in a shorter format               
# 	
# 	seti_prog                       Seti@home current progress
# 	seti_progbar      (height)      Seti@home current progress bar
# 	seti_credit                     Seti@hoome total user credit


# variable is given either in format $variable or in ${variable}. Latter
# allows characters right after the variable and must be used in network
# stuff because of an argument

# stuff after 'TEXT' will be formatted on screen
	
TEXT
      ${time %a, } ${color }${time %e %B %G} ${time %Z,    }${color }${time %H:%M:%S}|${machine} ${sysname} kernel ${kernel}|CPU:${color}${cpu}% ${cpugraph cpu0 12,75} ${color} @${freq cpu0} Mhz|MEM: ${color}${mem} ${color}|${color} UP: ${color}${uptime}${color}|${color} NET:${color} ${downspeedgraph ath0 12,75} ${downspeed ath0} Kb/s ${color} ${totaldown ath0}down${upspeedgraph ath0 12,75} ${upspeed ath0} Kb/s ${color} ${totalup ath0}${color}up|Swap:${swap}|Root: ${color}${fs_free /} ${color}|Home: ${color }${font}${fs_free /home} ${color}|Media: ${color }${font}${fs_free /media/disk} ${color}|Top Prc ${color}${top name 1}
```

Good luck!
-nkri

This fixed my problem, thanks for the help.

```
# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_hints undecorated,below,skip_taskbar
own_window_type override

# Use pseudo transparency with own_window?
own_window_transparent yes
```

---

