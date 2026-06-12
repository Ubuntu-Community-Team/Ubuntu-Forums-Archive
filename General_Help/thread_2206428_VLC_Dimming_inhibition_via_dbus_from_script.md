---
title: "VLC Dimming inhibition via dbus from script"
date: 2014-02-19
forum: General Help
---

### Post by MikeBraxner on 2014-02-19
I start VLC with large playlists, i.e. TV-Series with many episodes, and watch ***part*** of an episode as a break from my work, just clearing out my head, then **pause** VLC to return to work ... thus being able to return to the episode and playlist just where I left off ... I love convenience. 

Any screen-dimming while watching my episodes tends to be annoying, but can be inhibited by VLC. However, VLC **keeps** inhibiting my power savings even if it is *just 'standing by'*, i.e. *paused*. I'm thus forced to either forgo the inhibition during VLC-play, or scarifies my power-savings during work, or shut down VLC and try to skip-find the right spot in the last watched episode ... not the relaxing intermission I'm aiming for.

So, I figured it should be possible to circumvent this with a simple script, which checks if VLC is *actually* playing anything, and if so, inhibit the screen dimming, and if not, just ignore it, which gives me the following script ...

```
#!/bin/bash
export DISPLAY=:0
delay=250
while true
do
    currStatus=`qdbus org.mpris.MediaPlayer2.vlc /org/mpris/MediaPlayer2 org.mpris.MediaPlayer2.Player.PlaybackStatus`
    if [ ${currStatus} == "Playing" ];then 
        qdbus org.freedesktop.ScreenSaver /ScreenSaver SimulateUserActivity > /dev/null
    fi
    sleep $delay
done
exit 0
```

Now, this script ***works just fine***, if it's run 'interactively' in a terminal window, but ***fails completely*** if it's detached, or run as a background process, or started at start-up, or called from another script, ... which is, of course, precisely what I'm looking for.  

I just can't figure out why the script isn't working properly, and how to fix it. 

Any bright ideas?

---

### Post by MikeBraxner on 2014-02-19
Cause of the problem ... side-by-side installation of qt4 and qt5.

With the proper path designation '/usr/lib/x86_64-linux-gnu/qt4/bin/qdbus', everything seems to work as its supposed to.

---

