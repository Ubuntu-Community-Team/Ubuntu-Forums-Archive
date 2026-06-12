---
title: "X server problem"
date: 2006-11-01
forum: General Help
---

### Post by ivasic on 2006-11-01
I installed Edgy yesterday and I'm still having issues with my monitor.
My monitor is Philips 170S4 17" TFT and I was successfully using it with Dapper and Breezy so far.

Edgy won't allow me refresh rate lower than 75Hz. My default should be 1280x1024@60Hz.

I've tried everything: added modeline to xorg.conf, added horizontal and vertical-sync values, experimented with those values but somehow I get the impression that anything I change in xorg.conf does not affect my X session. Earlier, I remember that playing around with these settings at least gave me some changes in X, now I can't trigger it.
I even put some stupid values for "DisplaySize" in Monitor section (which should change my resolution from 96dpi to something else) but that didn't seem to have any effect. This was surely working in dapper, so what's wrong now?

---

### Post by CatKiller on 2006-11-01
Putting ```
Option    "IgnoreEDID"    "true"
``` in your Device section will cause X to ignore what your monitor is telling it, if that's what you want.

---

### Post by ivasic on 2006-11-01
Thanks for your reply, but unfortunately that does not help either.
X server is ignoring every option I set in monitors section (at least it appears so).

Here's my section:
```
Section "Monitor"
    Identifier     "Philips 170S4"
    Option    "IgnoreEDID "true"
    HorizSync       56.0 - 76.0
    VertRefresh     30.0 - 82.0
# 1280x1024 @ 60.00 Hz (GTF) hsync: 63.60 kHz; pclk: 108.88 MHz
#    Modeline "1280x1024_60.00"  108.88  1280 1360 1496 1712  1024 1025 1028 1060  -HSync +Vsync
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "nVidia fx5700LE"
    Driver         "nvidia"
EndSection

```

---

### Post by CatKiller on 2006-11-01
I think that option should go in the **Device** section. And don't forget to restart your X server (**Ctrl-Alt-Backspace**) for any changes to take effect.

EDIT: And it might be "IgnoreEDIDFreqs" - I'm not sure because I've never had to use it.

---

### Post by ivasic on 2006-11-01
Neither option works. Putting 'edid' stuff in device section makes my box unable to start X. Monitor section, however, accepts this stuff but doesn't make any difference.

Weird thing is that it worked allright in Dapper but the same X config won't in Edgy.

---

### Post by CatKiller on 2006-11-01
> **ivasic said:**
> Neither option works. Putting 'edid' stuff in device section makes my box unable to start X.

I'm not sure exactly what else you were expecting. You've put some random stuff into your configuration, and then turned off the safety catch that stops you breaking anything.

I don't really understand why you're so set on having a box say one number rather than another. It's not like it really means anything on an LCD monitor, as I understand it.

> Monitor section, however, accepts this stuff but doesn't make any difference.

I think you'll find it's the latter statement that causes the former.

---

### Post by ivasic on 2006-11-01
Ehm, my TFT monitor supports resolution of 60Hz only. Edgy won't let me change it to 60Hz. The only option I have is 75Hz, now I you have any other tip on how to change resolution to 60Hz to prevent my monitor going to hell just shoot. Do you understand me now?

BTW, I'm not putting random stuff in xorg - I've experimented different settings but X session just don't make a difference at all.

---

