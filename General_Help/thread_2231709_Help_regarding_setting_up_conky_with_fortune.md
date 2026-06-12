---
title: "Help regarding setting up conky with fortune"
date: 2014-06-27
forum: General Help
---

### Post by amhndu on 2014-06-27
I want to configure *conky* such that it displays a *fortune* message , after some Googling and editing another *conky* script *Mira ,*this is what I have so far ,
```

#This comes from the Mira-blue conky script ( I don't remember the author )
#I removed some insignificant parts and edited the TEXT part
use_xft yes
xftfont cure:size=8


# Create own window instead of using desktop (required in nautilus)
own_window  yes
own_window_transparent no
#own_window_type widget
own_window_hints undecorate,sticky,skip_taskbar,skip_pager 


# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes


# Minimum size of text area
minimum_size 300 70


# Draw shades?
draw_shades no


# Draw outlines?
draw_outline no


# Draw borders around text
draw_borders yes


# Stippled borders?
stippled_borders 0


# border width
border_width 1


# Default colors and also border colors
default_color 303030
#default_shade_color white
#default_outline_color black
own_window_colour 262524


# Text alignment, other possible values are commented
alignment top_left
#alignment top_right
#alignment bottom_left
#alignment bottom_right


# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 230#20
gap_y 40#45


# set to yes if you want all text to be in uppercase
uppercase no


# Force UTF8? note that UTF8 support required XFT
override_utf8_locale yes


# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer true


TEXT
${color a4a4a4}${font Ubuntu Condensed:size=13}${execi 320 fortune}

```
The problem is that when I log-in to my system (auto-login though , I'm the sole user) ,
the message doesn't show up instead there's a > (null) in the output , I assume it's probably related to execi , further when it auto updates after the specified interval , many the times the message overflows the box , I worked around this by specifying a minimum size , solves the problem for a few cases .
I thought , If I delayed the launch it would fix it , but in vain.
Further , I have no *conky *configuring knowledge and incidentally I don't know how to use execi and all , all I ever did was use others' , the man page is pretty big and intimidating :D.
FYI , here's my startup script and some other trivial details , If it matters at all
```

#!/bin/bash
sleep 10
conky -c ~/.conky/Mira_blue/.conkyrc_clock &
conky -c ~/.conky/Mira_blue/.conkyrc_sys &
conky -c ~/.conky/Mira_blue/.conkyrc_net &
conky -c ~/.conky/Mira_blue/.conkyrc_disk &
conky -c ~/.conky/fortune_rc &
exit 0

```
conky version : 1.8.1 (conky -v gave a long output though)
Ubuntu 12.04.1 , Unity removed and installed the *lubuntu-desktop* package (not in this order ofcourse ;) )

Also , if you have a really cool conky script with fortune , share it .

Thanks for any help.

---

### Post by ajgreeny on 2014-06-27
The ${execi 320 fortune} that you are using means that the fortune message will not show until the 320 seconds has elapsed after conky starts, and then presumably changes every 320 seconds following that.  Itmay be worth using the command **conky -p 10** for the autostart of conky to delay the start for 10 seconds as I found some anomalies in the display if it started too quickly, and before the DE was fully up and running.

I am not sure I can help with the text overflow problem, but it could be worth searching for "text wrapping in conky" which is where I found this possibility
```
${execi 300 fortune | fold -w66}
``` editing the **fold -w66** to fit your conky's width.

---

### Post by amhndu on 2014-06-28
How can I make the specified command run when conky starts with exec* ?

Thanks for the tip , besides I found a fortune argument which only displays cookies less than the specified length.

---

### Post by ajgreeny on 2014-06-28
> **amhndu said:**
> How can I make the specified command run when conky starts with exec* ?

Thanks for the tip , besides I found a fortune argument which only displays cookies less than the specified length.
Sorry, but I have no idea about that.

EDIT:
A quick search for my own info suggests that you can use ```
${exec fortune | fold -w66}
``` to run the command once at conky start, but then it will not be repeated every 320 seconds; if you run both command in the conky config you would get two instances of fortune showing, one which was constant and the second that changes.

---

### Post by amhndu on 2014-07-02
I worked it out some way.
I saw in the *fortune *man page the *-s* option which when set , fortune only displays small cookies smaller than the length specified by the *-n* option , default is 160.
It still shows (null) the first time , and further it is updated after the specified interval.
Here's my new  fortune_rc file,
```
# Use Xft?use_xft yes
xftfont cure:size=8

# Create own window instead of using desktop (required in nautilus)
own_window  yes
own_window_transparent no
own_window_hints undecorate,sticky,skip_taskbar,skip_pager


# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes


# Minimum size of text area
minimum_size 500 100


# Draw shades?
draw_shades no


# Draw outlines?
draw_outline no


# Draw borders around text
#draw_borders yes


# Stippled borders?
#stippled_borders 0


# border width
#border_width 1


# Default colors and also border colors
default_color 303030
own_window_colour 262524


# Text alignment, other possible values are commented
alignment top_left

# Gap between borders of screen and text
gap_x 230
gap_y 40

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale yes


# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer true


TEXT
${color a4a4a4}${font Ubuntu Condensed:size=13}${execi 100 fortune -s linuxcookie riddles science linux computers paradoxum}



```

---

### Post by amhndu on 2014-07-14
[B]FIXED
[/B]The (null) was due to a bug in the conky provided by **precise **repositories.
**More**
[http://ubuntuforums.org/showthread.php?t=2072429](http://ubuntuforums.org/showthread.php?t=2072429)

---

