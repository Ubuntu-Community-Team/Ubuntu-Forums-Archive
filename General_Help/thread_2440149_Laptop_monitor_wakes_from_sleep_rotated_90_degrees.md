---
title: "Laptop monitor wakes from sleep rotated 90 degrees"
date: 2020-04-06
forum: General Help
---

### Post by jon-carmicheal on 2020-04-06
When my laptop wakes from sleep, the screen is rotated 90 degrees, even if it is kept level on the table the entire time (before going to sleep and after resuming).  After I enter my password, I can tilt the laptop then return it to level, and the screen will auto-orient to the correct orientation.  But it is very annoying to have to do that each time.

This started a few days ago when I was trying to get my screen to rotate (it wouldn't auto-rotate at the time).  I entered a few commands, including these:

```
xrandr -o normal
xrandr -o left
sudo xrandr -o left
xrandr --output $(xrandr |grep eDP|cut -d" " -f1) --rotate left
```


It had no effect at the time, but later (after reboot?) the laptop started auto-rotating the screen correctly, except that when it wakes up from sleep the screen is incorrectly rotated 90 degrees.  I've tried the following, but none have resolved the issue:
```
sudo xrandr -o right
sudo xrandr 
sudo xrandr --output XWAYLAND0 --rotate right
sudo xrandr --output XWAYLAND0 --rotate up
xrandr --help
xrandr --query
xrandr --rotate --query
xrandr --rotate 0
sudo xrandr --output XWAYLAND0 --rotate 0
sudo xrandr --output XWAYLAND0 --normal
sudo xrandr --output XWAYLAND0 --rotate normal
sudo xrandr --output XWAYLAND0 --rotate left
sudo xrandr --output XWAYLAND0 --rotate normal
xrandr --output XWAYLAND0 --rotate normal
xrandr --orientation normal
sudo xrandr --orientation normal

```

Is there anything else that could be causing this?

I'm running Ubuntu 19.10 (5.3.0-45-generic) on a Lenovo Flex 14.

---

