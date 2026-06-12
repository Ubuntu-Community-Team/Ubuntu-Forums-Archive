---
title: "Screen Fades After 5 Mins Before Screensaver"
date: 2006-11-30
forum: General Help
---

### Post by MikeDC on 2006-11-30
Hi there!

I'm running Edgy on a Thinkpad R60 and it's working BRILLIANTLY.  I'm using Beryl as well.

The only annoyance is the fact that the screen will fade to black after about 3-5 minutes and I can't find where to change this setting... I've tried power settings, etc. everything.  I can't stop/extend this fade.  In order to get the screensaver to work I need to make the screensaver start under that timeframe otherwise it won't start.

Anyone know where this fade setting/timer can be adjusted?

Thanks!

---

### Post by Feanor on 2006-12-03
I've the same problem and my only luck is that the time is about 10 minutes, after that... THE BLACK! Uff.. Is annoying to see films in this way...

---

### Post by cbudden on 2006-12-03
Its something to do with dpms.  If you add the following to your xorg.conf, you should find it will not turn off :

```


Section "ServerFlags"
Option "blank time" "0"
Option "standby time" "0"
Option "suspend time" "0"
Option "off time" "0"
EndSection


```

---

