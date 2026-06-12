---
title: "Skype sound notifications generates neverending scratchy white noise sound."
date: 2013-11-10
forum: General Help
---

### Post by cdysthe on 2013-11-10
Hi,

I have Skype installed from the repos and it works well. However, there's one annoying problem. Every time there's a sound notification Skype starts generating a scratchy sound similar to white noise that never ends. I have to shut down Skype to get it to stop. Then Skype runs fine until there's another sound notification and the same thing happens again. If I turn off all sound notifications it works fine including making audio and video calls. If I install the version from the Skype site this problems goes away, but that version has other problems so I would like to figure out the notification sound problem in the version of Skype in the repos.

I'm running 13.10 on a Lenovo Thinkpad T430S.

---

### Post by wolvenreign2 on 2013-11-18
I have the same problem. I'm using the KDE desktop.

---

### Post by dkolars on 2013-11-19
Don't know if this is related to your problem, but maybe so?  I'm running Xubuntu 12.04.3.xxx  When I start Skype and make a test call, it is very static-y...  So, I've found a fix, but wondering why I have to do this every time???

I open Pulse Audio Volume Control (I put icon on bar so I could get to it easily!)... My "Built-In Audio" is set to "Analog Stereo Duplex".  I change it to "Analog Stereo Output", then close the Pulse Audio Window.  Making a Skype test call now, it still it static-y... So, re-open PA again, switch it back to "Duplex", close, and now Skype works fine.

Like I say, I have to do this nearly every time I run Skype... I don't use it often, but need it when I do!!  PIA... Hope this helps, and anyone know how to make the settings that seem "permanent" work the same every time?  TIA

dk

---

### Post by timgood on 2013-11-20
Try this:

```
gksu gedit /etc/pulse/default.pa
```

and changing the line: load-module module-udev-detect
to: load-module module-udev-detect tsched=0

Sound will be OK after reboot.

---

