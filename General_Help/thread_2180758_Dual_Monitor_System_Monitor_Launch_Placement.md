---
title: "Dual Monitor: System Monitor Launch Placement"
date: 2013-10-14
forum: General Help
---

### Post by lastlion on 2013-10-14
Ubuntu 12.04

When i place the command below in the startup applications list the geometry is not respected on next boot.  When I issue this command from a terminal from my main monitor it places the system monitor on the second monitor like I want.  But on reboot it does not.

```
gnome-system-monitor --geometry 80x25+100+100
```

I have tried wmctrl to control placement and that doesn't work.  

And then there's this.  Only one display is available for reference.  
```
echo $DISPLAY
:0
```

Both monitors boot fine.  Clementine music player is also launched on startup and it seems to be "smart" enough to remember to launch on the second monitor which is where I kept placing it.  I do not put any placement parameters for Clementine.

How to make this same thing happen with system monitor?

---

### Post by erind on 2013-10-14
> **lastlion said:**
> Ubuntu 12.04

When i place the command below in the startup applications list the geometry is not respected on next boot.  When I issue this command from a terminal from my main monitor it places the system monitor on the second monitor like I want.  But on reboot it does not.

```
gnome-system-monitor --geometry 80x25+100+100
```
[...]

Try it with '*sleep 5 *'  (or some other value) first:

```

sleep 5 && gnome-system-monitor --geometry 80x25+100+100

```

Check this thread below too:

[http://ubuntuforums.org/showthread.php?t=2041248](http://ubuntuforums.org/showthread.php?t=2041248)

---

### Post by lastlion on 2013-10-15
Sleep method doesn't work.  In fact, the monitor won't even launch w.

---

### Post by erind on 2013-10-15
It works if '*sleep <N>*' is included inside a script (see again my link above), and run from the script. In my setup Xubuntu 12.04, if I simply use '*gnome-system-monitor*' command in Applications Startup, it works fine, it even retains its previous position across reboots. Nevertheless try this script below (start_sys_monitor), make it executable and add its path into the Startup Applications: 

[ *Tested on a single monitor setup, Xubuntu 12.04 *]

*start_sys_monitor*
```

#!/bin/bash
## Tested on a single monitor setup, Xubuntu 12.04

gnome-system-monitor &

sleep 20    ## [COLOR=#0000ff]change this value between 10-20 secs or more. [/COLOR]

wmctrl -r 'System Monitor' -e '0,660,300,400,450'

####
```

'*sleep <N>*' above is crucial, change its value as you see fit. Afterwards *wmctrl *does the window positioning, (modify it to your specific needs as well. See end notes).
I can't find any mention of *--geometry *option in man pages for '*gnome-system-monitor'*, in my tests it simply gets ignored, so I didn't use it. Just in case, there are also other commands that interact with window managers, *xdotool *being one of them.

--

From *wmctrl* man pages:
> 
       **-e <MVARG>**
              Resize  and  move  a  window  that  has been specified with a -r
              action according to the <MVARG> argument.
            **<MVARG>**
              A move and resize argument has the format 'g,x,y,w,h'.  All five
              components are integers. The first value, g, is the  gravity  of
              the  window,  with  0  being  the most common value (the default
              value for the window).

---

