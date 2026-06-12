---
title: "DPMS Standby is totally WONKY, unreliable - Kubuntu 18.04"
date: 2018-08-02
forum: General Help
---

### Post by karnival8 on 2018-08-02
It's been weeks and I cannot figure this out so I decided to post here. Something is resetting my DPMS to 0 0 0. I have to manually set it back to fix the problem and a couple hours later it will be reset. There is an app somewhere that is doing this but I have no idea how to hunt it down. 

I have a dual GPU Nvidia 960's. I suspect one of the following apps may be the culprit but don't know how to verify: Teamviewer, Telegram, Chrome. 
This is an Ubuntu build with KDE added after (not originally Kubuntu). 

Also, I have noticed that the KDE power settings seem to be so unreliable that I just end up setting this all through the CLI which is weird because on my laptop and other machines it seems to work fine. 

Another issue (which I don't care about but could be a clue) is that the system will not recover from Suspend. I don't intend on using Suspend ever but if it is set and I wake the machine I get a black screen with a cursor only. Have to hard reset to get the machine back. 

This is my xset -q AFTER I notice this reset has occurred:

```
Keyboard Control:
  auto repeat:  on    key click percent:  0    LED mask:  00000002
  XKB indicators:
    00: Caps Lock:   off    01: Num Lock:    on     02: Scroll Lock: off
    03: Compose:     off    04: Kana:        off    05: Sleep:       off
    06: Suspend:     off    07: Mute:        off    08: Misc:        off
    09: Mail:        off    10: Charging:    off    11: Shift Lock:  off
    12: Group 2:     off    13: Mouse Keys:  off
  auto repeat delay:  600    repeat rate:  25
  auto repeating keys:  00ffffffdffffbbf
                        fadfffefffedffff
                        9fffffffffffffff
                        fff7ffffffffffff
  bell percent:  50    bell pitch:  400    bell duration:  100
Pointer Control:
  acceleration:  150/10    threshold:  4
Screen Saver:
  prefer blanking:  yes    allow exposures:  yes
  timeout:  0    cycle:  600
Colors:
  default colormap:  0x20    BlackPixel:  0x0    WhitePixel:  0xffffff
Font Path:
  /usr/share/fonts/X11/misc,/usr/share/fonts/X11/Type1,built-ins
DPMS (Energy Star):
  Standby: 0    Suspend: 0    Off: 0
  DPMS is Disabled

```

And then after I manually correct the problem:
```
Keyboard Control:
  auto repeat:  on    key click percent:  0    LED mask:  00000002
  XKB indicators:
    00: Caps Lock:   off    01: Num Lock:    on     02: Scroll Lock: off
    03: Compose:     off    04: Kana:        off    05: Sleep:       off
    06: Suspend:     off    07: Mute:        off    08: Misc:        off
    09: Mail:        off    10: Charging:    off    11: Shift Lock:  off
    12: Group 2:     off    13: Mouse Keys:  off
  auto repeat delay:  600    repeat rate:  25
  auto repeating keys:  00ffffffdffffbbf
                        fadfffefffedffff
                        9fffffffffffffff
                        fff7ffffffffffff
  bell percent:  50    bell pitch:  400    bell duration:  100
Pointer Control:
  acceleration:  150/10    threshold:  4
Screen Saver:
  prefer blanking:  yes    allow exposures:  yes
  timeout:  0    cycle:  600
Colors:
  default colormap:  0x20    BlackPixel:  0x0    WhitePixel:  0xffffff
Font Path:
  /usr/share/fonts/X11/misc,/usr/share/fonts/X11/Type1,built-ins
DPMS (Energy Star):
  Standby: 300    Suspend: 0    Off: 0
  DPMS is Enabled
  Monitor is On


```

---

