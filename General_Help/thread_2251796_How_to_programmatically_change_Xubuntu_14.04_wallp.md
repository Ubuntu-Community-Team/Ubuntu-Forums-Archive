---
title: "How to programmatically change Xubuntu 14.04 wallpaper?"
date: 2014-11-06
forum: General Help
---

### Post by Max the Happy User on 2014-11-06
Please help me find this:

**A shell command which will instantly change the wallpaper to the next random wallpaper from my wallpaper list.** Basically, I want to be able to do the same thing which *Desktop right-click -> Desktop Settings* does once you have set it up to rotate randomly between wallpapers from a chosen directory.

I have already set up a directory where my images are, ticked "Change the background", chosen the number of minutes, and ticked "Random order".
I did it through Desktop right-click -> Desktop Settings.
It works perfectly - every 10 minutes the wallpaper changes to a random one from that directory.
But I would also like to be able to change it at will using a shell command (I'd bind it to a key).


I've Googled for hours and stumbled upon these solutions only:

```
xfdesktop --reload
killall -HUP xfdesktop
killall -USR1 xfdesktop
killall -USR2 xfdesktop
```

and there were two more, if I'm not mistaken. They didn't work. I suspect it's because I use newer Xubuntu and XFCE versions.

Thanks in advance.

---

### Post by CantankRus on 2014-11-06
Try 
```
xfconf-query -c xfce4-desktop -p /backdrop/screen0/monitor$(xrandr -q | awk '/ connected/{print $1}')/workspace0/last-image -s [COLOR="#808080"]**/path/to/image**[/COLOR]
```

I can use this command to change to a random picture from a directory...
```
xfconf-query -c xfce4-desktop -p /backdrop/screen0/monitor$(xrandr -q | awk '/ connected/{print $1}')/workspace0/last-image -s **"$(find "[COLOR="#FF0000"]/home/glen/Pictures/wallpaper[/COLOR]" -type f -iname '*.jpg' -or -iname '*.jpeg' -or -iname '*.png' | shuf -n 1)"**
```

Edit to reflect [COLOR="#FF0000"]your wallpaper directory[/COLOR]

and a random wall changer script that works for me.
```
#!/bin/bash

device=$(xrandr -q | awk '/ connected/{print $1}')	# connected device
wallpaperdirectory=/home/fred/Pictures/wallpaper	# set your wallpaper directory
interval=10	# minutes between wallpaper change

while [ 1 ]; do
	xfconf-query -c xfce4-desktop -p /backdrop/screen0/monitor"$device"/workspace0/last-image -s "$(find "$wallpaperdirectory" -type f -iname '*.jpg' -or -iname '*.jpeg' -or -iname '*.png' | shuf -n 1)" 
	sleep "$interval"m
done
```

---

### Post by Max the Happy User on 2014-11-07
Thanks, Gleb, it worked!

After adapting the script to my system (a different directory and all image files are without extensions, the directory contains only the desired images) it looks like this:

```
xfconf-query -c xfce4-desktop -p /backdrop/screen0/monitor$(xrandr -q | awk '/ connected/{print $1}')/workspace0/last-image -s "$(find "/home/max/.local/share/xfce4/backdrops" -type f -iname '*' | shuf -n 1)"
```

So now I have a keyboard shortcut to change my wallpaper randomly, plus Xubuntu does it as well independently every 10 minutes.

If you wonder why I want that, I have a collection of quotes (aphorisms), which I edited so that they fit nicely as wallpapers. So whenever I look at my desktop, I see a fresh quote. With your help, now I can also see a new quote at will, if I'm in the mood for one.

---

### Post by CantankRus on 2014-11-07
Very nice.
Ever looked at **conky** to display Text on screen?
eg pic shows conky used with the fortune application.
Would be very simple to display random lines from a text file.

---

