---
title: "Replacement for gnome-power-manager?"
date: 2006-11-10
forum: General Help
---

### Post by AlucardZero on 2006-11-10
In my quest to switch to Fluxbox, I have two problems left.  One [here](http://ubuntuforums.org/showthread.php?t=294672), and the other with gnome-power-manager.  It (now) refuses to stick around in Fluxbox's tray, so my question is if there is a replacement program that will give me the tray icon with battery status etc, and that, like g-p-m, can suspend/hibernate the (laptop) computer after set amounts of time, and act differently based upon whether the AC cord is plugged in or not.  Thanks for any suggestions.

---

### Post by kerry_s on 2006-11-10
I use xset to set my settings. Use xset q to see the settings. Here are mine->

xset s off off &   <- turns screen saver off
xset +dpms &     <- turns dpms on, mplayer likes to turn it off
xset dpms 0 0 300 &  <- turns screen off in like 5 min.

I run these at startup, but i also have a launcher that runs it and turns the screen off in 10 seconds, just so i don't have to wait to get some sleep ;) 

#!/bin/sh

sleep 10
xset +dpms & 
xset s off off &
xset dpms 0 0 300 &
xset dpms force off &


forgot xset is already installed by default, power managers are just the gui front end

---

### Post by stealth17 on 2007-01-05
I'm looking for something as well. I just want something with all the info like GPM. It has some pretty neat info about the battery and power usage! How did you open it from fluxbox? Did you open Gnome Control Center and then goto it?

---

### Post by AlucardZero on 2007-01-05
I just ran gnome-power-manager.

I don't need this anymore, as I settled on XFCE.

---

### Post by stealth17 on 2007-01-07
Ahhh I got it!

Here are a couple shots:
[attach]22491[/attach] [attach]22492[/attach]

I'm on Ubuntu Edgy 6.10 and Fluxbox 0.9.15

To get it to start with Fluxbox and to make it stay there do this:

```
$ gedit ~/.fluxbox/startup
```In the file add gnome-power-manger with a & after it like so:

```
# Applications you want to run with fluxbox.
# MAKE SURE THAT APPS THAT KEEP RUNNING HAVE AN ''&'' AT THE END.
#
# unclutter -idle 2 &
# wmnd &
# wmsmixer -w &
# idesk &
gkrellm &
[highlight]gnome-power-manager &[/highlight]
fbdesk &
```Restart and it should be there! If it's not, type:

```
$ gnome-power-preferences
```and in the General tab select "Always Display Icon." If it hasn't showed up yet then do a full restart again. You should be golden after that :p

Thanks to all who helped in other threads, I hope someone else enjoys this as much as I do!

-Jordan
TheOverclocked.com

---

### Post by cam_tram on 2007-02-10
That didn't work for me.  G-P-M is running (it still makes popups when I unplug), and its set to always display the icon.

---

