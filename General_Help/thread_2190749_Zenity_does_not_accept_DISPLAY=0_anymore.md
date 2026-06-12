---
title: "Zenity does not accept DISPLAY=:0 anymore"
date: 2013-11-29
forum: General Help
---

### Post by Redsandro on 2013-11-29
I have a script that runs from **udev** when I plug in my external drive. It always worked. But after upgrading from Ubuntu **12.10** to **13.10**, it doesn't work anymore.

The script still runs, but none of the commands that require the display work. I figured that out by quitting the **udev** daemon and manually run **udevd -debug** (more below).

This script used to work in Ubuntu **12.10**:
```

export DISPLAY=:0
UUID=$1
DEV=$2

notify-send -t 700 "mounting $DEV ($UUID)"
gnome-terminal -t "Backing up home..." -x rsync long line of data
zenity --warning --text="Done."

```

But not anymore in **13.10**. So I gradually added stuff and now it looks like this:
```

export DISPLAY=:0.0

xhost +local:
xhost +si:localuser:root
xhost +

DISPLAY=:0.0
export DISPLAY=:0.0
UUID=$1
DEV=$2

notify-send -t 700 "mounting $DEV ($UUID)"
gnome-terminal -t "Backing up home..." -x rsync long line of data
zenity --warning --text="Done." --display=:0.0

```
But it still doesn't work. udev -debug shows this:

> 
'(err) 'No protocol specified'
'(err) ''
'(err) '** (gnome-terminal:24171): WARNING **: Could not open X display'
'(err) 'No protocol specified'
'(err) 'Failed to parse arguments: Cannot open display: '
'(err) 'No protocol specified'
'(err) ''
'(err) '** (zenity:24173): WARNING **: Could not open X display'
'(err) 'No protocol specified'
'(err) ''
'(err) '(zenity:24173): Gtk-WARNING **: cannot open display: :0.0'
'(err) 'No protocol specified'


Note that any bash logic works, echoing test vars to >>/tmp/test.log works. It's just accessing the display that doesn't work anymore.

This is driving me crazy. Thoughts, anyone?

---

