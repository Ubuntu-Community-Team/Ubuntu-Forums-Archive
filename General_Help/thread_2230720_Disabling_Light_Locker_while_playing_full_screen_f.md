---
title: "Disabling Light Locker while playing full screen flash video"
date: 2014-06-20
forum: General Help
---

### Post by Sunbriel on 2014-06-20
I've spent hours searching for some sort of a solution to this everlasting problem with Linux. I think it's long past time for this to finally be fixed. But for now I'm just looking to receive a workaround. It's pretty obvious what I'm trying to achieve here looking at the thread title. I tend to watch full screen flash videos (Twitch.tv to be specific). But Light Locker doesn't get disabled, so my screen turns off every 10 minutes. A not-so-lovely workaround it to disable the Light Locker each time I watch Twitch, but it's annoying me to hell and back, doing this each time I watch a video. So is it possible to write some sort of script that would do all this automatically?

---

### Post by Sunbriel on 2014-06-23
Bump

---

### Post by monkeybrain20122 on 2014-07-07
I just noticed this problem on a Xubuntu 14.04 installation. Caffiene also no longer works.
[https://bugs.launchpad.net/ubuntu/+source/light-locker/+bug/1309744](https://bugs.launchpad.net/ubuntu/+source/light-locker/+bug/1309744)

Edited: I can confirm that the workaround of post #17 in the bug report works for gecko-mediaplayer in fullscreen  (hence gnome-mplayer) so it would work for video players  like vlc, parole and Totem as well. Not sure about flash as it may be different and I don't use flash very much.

so 
```
gksudo mousepad /usr/bin/xdg-screensaver
```

Choose 'show line number' from view and replace the ' ' in line 435 with 'xfce'

---

