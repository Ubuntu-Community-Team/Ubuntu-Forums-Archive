---
title: "prevent suspend while streaming audio only"
date: 2014-06-29
forum: General Help
---

### Post by icu12345 on 2014-06-29
So there are numerous ways to prevent the computer from sleeping when full screen video is playing (caffeine, which is now just a daemon and dosen't have a GUI anymore, the LightsOn script, etc.)

However, I often listen to streaming radio from tunein.com. That is just streaming audio and no picture, so consequently there is no fullscreen mode. Is there a way to prevent the computer from suspending when there is just audio playing?

Thanks for your help.

---

### Post by HermanAB on 2014-06-30
You need caffeine to prevent sleep, but you got to configure it right!
[http://www.webupd8.org/2012/05/2-ways-to-temporarily-disable.html](http://www.webupd8.org/2012/05/2-ways-to-temporarily-disable.html)
[https://unix.stackexchange.com/questions/52643/how-to-disable-auto-suspend-when-i-close-laptop-lid](https://unix.stackexchange.com/questions/52643/how-to-disable-auto-suspend-when-i-close-laptop-lid)

---

### Post by icu12345 on 2014-06-30
Thanks. However, since version 2.7 caffeine has no GUI (it's just a daemon) so there is no way to configure it: [http://www.omgubuntu.co.uk/2014/05/stop-ubuntu-sleeping-caffeine](http://www.omgubuntu.co.uk/2014/05/stop-ubuntu-sleeping-caffeine)

Which is why I was wondering if there is a better way to do it...

---

### Post by HermanAB on 2014-07-01
OK, wasn't aware of that development.  If you are truly desperate, then you could get the old Caffeine version's source and compile it yourself.

Otherwise, you need to stop suspend using one of the methods in the delay screensaver procedure below:
[https://raw.githubusercontent.com/hotice/lightsOn/master/lightsOn.sh](https://raw.githubusercontent.com/hotice/lightsOn/master/lightsOn.sh)

The simplest method of all, is to simulate what a user is doing: Wiggle the mouse using the xdotool every 60 seconds.
[http://tuxradar.com/content/xdotool-script-your-mouse#null](http://tuxradar.com/content/xdotool-script-your-mouse#null)

Here is a wiggle script':
#! /bin/bash
STATUS=1
while [ "${STATUS:-null}" != null ]; do
 STATUS=`pgrep firefox`
 xdotool mousemove_relative -- -1 -1
 sleep 1
 xdotool mousemove_relative 1 1
 sleep 1
done

It will keep wiggling the mouse pointer while firefox is running.  Modify at your peril...

---

### Post by icu12345 on 2014-08-16
Thanks! Sorry for the late reply ;)
I used your script at first but today I finally made some modifications:

```

#! /bin/bash
State=1
while [ State != 0 ]; do


if grep -q RUNNING /proc/asound/card*/*p/*/status 2>&1; then
    let State=1
    #echo "Playing"
    xdotool mousemove_relative -- -1 -1
    sleep 10m
    xdotool mousemove_relative 1 1
    sleep 10m
else
    let State=0
    #echo "Idle"
fi


done

```

The scrips uses now procfs for ALSA and detects if audio is being played. Otherwise, if you do not stream any audio but leave your browser open the script would still prevent the system from suspending. I also modified the wiggle time. My system suspends after 30 mins of inactivity, so the script wiggles the mouse every 10 minutes which makes the wiggling virtually undetectable ;)

---

