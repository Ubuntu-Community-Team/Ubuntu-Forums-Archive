---
title: "HP w2207h not working under 18.10"
date: 2019-01-07
forum: General Help
---

### Post by botris on 2019-01-07
Hi,

I have a dual monitor setup with a Sapphire Nitro+ MD Radeon RX 580 graphics card.
Both monitors are connected via HDMI.
The second monitor is an (old) HP w2207h, which I can see when booting under Windows or grub, but not under Ubuntu.
I've tried another monitor (iiyama) on the same HDMI cable and port and then the dual monitor setup works. So I think the drivers and all must be ok.

It looks like a software off switch, in the sense that if I boot to Ubuntu then monitor get's turned off. Then booting into Windows it's still turned off untill I press the power button.
While if I was to reboot in Windows the monitor stays on.
Also just now I noticed for the first time that if I press the power button on the HP there is a small flicker on the main (dell) monitor. Pressing the power button after did not replicate the flicker.

Output of *xrandr* is:
```
Screen 0: minimum 320 x 200, current 2560 x 1440, maximum 16384 x 16384
DisplayPort-0 disconnected (normal left inverted right x axis y axis)
DisplayPort-1 disconnected (normal left inverted right x axis y axis)
HDMI-A-0 disconnected (normal left inverted right x axis y axis)
HDMI-A-1 connected primary 2560x1440+0+0 (normal left inverted right x axis y axis) 553mm x 311mm
```

---

