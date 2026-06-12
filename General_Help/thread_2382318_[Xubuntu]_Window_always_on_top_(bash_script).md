---
title: "[Xubuntu] Window always on top (bash script)"
date: 2018-01-11
forum: General Help
---

### Post by porparek on 2018-01-11
Hi
I open xterm window from bash script. I want this window to be always on top so I run it from bash script as follows:
xterm
wmctrl -r :ACTIVE: -b toggle,above


  It works in most cases but not all. The wmctrl requires the window to  show up to manipulate on it. When the system is overloaded it takes  some time for the window to show up. In such case wmctrl command in my  script is called on another window. In case I use the specific window  name in "-r" parameter it also doesn't work since the named window is  not present at the moment when wmctrl is called. How can I solve my  issue ?

  I use XFCE in Xubuntu 16.04.

  thanks in advance

---

### Post by dragonfly41 on 2018-01-11
Try Yakuake .. drop down shell window .. F12 to toggle .. 
Set options in bottom right bar.
"Keep window open when it loses focus"

---

### Post by Holger_Gehrke on 2018-01-11
Try it like this:```

#/bin/bash
xterm & # start a terminal in the background
PID=$! # get the process id of the newest process in the background (our xterm)
sleep 0.5 # wait for the windowmanager to construct the window
WINID=$(wmctrl -lp|grep $PID|cut -d' ' -sf1) # get the list of all windows, search it for the pid, get the window-id (first field)
wmctrl -ir $WINID -b toggle,above # use the window-id instead of the name, matching window-names is not a sure thing

```
You might want to adjust the period the script sleeps. Also: 'above' doesn't make a window stay in the foreground, it just puts it there; other windows can and will cover it. I don't think there is a property you can set through wmctrl which will make the window stay in the foreground although xfwm4 does have that capability.

Holger

---

