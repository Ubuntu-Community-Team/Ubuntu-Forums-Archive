---
title: "Suddenly undetected soundcard"
date: 2007-02-05
forum: General Help
---

### Post by dckirba on 2007-02-05
Hello all,

I've been using Dapper at work for a while and have been having a ball. Anyways, today, I logged out and logged back in after installing a new GDM theme and the Volume Control icon in the system tray had an x on it.

Upon clicking, I get this error

> The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu.

The funny thing is, I get the startup sound when I restart the computer and the login screen pops up. Also, windows doesn't seem to have a problem.

Do I have to reinstall the sound plugins? If so, which ones?

I don't know if this helps, but the output of cat /proc/asound/cards was 

```
david@david:~$ cat /proc/asound/cards
0 [V8233A         ]: VIA8233A - VIA 8233A
                     VIA 8233A with ALC200,200P at 0xe400, irq 12
david@david:~$
```

Thanks in advance for your help. This isn't a life threatening situation, but I do enjoy my music and can work a whole lot better when I can cut out distracting noise :grin: 

[COLOR="Red"]**EDIT:**[/COLOR] Problem resolved [http://ubuntuforums.org/showthread.php?t=354506]("http://ubuntuforums.org/showthread.php?t=354506")

Cheers all, 
David

---

