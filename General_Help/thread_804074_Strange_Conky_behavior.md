---
title: "Strange Conky behavior"
date: 2008-05-22
forum: General Help
---

### Post by LeoSolaris on 2008-05-22
Conky is booting up somewhat strangely. I have it set to boot at login, to appear under everything, and to have no border.                           Well when I login, it is above everything and compiz draws a shadow around it.


                                  Right now I am working around it with killall conky, then conky in my terminal. When it restarts, it restarts perfectly, meaning it's flushed to the desktop and doesn't have a shadow around it from compiz.


Does compiz mess with conky, or is this an error on my part somehow?

Solved, see my final post.

---

### Post by mano cazalet on 2008-05-22
Not sure if it is related to compiz settings or something else. Mine is working fine with compiz enabled.

maybe you can post your conkyrc here
or at the [conky gurus place]("http://ubuntuforums.org/showthread.php?t=205865")

:)

---

### Post by cammin on 2008-05-22
I'm guessing that Compiz is starting after Conky and doesn't know how to handle the window.

See if you can get Conky to load later in the startup process.

---

### Post by kerry_s on 2008-05-22
put a little sleep time on your conky startup command.

**sleep 5;conky**

---

### Post by LeoSolaris on 2008-05-22
Well guys, the conkyrc I am using is copied from [the show and tell thread]("http://ubuntuforums.org/showthread.php?p=5018953#post5018953"). I have modified it some from that based, but it has always done it, ever since the first reboot with it on. (I meant to log out and back in but click the wrong one)

Just because I forgot to mention it in my first post, I am using 8.04 64-bit.

Just to see if it works, how do I change the boot order so to speak? 

Just to post it, here is the current incarnation.

```
# do not fork to background
background no

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer right
use_xft yes

# Update interval in seconds
update_interval 1.0

# Minimum size of text area
minimum_size 10 5

# Draw shades?
draw_shades no

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
default_color 75B6D1
default_shade_color black
default_outline_color white

#own_window_colour no

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 10
gap_y 30

# stuff after 'TEXT' will be formatted on screen


override_utf8_locale yes
xftfont sans:size=8
xftalpha 0.8
TEXT
${offset 0}${color #FFF500}${font sans:size=10}${exec whoami}@${exec hostname}$font
 ${offset 0}${color #ffffff}Date/Time ${stippled_hr }
 ${offset 0}${color #ffffff} ${time %a, }${color #ffffff}${time %e %B %G  }${color #ffffff} ${color #ffffff}${time %H:%M:%S}${time %Z}

${offset 0}${color #ffffff}System Info ${stippled_hr }

 ${offset 0}${color #ffffff} UpTime: ${color }${alignr}$uptime
 ${offset 0}${color #ffffff} Kern:${color }${alignr}$kernel
 ${offset 0}${color #ffffff} Battery: ${color }${alignr}${battery BAT0}

${offset 0}${color #ffffff}CPU INFO ${stippled_hr }

  ${offset 0}${color #ffffff} CPU Clock: ${color }${alignr}${freq_g}GHz
  ${offset 0}${color #ffffff} Load: ${color }${alignr}$cpu %
  ${offset 0}${color #ffffff} Load Avg: ${color }${alignr}$loadavg
  ${offset 0}${color #ffffff} Processes: ${color }${alignr}$processes
  ${offset 0}${color #ffffff} Running:   ${color }${alignr}$running_processes

${alignc}${color #ffffff}Highest CPU
${alignc}${color } ${top name 1}${top cpu 1}%
${alignc}${color } ${top name 2}${top cpu 2}%

${alignc}${color #ffffff}Highest MEM
${alignc}${color } ${top_mem name 1}${top_mem mem 1}%
${alignc}${color } ${top_mem name 2}${top_mem mem 2}%

${offset 0}${color #ffffff}Memory and Storage${stippled_hr }

${offset 0}${color #ffffff}MEM:
 ${offset 0}${color }$mem/$memmax${alignr}${membar 3,150} ${memperc}%

${offset 0}${color #ffffff}SWAP:
 ${offset 0}${color }$swap/$swapmax${alignr}${swapbar 3,150} ${swapperc}%

${offset 0}${color #ffffff}ROOT:
 ${offset 0}${color }${fs_used /}/${fs_size /}${alignr}${fs_bar 3,150 /} ${fs_used_perc /}%

${offset 0}${color #ffffff}HOME:
 ${offset 0}${color }${fs_used /home}/${fs_size /home}${alignr}${fs_bar 3,150 /home} ${fs_used_perc /home}%

${offset 0}${color #ffffff}Windows:
 ${offset 0}${color }${fs_used /media/Windows}/${fs_size /media/Windows}${alignr}${fs_bar 3,150 /media/Windows} ${fs_used_perc /media/Windows}%

${offset 0}${color #ffffff}NETWORKING ${stippled_hr }


${color #ffffff}NETWORK (${addr wlan0} ${wireless_essid wlan0})
 ${offset 0}${color #ffffff}Down: $color${downspeed wlan0} kb/s${alignr}${color #ffffff}UP:   $color${upspeed wlan0} kb/s
 Total Down: ${totaldown wlan0}${alignr}Total Up:   ${totalup wlan0}

```

