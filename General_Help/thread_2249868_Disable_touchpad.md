---
title: "Disable touchpad"
date: 2014-10-25
forum: General Help
---

### Post by dovydas2 on 2014-10-25
Hi. How do I disable a touchpad? Seriously, all shortcut keys on my laptop are working except for a touchpad! Also can't believe there are no option to disable a touchpad on mouse & touchpad settings. Only solution I could find was install touchpad-indicator, but it resets after reboot or even suspend, so I need to disable it manually every time, so it does not solve a problem. Dammit, we live in 2014 where a lot of users use laptops and we still don't have option by default to disable touchpad???

---

### Post by sudodus on 2014-10-26
I have a small bash function, that can be added the end of the bash configuration file **~/.bashrc** (for one user) or at the end of **/etc/bash.bashrc** (for all users).

```
# Appended to /etc/bash.bashrc

alias TT='touchpad-toggle'

function touchpad-toggle {

# toggle synaptic touchpad on/off

# get current state
SYNSTATE=$(synclient -l | grep TouchpadOff | awk '{ print $3 }')

# change to other state
if [ $SYNSTATE = 0 ]; then
    synclient touchpadoff=1
    echo "touchpad OFF"
elif [ $SYNSTATE = 1 ]; then
    synclient touchpadoff=0
    echo "touchpad ON"
else
    echo "Couldn't get touchpad status from synclient"
    exit 1
fi
}

####

alias TT

```

This way, it will remind me to use TT (to run touchpad-toggle). If you want it off always (or starting off), you can use part of the script, and put it into ***autostart***, which is configured in different ways in different flavours of Ubuntu.

```
synclient touchpadoff=1
```

turns the touchpad off.

---

