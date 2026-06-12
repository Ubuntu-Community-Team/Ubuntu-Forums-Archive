---
title: "Conky at startup on 18.04 with MATE 1.22 desktop..."
date: 2019-03-28
forum: General Help
---

### Post by toad007toad007 on 2019-03-28
So, after a LOT of searching on Google, I know that this is a question that has been asked and answered to death. BUT, I cannot for the life of me, no matter what I try, get conky to startup automatically at bootup, no matter what delay I put on it - 10 sec, 30 sec, 60 sec. Nothing. When I simply input the command in Synapse it runs just fine. I am running plain Ubuntu 18.04 with the MATE 1.22 desktop installed on top with Compiz as my WM (got sick of Gnome's resource hunger and slow loading at startup - though I did have it looking quite beautiful and very functional). Currently I have conky set to start with a delay of 20 seconds. Still nothing. Any ideas?

---

### Post by again? on 2019-03-28
I don't use mate but I have a test partition of Ubuntu 18.04 installed in which I just installed mate-desktop.
```
**[COLOR="#006400"]glen@ubutest:~$[/COLOR] inxi -S**
System:    Host: ubutest Kernel: 4.15.0-46-generic x86_64 bits: 64
           Desktop: MATE 1.20.1  Distro: Ubuntu 18.04.2 LTS
```

Conky starts ok when added to startup applications.
Check if conky is running but not displaying...
```
ps aux | awk '/[c]onky/'
```


I don't see a delay section in my startup applications.(MATE 1.20.1)
conky has a built in delay option.
> -p | --pause= SECONDS
Time to pause/wait before actually starting Conky.

Try using that instead.
eg
```
conky -p 10
```

Also check your desktop file that startup applications creates in ~/.config/autostart

This is my file created by startup applications...
```
**[COLOR="#006400"]glen@ubutest:~$[/COLOR] cat ~/.config/autostart/conky.desktop**
[Desktop Entry]
Type=Application
Exec=conky -p 10
Hidden=false
X-MATE-Autostart-enabled=true
Name[en_AU]=myconky
Name=myconky
Comment[en_AU]=
Comment=
```

---

### Post by toad007toad007 on 2019-03-29
No dice. Still doesn't start

---

### Post by again? on 2019-03-29
Did you check if conky was running?
Was it working before you upgraded mate to 1.22?

I just upgraded to mate 1.22 from jonathonf/mate-1.22 ppa.
The autostart applications delay also works.

Try replacing ~/.config/autostart/conky.desktop with this (has a pause of 30 secs)...
```
[Desktop Entry]
Type=Application
Exec=conky -p 30
Hidden=false
#X-MATE-Autostart-enabled=true
Name=conky
Comment=
#X-MATE-Autostart-Delay=30
```


Also try using this simple conky config at ~/.conkyrc
```
use_xft yes
xftfont Droid Sans:size=8
xftalpha 0.8
text_buffer_size 2048
background no
# Update interval in seconds
update_interval 1

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_transparent yes
own_window_type normal
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
#own_window_argb_visual no
#own_window_argb_value 0 

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 182 20
maximum_width 182

# Draw shades?
draw_shades no
default_color D6D6D6 #4D4D4D
# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Stippled borders?
stippled_borders 0

# border margins
border_inner_margin 5
border_outer_margin 3

# border width
border_width 1

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 20
gap_y 50

# Set default bar size
default_bar_size 8 60

TEXT
SYSTEM ${hr 2}
${font}${goto 36}${execi 3600 cat /etc/issue.net} $machine
${goto 36}Kernel: ${kernel}
${goto 36}Conky: ${conky_version}
${hr 2}

```
[COLOR="#FF0000"]**EDIT**[/COLOR]: I made a copy paste error of conky config...now fixed.

---

### Post by ajgreeny on 2019-03-29
Can you actually get conky to run properly using your current .conkyrc file (or whatever file you use as the config for conky) if you start it with a terminal command?

It is quite easy to get the configuration file syntax wrong, particularly since the new version of conky appeared maybe a couple of years ago now, and when starting it in terminal you may see some helpful error messages.

---

### Post by toad007toad007 on 2019-03-29
Ok, thanks for all the help guys. I got it working. I had to put a conky.desktop file in /usr/share/applications. That did the trick and it starts right up at bootup without any delay needed. SOLVED! Thanks for all the help!

---

### Post by ajgreeny on 2019-03-29
Great news! 

Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. 
It is a great help to users searching the forum.

---