---

### Post by LeoSolaris on 2008-05-22
Ok, I just tried the sleep 5;conky (and sleep 5:conky just to be safe) and it did not do anything. Could that be because I used the save session option on the last tab to get rid of the gnome panel? Maybe I should try making a desktop launcher with the sleep timer built in to see if saving that can sneak it around the saved session.

---

### Post by kerry_s on 2008-05-23
> **LeoSolaris said:**
> Ok, I just tried the sleep 5;conky (and sleep 5:conky just to be safe) and it did not do anything. Could that be because I used the save session option on the last tab to get rid of the gnome panel? Maybe I should try making a desktop launcher with the sleep timer built in to see if saving that can sneak it around the saved session.

you can kill conky, save the session, then add conky to the startup. you might also need to put the command in a script.
example:
gedit .conky5

#!/bin/sh
sleep 5;conky &

chmod +x .conky5

then put ~/.conky5 for the startup command.

---

### Post by LeoSolaris on 2008-05-23
I gave it a try. C&P'ed it, but no joy. Oddly my awn(bzr version) failed to start up a couple times. I need sleep it's 1:45 am here.

---

### Post by LeoSolaris on 2008-05-23
Alright, back at the problem. Here's what I have tried so far this morning. I added the script back again, this time I put a little thought into it and realized that the "chmod" was meant as a command to be put in terminal, not added to the file. So I removed it, made the file executable, and tried again. It did work, but it was a root conky, rather than a user conky. so I had to sudo killall conky to be rid of it. I removed the script from the start up list and altered its name just to be safe.

Frustrated I purged conky, restarted, then did the "save session" command. logged out and back in to be sure after reinstalling conky, but to my utter frustration, conky reappeared, this time as the standard one probibly because I renamed the .conkyrc file.

I do believe that was the point at which I started screaming. After calming down and meditating for a little while, I came back here.

What the hell? Where is the list for the saved session? I would like to edit it by hand. It seems to never over write, just add. 



Wait, I  just thought of something...   hmm   strange. I have conky killed. It's not currently running, but in the current session tab, it's still there, along with the script, and the sleep 5;conky...  what the?  I removed them and resaved the session...  let's try this.


Edit: WOOOHOOOOO!!!!    Man that was frustrating!  

Ok  here's how I got it to finally work. 

I removed conky from the currently running tab, and logged out. Came back, no conky. 

Step in the right direction. 

I deleted conky's entry on the Startup Programs tab, then relogged in. Ok, still no conky. 

I remade the script kerry_s gave me, and added it to the Startup Programs list. Relogged in, and voila! Conky started after 5 seconds, although it did delay AWN's start and made the whole startup process take 5 seconds longer, I am ok with that.

Finally, it bloody works!

Thank you guys so very very much! This was driving me batty.

Leo

---

### Post by kerry_s on 2008-05-23
it shouldn't add to the startup, did you put the "&" on the end? that backgrounds it so the rest of the desktop can continue to load while that sleeps.

---

### Post by LeoSolaris on 2008-05-24
ooohhh...   that explains a little bit!   thanks!

Leo

---

