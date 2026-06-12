---
title: "Screen resolution stuck at 50Hz"
date: 2006-11-10
forum: General Help
---

### Post by lwr on 2006-11-10
It's driving my a little crazy on my 17" monitor. I've tried everything I can find in the forums. I've reconfigured xserver-xorg many many times, I've edited xorg.conf in different ways, but I must be doing something wrong because my only option is still only 50Hz. I'm running at 1280x1024. When I change to 1024x768, I get options from 52Hz to 62Hz, but that's not exactly great either. I'm not sure what my screen's capable of, but I want to try things out. Please help me and my eyes!

---

### Post by ReaderRat on 2006-11-10
This may be what you need:
Resolution (& Refresh Rate) - HOWTO Change
         [http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

---

### Post by lwr on 2006-11-11
Thanks for your suggestion. I've tryed jsut about everything on that thread now. My xorg.conf file has the range 85-100Hz, but I still only get 50Hz as an option in System>Preferences>Screen Resolution. My screen's a Relisys TE770 by the way. Any suggestions as to why things aren't working would be highly appreciated. Thanks

Luke

---

### Post by OffHand on 2006-11-11
Did you happen to change it with the nvidia settings?

---

### Post by lwr on 2006-11-11
> **OffHand said:**
> Did you happen to change it with the nvidia settings?

Ah, I'd forgotten I had that. It lets me change it to 60Hz, but then if I go to Screen Resolution, it claims to be on 102Hz with no other options. However, it looks the same to me, and when I restart X, everything goes back to how it was.

---

### Post by juve on 2006-11-11
I'm on ATI and here's what helped me:

VRefresh2 and VertRefresh are probably useless.
try to increase the minimum values in for: **HSync2** and [B]HorizSync
[/B]```
#    HorizSync    30.0 - 98.0 # Monitor 1 stuck at 85 Hz
    HorizSync    70.0 - 98.0 # Monitor 1 "stuck" at 100 Hz
...
#    Option        "HSync2" "30-70" # Monitor 2 stuck at 85 Hz
    Option        "HSync2" "60-70"# Monitor 2 stuck at 100 Hz
```

---

### Post by OffHand on 2006-11-11
> **lwr said:**
> Ah, I'd forgotten I had that. It lets me change it to 60Hz, but then if I go to Screen Resolution, it claims to be on 102Hz with no other options. However, it looks the same to me, and when I restart X, everything goes back to how it was.

I had the exact same issues with nvidia settings too. What I did was a sudo dpkg-reconfigure xserver-xorg and I didn't change anything with nvidia settings after that. Somehow there are conflicts between them.

---

