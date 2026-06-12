---
title: "Help with a conky file"
date: 2013-04-22
forum: General Help
---

### Post by breezypt on 2013-04-22
I did what was recomended on the wiki page and took a conky file and edited it to some of my specs. I cant seem to get my core temps of my CPU or GPU. I did a sensor detect and my sensors in my modules file are coretemp and it87.
Also is there a manual for terminology I've been googling around and cant seem to find one.

Thanks for any suggestions:
# Conky sample configuration
#
# the list of variables has been removed from this file in favour
# of keeping the documentation more maintainable.
# Check [http://conky.sf.net](http://conky.sf.net) for an up-to-date-list.

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

# Set conky on the bottom of all other applications
own_window_hints below

# Xft font when Xft is enabled
xftfont Sans:style=Bold:size=10

# Text alpha when using Xft
xftalpha 1

# Print everything to stdout?
# out_to_console no

# MPD host/port
# mpd_host localhost
# mpd_port 6600
# mpd_password tinker_bell

# Print everything to console?
# out_to_console no

# mail spool
#mail_spool $MAIL

# Update interval in seconds
update_interval 5

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_hints undecorated,below,skip_taskbar
own_window_type override

# Use pseudo transparency with own_window?
own_window_transparent yes

# If own_window_transparent is set to no, you can set the background colour here
#own_window_colour hotpink

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 280 5

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Stippled borders?
stippled_borders 8

# border margins
border_margin 5

# border width
border_width 10

# Default colors and also border colors
default_color white
default_shade_color black
default_outline_color black

# Text alignment, other possible values are commented
#alignment top_left
#alignment top_right
#alignment bottom_left
alignment bottom_right
#alignment none

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 50
gap_y 12

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# number of cpu samples to average
# set to 1 to disable averaging
cpu_avg_samples 1

# number of net samples to average
# set to 1 to disable averaging
net_avg_samples 1

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale no


# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer yes

#   mldonkey_hostname     Hostname for mldonkey stuff, defaults to localhost
#   mldonkey_port         Mldonkey port, 4001 default
#   mldonkey_login        Mldonkey login, default none
#   mldonkey_password     Mldonkey password, default none

# boinc (seti) dir
# seti_dir /opt/seti

# Allow for the creation of at least this number of port monitors (if 0 or not set, default is 16) 
min_port_monitors 16

# Allow each port monitor to track at least this many connections (if 0 or not set, default is 256)
min_port_monitor_connections 256

# variable is given either in format $variable or in ${variable}. Latter
# allows characters right after the variable and must be used in network
# stuff because of an argument

# stuff after 'TEXT' will be formatted on screen

TEXT
 ${color white}           ${time %l:%M %a %b %d}
${color white}CPU:${color white} ${freq} ${color white}mhz / Temp:${color white} ${color white}C 
${color white}Disk I/O:${color white} ${diskio}    ${color white}Uptime:${color white} $uptime 
${color white}Processes:${color white} $processes  ${color white}Running:${color white} $running_processes
${color white}CPU Usage:${color white} $cpu% ${color white}${cpugraph  20, 125 ffffff 0000ff}

${color white}RAM Usage:${color white} $mem of $memmax ${color white}- ${color white}$memperc% 
${color white}Swap Usage:${color white} $swap of $swapmax ${color white}- ${color white}$swapperc% 
${color white}File systems: ${color white}${fs_used /} of ${fs_size /}

${color white}Name                     PID     CPU%   MEM%
${color white} ${top name 1}         ${top pid 1} ${top cpu 1} ${top mem 1}
${color white} ${top name 2}         ${top pid 2} ${top cpu 2} ${top mem 2}
${color white} ${top name 3}         ${top pid 3} ${top cpu 3} ${top mem 3}
${color white} ${top name 4}         ${top pid 4} ${top cpu 4} ${top mem 4}
${color white} ${top name 5}         ${top pid 5} ${top cpu 5} ${top mem 5}

