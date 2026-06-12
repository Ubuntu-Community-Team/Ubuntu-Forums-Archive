---
title: "Screen does not go to standby or suspend on startup or after video"
date: 2014-05-29
forum: General Help
---

### Post by Jumbs on 2014-05-29
I am running 14.04 with the Gnome 3 shell environment.
If it matters, i have dual monitors, along with a nvidia card and driver. 

When the system is logged in, the screen will never blank or turn off, unless i manually tell it to with xset.
in 13.10, i fixed this with an xset command that ran on startup 

```
xset dpms 600 600
```

However on upgrade, this no longer fully works.
When something like VLC disables the screen saver, the system does not re-enable it afterwards.

I have to constantly keep firing off the 'xset dpms 600 600' in case it has been disabled again. 


xset q returns:
 ```
  
Keyboard Control:
auto repeat:  on    key click percent:  0    LED mask:  00000000
XKB indicators:
 00: Caps Lock:   off    01: Num Lock:    off    02: Scroll Lock: off
 03: Compose:     off    04: Kana:        off    05: Sleep:       off
 06: Suspend:     off    07: Mute:        off    08: Misc:        off
 09: Mail:        off    10: Charging:    off    11: Shift Lock:  off
 12: Group 2:     off    13: Mouse Keys:  off
  auto repeat delay:  500    repeat rate:  33
  auto repeating keys:  00ffffffdffffbbf
                        fadfffefffedffff
                        9fffffffffffffff
                        fff7ffffffffffff
  bell percent:  50    bell pitch:  400    bell duration:  100
Pointer Control:
  acceleration:  2/1    threshold:  4
Screen Saver:
  prefer blanking:  yes    allow exposures:  yes
  timeout:  0    cycle:  0
Colors:
  default colormap:  0x20    BlackPixel:  0x0    WhitePixel:  0xffffff
Font Path:
  /usr/share/fonts/X11/misc,/usr/share/fonts/X11/Type1,built-ins
DPMS (Energy Star):
  Standby: 0    Suspend: 0    Off: 0
  DPMS is Enabled
  Monitor is On

```

---

