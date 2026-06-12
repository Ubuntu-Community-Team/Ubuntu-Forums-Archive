---
title: "xorg joystick and amplify"
date: 2012-11-03
forum: General Help
---

### Post by ant2ne on 2012-11-03
my /usr/share/X11/xorg.conf.d/*joystick.conf contains the following
```

Section "InputClass"
        Identifier "joystick catchall"
        MatchIsJoystick "on"
        MatchDevicePath "/dev/input/event*"
        Driver "joystick"
Option "DebugLevel" "99"
# Right Buttons
# Button w(Up)/s(Down)
# Button a(Left)/d(Right)
Option "MapAxis1" "mode=accelerated keylow=38 keyhigh=40"
Option "MapAxis2" "mode=accelerated keylow=25 keyhigh=39"
# Right joystick: Like mouse
Option "MapAxis3" "mode=relative axis=+1x deadzone=5000"
Option "MapAxis4" "mode=relative axis=+1y deadzone=5000"
# Left joystick:
# axis X - Left/Right
# axis Y - Up/Down
Option "MapAxis5" "mode=relative deadzone=28000 keylow=100 keyhigh=102 axis=0.15key"
Option "MapAxis6" "mode=relative deadzone=28000 keylow=98 keyhigh=104 axis=0.15key"
#
Option "MapButton1" "key=10"
Option "MapButton2" "key=11"
Option "MapButton3" "key=12"
Option "MapButton4" "key=13"
Option "MapButton5" "key=14"
Option "MapButton6" "key=15"
# mouse button: left
Option "MapButton7" "button=1"
# mouse button: right
Option "MapButton8" "button=3"
# button "Space"
Option "MapButton9" "key=65"
# button "Enter"
Option "MapButton10" "key=36"
EndSection
```

I need to speed up this section
```
# Right joystick: Like mouse
Option "MapAxis3" "mode=relative axis=+1x deadzone=5000"
Option "MapAxis4" "mode=relative axis=+1y deadzone=5000"
```
And I'm looking at the amplify=parameter explained in a variety of sources, such as [http://manpages.ubuntu.com/manpages/karmic/man4/joystick.4.html](http://manpages.ubuntu.com/manpages/karmic/man4/joystick.4.html) and I've dones some googling looking for an example, But I can't find a good example of how to apply it.

I've tried 
Option "MapAxis3" "mode=relative axis=+1x deadzone=5000 amplify=10"
and
Option "MapAxis3" "mode=relative axis=+1x deadzone=5000" "amplify=10"
and a few other things and either nothing is amplified, or X crashes completely. Has anyone successfully used amplify?

---

### Post by ant2ne on 2012-11-05
bumpit

---

