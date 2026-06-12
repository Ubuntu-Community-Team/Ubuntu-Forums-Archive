---
title: "Ubuntu Studio Volume???"
date: 2008-06-19
forum: General Help
---

### Post by screaminfakah on 2008-06-19
I cant figure out what I need to do to make any "louder" volume adjustments.
It sounds like I am listening to 2 watt jam box when cranked in amarok or any other program.
I have searched google and the forums with no luck.  There has been alot of volume prolems but none that help me.

How do you turn it up?

I have no speaker icon in the task bar and in options it doesn't give an option to turn up.

the studio version is pretty cool so far but the volume dillema really sucks.

Thanks guys

---

### Post by forestpixie on 2008-06-19
Try using the mixer from a terminal

```
alsamixer
```

---

### Post by lieryan on 2008-06-19
When I have volume problems, I usually check these places first:
1. The speaker's volume button (you know where)
2. The OS' volume control ([1])
3. The program's volume control (you know where)

[1] This seems to be you may use the alsamixer from terminal, or (I've never used Ubuntu Studio so it might be different) right click on a Panel -> Add to Panel -> Volume Control

---

### Post by screaminfakah on 2008-06-19
Every level I could find was cranked and I was hearing audio just very low.

Thanks for the command Forestpixie!

I really find it hard to believe that this distribution is geared towards Studio software and doesn't have the Alsa Mixer accessible through an icon on the desktop by default??  Strange.

Thanks again.

---

