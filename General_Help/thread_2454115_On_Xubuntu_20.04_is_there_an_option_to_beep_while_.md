---
title: "On Xubuntu 20.04 is there an option to beep while toggling Caps Lock and Num Lock?"
date: 2020-11-23
forum: General Help
---

### Post by Saptarshi_Roy on 2020-11-23
Greetings!


I'm using Xubuntu 20.04 and what is missing is an option to enable a beep sound while toggling the Caps Lock and the Num Lock keys, and any advise/suggestion on how to achieve the desired functionality would be greatly appreciated.


Thank you.

---

### Post by pqwoerituytrueiwoq on 2020-11-23
have this run in the background as root on boot, this will produce a beep between 0 and 1 second after you hit the key
```

#!/bin/sh
modprobe pcspkr # Enabled beep speaker (less common hardware to have in custom builds as case manufacture no longer ship them, still common in the typical dell/hp box)
while [ 1 -eq 1 ];do # infinite loop
        numlock=$(cat /sys/class/leds/input28\:\:numlock/brightness) # get numlock
        capslock=$(cat /sys/class/leds/input28\:\:capslock/brightness) # get capslock
        if [ -n "$lnumlock" ];then # make sure this is not the 1st loop
                if [ $numlock -ne $lnumlock -o $capslock -ne $lcapslock ];then # check for change in numlock/capslock
                        echo -en "\a" > /dev/tty5 # make it beep
                fi
        fi
        sleep 1 # wait 1 second
        lnumlock=$numlock # store last numlock state
        lcapslock=$capslock # store last capslock state
done

```
note the lines to get the led status:
```
~$ ls /sys/class/leds/
input28::capslock  input28::scrolllock  input8::numlock
input28::numlock   input8::capslock     input8::scrolllock
```
both input8 and input28 work interchangeably, the number varies with what usb port your keyboard(s) is/are in (i have 2 devices that read as keyboards, probably my mouse)

---

