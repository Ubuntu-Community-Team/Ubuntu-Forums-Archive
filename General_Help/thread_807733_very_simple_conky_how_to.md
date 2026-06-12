---
title: "very simple conky how to"
date: 2008-05-26
forum: General Help
---

### Post by chrismitt2002 on 2008-05-26
#Conky Howto 

#this howto assumes your in the /home/ folder of the account your working with e.g.

/home/owner/


#from this point on - lines that do not have a # infront of them are commands for terminal
#unless stated otherwise..


#install conky like so via terminal

sudo apt-get install conky

#Now run conky just once so it creates a .conkyrc config file like so...
#in terminal type 

conky

#let it load then hit ctrl + C

#to edit the conkyrc config file open terminal and type

sudo gedit .conkyrc

#these commands in are for enter in the config file for conky
#it should open witht he config file...
#Now to make sure u can see your icons u need to make sure this is in the config

own_window yes
own_window_transparent yes
own_window_override yes

#... now - to add a core from a DUO CORE add the following in the BOTTEM of
#the config file where required (sure you'll figure out where u want it)

${cpu cpu0}         <---CORE 1 / is to show percentage of CORE 1 in use
${cpu cpu1}         <---CORE 2 / As above but for CORE 2 
${cpu cpu2}	    <---CORE 3 / Use this if u have quad-core / for CORE 3(not sure if its supported yet)
${cpu cpu3}	    <---CORE 4 / As mentioned above... this would be for CORE 4
#as for changing color - look at the current config  and im sure u can figure that one out..

#how to make conky work on startup....

#open terminal and type the following....

sudo gedit .conky_startup.sh

#one it opens enter the following
#below u MUST ENTER IT AS IT APPEARS HERE INCLUDING THE #


#!/bin/bash
sleep 10 && conky


#save and exit it.. now in terminal we need to change the permissions of that file
#we just ceated.. so type..

sudo chmod 755 .conky_startup.sh 

#now that's done.... goto menu - system - prefrences - session - --/ add - give it a name of 
#conky,   then point it to that file - u probley wont be able to see that file in your
#home folder so hit "ctrl + h" to show hidden files... and point it to .conky_startup.sh
#save - and logout and log back in.. your done...










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
own_window_hints undecorated,below,skip_taskbar
background yes

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer yes
use_xft yes

# Update interval in seconds
update_interval 3.0

# Minimum size of text area
minimum_size 400 5

# Draw shades?
draw_shades yes

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no

uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 8

# border margins
border_margin 4

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
gap_x 35
gap_y 15

# stuff after 'TEXT' will be formatted on screen

override_utf8_locale no
xftfont Terminus:size=8
xftalpha 0.8

TEXT

${offset 240}${color slate grey}${time %a, } ${color }${time %e %B %G}
${offset 240}${color slate grey}${time %Z,    }${color }${time %H:%M:%S}
${offset 240}${color slate grey}UpTime: ${color }$uptime
${offset 240}${color slate grey}Kern:${color }$kernel
${offset 240}${color slate grey}CPU:${color } $cpu% ${acpitemp}C
${offset 240}${cpugraph 20,130 000000 ffffff}
${offset 240}${color slate grey}Load: ${color }$loadavg
${offset 240}${color slate grey}Processes: ${color }$processes  
${offset 240}${color slate grey}Running:   ${color }$running_processes

${offset 240}${color slate grey}Core-1: ${color red}${cpu cpu0}%
${offset 240}${color slate grey}Core-2: ${color blue}${cpu cpu1}%

${offset 240}${color slate grey}Highest CPU:
${offset 240}${color #ddaa00} ${top name 1}${top_mem cpu 1}
${offset 240}${color lightgrey} ${top name 2}${top cpu 2}
${offset 240}${color lightgrey} ${top name 3}${top cpu 3}
${offset 240}${color lightgrey} ${top name 4}${top cpu 4}

${offset 240}${color slate grey}Highest MEM:
${offset 240}${color #ddaa00} ${top_mem name 1}${top_mem mem 1}
${offset 240}${color lightgrey} ${top_mem name 2}${top_mem mem 2}
${offset 240}${color lightgrey} ${top_mem name 3}${top_mem mem 3}
${offset 240}${color lightgrey} ${top_mem name 4}${top_mem mem 4}

${offset 240}${color slate grey}MEM:  ${color } $memperc% $mem/$memmax
${offset 240}${membar 3,100}
${offset 240}${color slate grey}SWAP: ${color }$swapperc% $swap/$swapmax
${offset 240}${swapbar 3,100}

${offset 240}${color slate grey}ROOT:    ${color }${fs_free /}/${fs_size /}
${offset 240}${fs_bar 3,100 /}
${offset 240}${color slate grey}HOME:  ${color }${fs_free /home}/${fs_size /home}
${offset 240}${fs_bar 3,100 /home}
${offset 240}${color slate grey}SLACK:  ${color }${fs_free /mnt/slack}/${fs_size /mnt/slack}
${offset 240}${fs_bar 3,100 /mnt/slack}
${offset 240}${color slate grey}NET: 
${offset 240}${color}Up: ${color }${upspeed eth0} k/s
${offset 240}${upspeedgraph eth0 20,130 000000 ffffff}
${offset 240}${color}Down: ${color }${downspeed eth0}k/s${color}
${offset 240}${downspeedgraph eth0 20,130 000000 ffffff}


worked 1st time for me :D
Thanks to Plasma_NZ

---

### Post by Plasma_NZ on 2008-05-26
My howto is a basic put-together of others and how i do mine...

---

### Post by Patb on 2008-05-26
```
sudo gedit .conkyrc
```
Why "sudo"?  If the file does not already exist (eg user omits previous step) access to the normal user may later be blocked because .conkyrc will be owned by root.

Conky is a lightweight but highly configurable system monitor.  There is an army of conky enthusiasts out there with a host of different configurations:
[http://ubuntuforums.org/showthread.php?t=281865](http://ubuntuforums.org/showthread.php?t=281865)

Cheers, Pat.

---

### Post by akahige on 2008-05-26
> **chrismitt2002 said:**
> #Conky Howto 

own_window yes
own_window_transparent yes
own_window_override yes



Nice write up.

One correction, though. In the quoted block (from the top of the OP, "own_window_override yes" should be "own_window_type override" (which is correct later on when you posted more of the .conkyrc).

Cheers.

---

