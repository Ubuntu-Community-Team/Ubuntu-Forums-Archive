---
title: "can no longer login to GUI after x11vnc faff"
date: 2018-11-17
forum: General Help
---

### Post by steve234 on 2018-11-17
Morning all,

I think I have accidentally created a "headless" box out of an old PC I use with the GUI from time to time!


I have a Lububtu box (not server) which I mostly use as a Nextcloud instance, but I do use the GUI from time to time.

It usually has a keyboard / mouse / monitor connected, but not always


Yesterday, I ssh'd in to manually copy some files to Nextcoud as the sync client wasn't working. This got me thinking about vnc so I could re-launch the client and visually check it. 


After much (much) faff and failing to get anything other than a grey screen with various VNC servers (I tried various methods to setup my conf files to use LXDE) I settled on setting up x11vnc using the guide here:


[https://gist.github.com/mgeeky/8e068b978095053b100ad49a6e9559d8](https://gist.github.com/mgeeky/8e068b978095053b100ad49a6e9559d8)

All steps were followed. In particular, my xorg.conf file was amended to be as per the tutorial:

```
[COLOR=#24292E][FONT=Consolas]Section "Device"[/FONT][/COLOR]
    Identifier  "Configured Video Device"
    Driver      "dummy"
EndSection

Section "Monitor"
    Identifier  "Configured Monitor"
    HorizSync 31.5-48.5
    VertRefresh 50-70
EndSection

Section "Screen"
    Identifier  "Default Screen"
    Monitor     "Configured Monitor"
    Device      "Configured Video Device"
    DefaultDepth 24
    SubSection "Display"
    Depth 24
    Modes "1920x1080"
    EndSubSection [COLOR=#24292E][FONT=Consolas]EndSection[/FONT][/COLOR]
```



All was well with the vnc connection (x11vnc was "listening" an I could connect via a vnc viewer) however only got a black screen. Albeit with a proper cursor this time.


I read somewhere that lightdm / lightlocker may have "locked" my display - and x11vnc wouldn't like that so...


I decided enough was enough and when I returned home I re-conneced my monitor / mouse / keyboard so I could visually check it and turn off screen locking if required.


On booting, I get a brief cli login propmt, which then goes to a black screen after a few seconds (even in "recovery" mode). No LXDE GUI.

I can still ssh in fine, and my Nextcloud instance is running fine, but I can't use the GUI at all.


Any help would be appreciated.


Steve

---

### Post by steve234 on 2018-11-18
Sorry for the bump - I think this question would be better off in the "Desktop Environments" section - is it possible for it to be moved.

---

### Post by HermanAB on 2018-11-18
Well, you easily go back to X11 defaults, by deleting (or renaming) xorg.conf.

---

### Post by steve234 on 2018-11-18
Cheers,

Will the system re-generate an xorg.conf file on boot? I'm pretty sure there was something there before I messed with it.

(I'll be making .backup copies of stuff I mess with from now on)

---

### Post by steve234 on 2018-11-19
Worked a treat - marked solved

---

