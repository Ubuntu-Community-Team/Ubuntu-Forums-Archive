---
title: "Sound increments too large"
date: 2014-09-12
forum: General Help
---

### Post by gregory7 on 2014-09-12
A new install of 14.04. ):P

The sound output program is either deafening or quiet. Is there a program that allows me to increase or decrease the sound by an increment of 1, ie simply putting in the sound volume I require rather than using the sliding scale, which chooses increments of 5 by default? 

I tried to install Volti which describes itself as able to manually input the sound, but it doesn't open at all. Pulse doesn't have the capacity to input a volume manually.

Really I would like to increase or decrease the sound through the wheel on my mouse to the correct level, rather than deafening myself.

I am quite new to this, so maybe I am just being a little silly, but my ears are still ringing!!!!

Oh, my sound has to go through an external analogue device as the computer is old and the headphone socket is broken.

---

### Post by gregory7 on 2014-09-13
If no one is able to answer, please feel free to tell me why the question is stupid, or unreasonable. Am I the only person to notice that the sounds increments are large and that it is hard to reduce the volume with control? It seems that it is a choice of either slight sound or deafening, is this usual for headphones plugged into a usb headphone socket? :confused:

Does anyone else have an old computer with a broken headphones socket? 

And why does the program Volti fail to work when I install it from the software centre?

If I am in the wrong place, could someone kindly direct me to where I might get some feedback please? :)

---

### Post by ibjsb4 on 2014-09-14
As far as I know, there is still no solution for this.

[https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/871133](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/871133)

---

### Post by CantankRus on 2014-09-14
Click on the sound indicator and use the slider.
There are also various scripts around to increase sound in smaller steps.
eg this script will increase in 1% steps. When you use a script you lose the notification though.
Save as **volume-step** to your **~/bin** folder and make executable.
Create the folder **~/bin** if needed.
```
#!/bin/sh

usage="usage: $0 -c {up|down|mute} [-i increment] [-m mixer]"
command=
increment=1%
mixer=Master

while getopts i:m:h o
do case "$o" in
    i) increment=$OPTARG;;
    m) mixer=$OPTARG;;
    h) echo "$usage"; exit 0;;
    ?) echo "$usage"; exit 0;;
esac
done

shift $(($OPTIND - 1))
command=$1

if [ "$command" = "" ]; then
    echo "usage: $0 {up|down|mute} [increment]"
    exit 0;
fi

display_volume=0

if [ "$command" = "up" ]; then
    display_volume=$(amixer set $mixer $increment+ unmute | grep -m 1 "%]" | cut -d "[" -f2|cut -d "%" -f1)
fi

if [ "$command" = "down" ]; then
    display_volume=$(amixer set $mixer $increment- unmute | grep -m 1 "%]" | cut -d "[" -f2|cut -d "%" -f1)
fi
```

usage: volume-step {up|down}

When the script is placed in ~/bin you can just bind keys to run the commands 
**volume-step up** and **volume-step down**

---

### Post by gregory7 on 2014-09-16
Thank you I will try the go around - hopefully there will be an easier solution in the future :)

---

