---
title: "Logitech G1 how to enable back button?"
date: 2008-02-21
forum: General Help
---

### Post by NinjaZec on 2008-02-21
i am used to use this button, but it doesn't work in ubuntu, so i am asking how to enable it
here is a pic:
[IMG]http://i39.photobucket.com/albums/e159/Ffrreennkk/First/Logitech_G1.png[/IMG]

---

### Post by fyo on 2008-02-21
You'll almost certainly need to manually edit your xorg.conf file. More on that in a bit...

Open a console and run

```
$ xev
```

This spawns a new little window with a square drawn in it. When the mouse cursor is over that window, any mouse events captured by X and dumped to the console. This allows you to see if anything is actually triggered, when you press your back button. If there is a ButtonPress and ButtonRelease event, then you know that it's working and you "just" need to configure the button to do whatever it is you want it to do.

More likely, you'll need to configure your mouse properly in xorg.conf. Use your favorite editor (I'm a vim guy, but if you're new to this stuff, pico or nano is probably easier):

```
$ cp /etc/X11/xorg.conf ~/xorg.conf.backup
$ sudo nano /etc/X11/xorg.conf
```

Always make a backup of xorg.conf before messing with it!

Find the section "InputDevice" that contains the mouse information. You could post what yours says here or you could just try the following:

```
Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "Buttons" "7"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "false"
    Option         "ButtonMapping" "1 2 3 6 7"
EndSection
```

Note the number of "buttons". If you have a scroll wheel, it counts as TWO BUTTONS (one scroll up, one down), plus a THIRD if it also acts as a normal (typically middle) button. So a normal mouse with a left and a right button, plus a scroll wheel which also acts a a middle button, has 5 buttons.

---

