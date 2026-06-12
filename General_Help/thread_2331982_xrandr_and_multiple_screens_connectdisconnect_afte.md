---
title: "xrandr and multiple screens connect/disconnect after update 14.04 to 16.04"
date: 2016-07-27
forum: General Help
---

### Post by nicke-claesson on 2016-07-27
Hey everyone,

When I ran 14.04 and connected/disconnected monitors they would automatically get added/removed to my "virtual screen". I don't remember having to setup anything special to make it work this way. After upgrading to 16.04 this is not the case anymore. If I disconnect a monitor all the windows on that monitor are out of the visible area instead of being rearranged to the monitors that are still connected.

Basically I want something like this to be called when a monitor is connected/disconnected:

```
xrandr --output eDP1 --auto --output DP1 --auto --right-of eDP1 --output DP2 --auto --right-of DP1
```

Which would be the same behaviour as 14.04.

Trying to get this to run I wrote an udev rule and a script:

```
ACTION=="change", SUBSYSTEM=="drm", RUN+="/usr/local/bin/hotplug-monitor.sh"
```

```
#!/bin/bash
export DISPLAY=:0
export XAUTHORITY=/home/<my-username>/.Xauthority                                                                                                                                            

A=$(cat /sys/class/drm/card1-DP-1/status)
B=$(cat /sys/class/drm/card1-DP-2/status)

if [[ "$A" == "connected" ]] ; then
»···a="--output DP1 --auto --right-of eDP1"
else
»···a="--output DP1 --off"
fi

if [[ "$B" == "connected" ]] ; then
»···b="--output DP2 --auto --right-of DP1"
else
»···b="--output DP2 --off"
fi

xrandrargs="--output eDP1 --auto $a $b"

/usr/bin/xrandr $xrandrargs 2>&1 >> /tmp/hotplug.log

date >> /tmp/hotplug.log
echo $xrandrargs >> /tmp/hotplug.log


```

I can verify that my script is run by looking at /tmp/hotplug.log. However nothing happens. The script is run, xrandr is not complaining, but the screens doesn't change. Could it be that my scripts get called before xrandr is able to find out the status of my monitors?

Does anyone have a solution to this?

btw, I'm running Ubuntu 16.04 with Awesome WM in a gnome session.

---