${color white}IN:${downspeed eth1} k/s ${color white}${downspeedgraph eth1 20,125 ff0000 0000ff}
${color white}OUT:${upspeed eth1} k/s ${color white}${upspeedgraph eth1 20,125 0000ff ff0000}
${color white}Connections: ${tcp_portmon 1 65535 count}
${color white}Netstat 
${color white}${execi 2 netstat -e -p -t | grep ESTABLISHED | cut -c45-68,80-86,102-140}

I figured out how to change the eth numbers I have 2 eth ports on my board so I got that working. I would like to get a graph of the 4 cores of my CPU, I had the graph of my 4 cores working in a file, before my OS crashed last week but lost the file and cant remember the terminology. I know I start out with core 0, then core1,2,3, just can't remember the rest.... along with core temps and GPU temp.

Thanks for any suggestions...

John

---

### Post by deadflowr on 2013-04-23
> [COLOR=#000000]Also is there a manual for terminology I've been googling around and cant seem to find one.[/COLOR]

Do you mean for conky?
If so this is helpful

[http://linux.die.net/man/1/conky](http://linux.die.net/man/1/conky)

---

### Post by s.fox on 2013-04-23
This thread would be better supported in a support area of the forum :)  

Moved.

---

### Post by breezypt on 2013-04-23
I found a lot of conky questions in this part of the forum which is why I posted it here.. Can you please tell me where you moved it to? Because now it is probably lost and I will get no repsonse how is anyone supposed to find it if you didn't say where it was moved to? :)

---

### Post by s.fox on 2013-04-23
> **breezypt said:**
> I found a lot of conky questions in this part of the forum which is why I posted it here.. Can you please tell me where you moved it to? Because now it is probably lost and I will get no repsonse how is anyone supposed to find it if you didn't say where it was moved to? :)

You have found it, you have posted in it since I moved it.  The thread link is: [http://ubuntuforums.org/showthread.php?t=2138087](http://ubuntuforums.org/showthread.php?t=2138087)

It is in the [General Help]("http://ubuntuforums.org/forumdisplay.php?f=331") area of the forum.

---

### Post by deadflowr on 2013-04-23
For your sensors you could try
```
sensors | grep "Core1" | awk '{print $2}'
```

with the $2 being the section in the line with the temperature.
Good practice with this one is to test/try it in a terminal.

---

### Post by breezypt on 2013-04-24
I found it sfox :). Thanks.

I can't decide weather to keep making changes to the one I have at the moment or to start a blank one from scratch. Any way I'm going to try your suggestion deadflower. Thanks. And yes deadflower I do everything in the terminal, I find it much easier, and better for me to learn linux the right way., is there a command to refresh conky while I'm doing changes. I've been killing the process number then doing a 'conky &' in another terminal window, was wondering if there was a quicker way to refresh the changes made...

I figured out another thing today to get the widow to stay behind all others. The previous one was staying on top so I got that fixed. I really love this app and the endless possibliities it can do...

---

### Post by deadflowr on 2013-04-24
I like looking at this one.

[http://ubuntuforums.org/showthread.php?t=1771033](http://ubuntuforums.org/showthread.php?t=1771033)

Aside from VinDSL's conky, the pointers on what does how and how to do what are straight forward and quite helpful.

---

### Post by breezypt on 2013-04-25
I managed to get all 4 core cars to show up. The problem was it wasn't registering correctly, all the bars were loading and unloading identically. Which is not how my CPU works. When I was running menu bars in Mac OSX it showed how the cpu actually deals with the cores. It will take information load into one core, then unload it to another core, and so forth and so on. Each bar was never full or empty at the same time representing each core. So I must be missing a variable or something I have to study up on. So for now I just changed it to one cpu bar for all the cores (for the time being).

I'm having another problem getting my CPU temp. I ran probes select and have coretemp and it87 in my /etc/modprobe file. So my sensors are set up for lm-sensors

My whole reasoning for wanting separate core bars is to make sure one core is not being over worked and that the cpu is functioning properly. I can't even get a temp reading as of now on the cores, without going into my BIOS, which doesn't give the true reading, because running the OS always brings up the temps anyway.

I'll check out VinDSL's file . If I don't have to add it to my repositories. I am very careful as to what repos' I add. As of now Launchpad is the only one.

---

### Post by breezypt on 2013-04-25
I got my correct cpu temp, my nvidia card temp and memory speed correct. I still can't get my name of my cpu, the MHz, and a separate bar for each core as they are loading. For those who may have just jumped on this thread the CPU starts at cpu0, then cpu1, cpu2, cpu3, I need the temp of each core... What am I missing here?

The CPU is an Intel  Core2Quad Q8400 2.66 GHz.

Anyone,

Thanks for any help....

John

PS Hers a pic of what I got so far:
[IMG]http://img839.imageshack.us/img839/7448/conkyscreenshot.png[/IMG]

---

### Post by breezypt on 2013-04-25
I was able to get somewhat further by getting my 4 core bars to show up and to show the proper percentage of info going through each one in real time , I got the ambient temp of 1 & 2 as I'll show in a screen shot but I can't seem to get each cores temp. Which I used to be able to get from this motherboard in Mac OS, so it can be done. I'm doing something wrong. I'm also going to post the code I put in to get the 4 corse and the correct percentages and the temps from 1 & 2 as you will be able to read form the code. 

I also will include a screen shot of my sensors from the command line. If someone can tell me the correct terminology to use to get each cores temperature I will be finished for what I am looking for.

thanks for looking,

John

Here is the conky file now:[IMG]http://img833.imageshack.us/img833/7647/conky2.png[/IMG]

And Here is my sensors putout form the commandline:[IMG]http://img835.imageshack.us/img835/7558/sensorsn.png[/IMG]

Thanks for any help!

Sorry I for got to post the code I used, Here it is:

 ${color #f80b0b}Temp 1:${execpi 5 sensors | grep temp1 | awk '{print $2}' | cut -c2-3}        
        ${color #f80b0b}Temp 2:${execpi 5 sensors | grep temp2 | awk '{print $2}' | cut -c2-3}
        ${color #f80b0b}CPU 0 ${offset 9}$color${cpu cpu0}%  ${color #f80b0b}${cpubar 5,140} ${execpi 5 sensors | grep Core 0 | awk '{print $2}' | cut -c2-3} 
        ${color #f80b0b}CPU 1 ${offset 9}$color${cpu cpu1}%  ${color #f80b0b}${cpubar 5,140} ${execpi 5 sensors | grep Core 1 | awk '{print $2}' | cut -c2-3} 
        ${color #f80b0b}CPU 2 ${offset 9}$color${cpu cpu0}%  ${color #f80b0b}${cpubar 5,140} ${execpi 5 sensors | grep Core 2 | awk '{print $2}' | cut -c2-3} 
        ${color #f80b0b}CPU 3 ${offset 9}$color${cpu cpu1}%  ${color #f80b0b}${cpubar 5,140} ${execpi 5 sensors | grep Core 3 | awk '{print $2}' | cut -c2-3}

---

### Post by deadflowr on 2013-04-25
Try putting the grep Core 0,1,2,3 with quotes around the Core like "Core 0".
 grep "Core 0"

Another tidbit about sensors, if you add -f to the sensors command, you'll get the Fahrenheit reading
 sensors -f.
No clue on how to get them on the nvidia temps though.

I also debate myself on whether sensors is the best temp gauge, or if a better one exists.

---

### Post by breezypt on 2013-04-25
Thanks I'll try that. I'm already used to the Celcius, so not too worried about that.

Deadflowr it was worth a try but didn't work. Any other ideas? :)

I'm positive that a core reading is given for each one..smh.. a delema...:)

---

