---
title: "Disable touchpad while typing - adjust disable duration"
date: 2013-10-11
forum: General Help
---

### Post by tyteen4a03 on 2013-10-11
Hey - I'd like to disable my touchpad while typing, however it restores its original status only a few seconds after I stopped typing. How can I adjust the disabled timing period from the moment I stop pressing keys?

---

### Post by sudodus on 2013-10-11
It is easy if you disable it until you decide that you want it again. You can do that with touchpad-indicator (which is a little tricky in the newest versions of the Ubuntu family), or a simple script function, that you can add to your .bashrc file. I use touchpad-toggle and make an alias to TT

```
alias TT='touchpad-toggle'

###

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

---

