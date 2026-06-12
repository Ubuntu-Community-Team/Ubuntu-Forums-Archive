---
title: "nvidia and compiz choppy (halfway fixed)"
date: 2008-04-28
forum: General Help
---

### Post by crispy_chunks on 2008-04-28
I just installed 8.04 and im pretty happy with it so far. My only problem is that compiz has been running a bit choppy. Window minimizations/maximizations and super-tapping is drawn really slow :( To fix that ive tried the following:

1. Added to xorg.conf in Device section:
```
Option         "AllowGLXWithComposite" "1"
Option         "AddARGBGLXVisuals" "1"
Option         "Coolbits" "1"
Option         "TripleBuffer" "1"
Option         "DamageEvents" "1"
Option         "BackingStore" "1"
Option         "InitialPixmapPlacement" "2"
```

2. using this little powermizer hack (got a 8400GS): [http://ubuntuforums.org/showthread.php?t=594593&page=2](http://ubuntuforums.org/showthread.php?t=594593&page=2)

These things didnt help the performance to be at a noticable good level (tho the hack solves alot of performance problems when everything is running as it should)

3. This fixed the low performance: sudo apt-get install xserver-xorg

Now all effects are nice and smooth and fast! YAY! But my problem is that now nvidia-settings is not working - you do not appear to be using the nvidia x driver - it says. Which is probably true because when i start compiz the console outputs: nVidia: not present - enabling Xgl with nvidia drivers. Also my keyboard layout changed from Danish to english, which makes me think that xorg.conf is not actually being used - but maybe another weird "xorg-xgl-conf" or something like that....

Can anyone shed some light on how to get nvidia-settings working again? I want to be using xserver-xgl because it make all the effects smooth :p

(im using nviodia settings to control my 2 monitor setup, projector and monitor)

---

### Post by Zorael on 2008-04-28
> **crispy_chunks said:**
> 3. This fixed the low performance: sudo apt-get install xserver-xorg

Now all effects are nice and smooth and fast! YAY! But my problem is that now nvidia-settings is not working - you do not appear to be using the nvidia x driver - it says. Which is probably true because when i start compiz the console outputs: nVidia: not present - enabling Xgl with nvidia drivers. Also my keyboard layout changed from Danish to english, which makes me think that xorg.conf is not actually being used - but maybe another weird "xorg-xgl-conf" or something like that....

Can anyone shed some light on how to get nvidia-settings working again? I want to be using xserver-xgl because it make all the effects smooth :p

(im using nviodia settings to control my 2 monitor setup, projector and monitor)
xserver-xgl makes Compiz use software rendering instead of hardware, so if I were you I'd work towards getting it to work without it.

These next bunch of commands assume that you have an Nvidia X driver installed (even if not in use).
```
$ sudo su
# aptitude purge xserver-xgl nvidia-settings+
# mv /etc/X11/xorg.conf /etc/X11/xorg.backup0804
# dpkg-reconfigure xserver-xorg    # set your keyboard layout and stuff
# nvidia-xconfig -d 24 --add-argb-glx-visuals --allow-glx-with-composite --coolbits --damage-events
```
Start compiz with the --loose-binding argument for extra performance on Nvidia cards (and --ignore-desktop-hints if you're running KDE).
```
$ compiz --replace --loose-binding &
```

---

### Post by spinanicky on 2008-05-03
Easier than doing all that.... (I think)..) Simply use EnvyNG to install your grafic card, then reboot ctrl+alt+backspace, then launch fusion-icon, in the top right corner (taskbar) you should see a blue box with an arrow, clicl on it => compiz-options=>lose bindings... fixed it for me :D
Hope that helps

---

### Post by crispy_chunks on 2008-05-03
Thanks for the replies.

Zorael, i did 

```
nvidia-xconfig -d 24 --add-argb-glx-visuals --allow-glx-with-composite --coolbits --damage-events
```

However, the --coolbits option wasnt supported for some reason (i also the the other things you suggested), but none of it improved performance significantly to notice a positive change.

spinanicky, i am using envyng to install my driver (169.xx), but i dont see any blue icon? Anyways, im running compiz with --loose-binding always, but same problem :(

As of now when i dont use xserver-xgl gnome menus take ~1 sec to open and effects are very slow to respond to user interactions, but with xserver-xgl everything is running very nice and smooth.

---

### Post by crispy_chunks on 2008-05-03
Little extra info, the cube effect is running smoother without xserver-xgl along with some other effects, for example expose, but menus and effects lag behind userinteractions with +1 secs consistently, plus there are small graphical glitches when mousing over a menu item; some of the letters will have a slightly darker shade of highlight within encircled spaces of the letters. Like the space in an e or an o or a g or a b (if you get what i mean by this 'encircled space'

---

### Post by drhabber on 2009-11-26
> **crispy_chunks said:**
> I just installed 8.04 and im pretty happy with it so far. My only problem is that compiz has been running a bit choppy. Window minimizations/maximizations and super-tapping is drawn really slow :( To fix that ive tried the following:

1. Added to xorg.conf in Device section:
```
Option         "AllowGLXWithComposite" "1"
Option         "AddARGBGLXVisuals" "1"
Option         "Coolbits" "1"
Option         "TripleBuffer" "1"
Option         "DamageEvents" "1"
Option         "BackingStore" "1"
Option         "InitialPixmapPlacement" "2"
```

[...]


Finally my Compiz is in tip-top shape (nVidia 8600) :). Thanks !

---

