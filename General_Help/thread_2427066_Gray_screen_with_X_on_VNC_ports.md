---
title: "Gray screen with X on VNC ports"
date: 2019-09-17
forum: General Help
---

### Post by ndnd on 2019-09-17
Hello, 

I have the following system 
> Distributor ID:	Ubuntu
Description:	Ubuntu 18.04.3 LTS
Release:	18.04
Codename:	bionic

I have installed tightvnc and xfce desktop environment
> ls /usr/bin/*session
/usr/bin/byobu-select-session  /usr/bin/dbus-run-session  /usr/bin/xfce4-session

Now I am able to run the vncserver which works perfectly for ssh tunnelling using 
> vncserver :1 -geometry 1920x1080 -depth 24/QUOTE]

[QUOTE]$ vncserver :1 -geometry 1920x1080 -depth 24

New 'X' desktop is analyze-2020:1

Starting applications specified in /home/user1/.vnc/xstartup
Log file is /home/user1/.vnc/analyze-2020:1.log



This works perfectly! I am able to login and see the desktop

However, when I do the same for 
>  vncserver :2 -geometry 1920x1080 -depth 24

New 'X' desktop is analyze-2020:2

Starting applications specified in /home/user1/.vnc/xstartup
Log file is /home/user1/.vnc/analyze-2020:2.log

I get a grey screen with 'X' - Please see attached file 

Same grey screen I get for 5903,5904...

My xstartup file is 
> #!/bin/sh

xrdb $HOME/.Xresources
xsetroot -solid grey
#x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
#x-window-manager &
# Fix to make GNOME work
export XKL_XMODMAP_DISABLE=1
/etc/X11/Xsession



I have also tried 
vncserver -kill :1
vncserver -kill :2 
.
. 

As well as tried to remove the 
files in tmp 
> rm -f /tmp/.X1-lock
rm -f /tmp/.X2-lock
rm -f /tmp/.X3-lock
rm -f /tmp/.X11-unix/X1 
rm -f /tmp/.X11-unix/X2
rm -f /tmp/.X11-unix/X3
rm -r /home/user1/.cache/sessions/*

I am also attaching the logs 
I have been seeing lot of posts stating changes in startup but I am not sure which one is right and I don't want to spoil the 5901 port that works! :(

Any help would be really appreciated I just don't know what is wrong here. :confused:

In case you need any additional info please let me know the exact command as I am not an expert with linux

---

### Post by TheFu on 2019-09-17
The gray background means that X/Windows is running, but that no WM has been told to run.  In the startup file, be certain you run a WM+DE or just a WM.  

```
xsetroot -solid grey  # <----- this is why the gray background happens.
```

BTW, if you want much better performance with built-in security, check out x2go or any NX-based remote desktop solution.  Easily feels 2-3x faster than any VNC solution.  And you can tune the amount of bandwidth used, based on the available bandwidth between the client/server connection.  I've used x2go from 5 different continents.  People who switch say it is like the difference between night and day.

---

### Post by ndnd on 2019-09-17
Thanks a lot TheFu for the quick reply. 

When you say WM+DE   do I need to insert (shown in color)

> #!/bin/sh

xrdb $HOME/.Xresources
xsetroot -solid grey
#x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
#x-window-manager &
# Fix to make GNOME work
export XKL_XMODMAP_DISABLE=1
/etc/X11/Xsession
[COLOR="#0000FF"]startfxce4 &[/COLOR]

Or uncomment the following lines (shown in color) 

> #!/bin/sh

xrdb $HOME/.Xresources
xsetroot -solid grey
[COLOR="#0000FF"]x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
x-window-manager &[/COLOR]
# Fix to make GNOME work
export XKL_XMODMAP_DISABLE=1
/etc/X11/Xsession

I am not very familiar with desktop environment so wanted to know the specific commands. 

In terms of x2go will definitely check it out. Thank you for that.

---

### Post by TheFu on 2019-09-17
I don't know.  Haven't used VNC much in about a decade. Since I was an X/Windows programmer years ago, any issues were trivial to fix quickly.  
There was a post here last week with a specific solution for the same problem you reported - gray background.
Really, you'll find x2go much easier and faster.  Use a lighter DE since Gnome3 and heavy DEs aren't supported.  XFCE, LXDE, Mate all work very well.  I use just fvwm or openbox which aren't DEs. They are WMs.

---

### Post by ndnd on 2019-09-18
Hello, 
Can anyone please let me know..
I have Desktop environment only on Port 5901 and rest of the ports I only get a black X.

---

