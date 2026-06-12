---
title: "Mouse Acceleration"
date: 2013-09-02
forum: General Help
---

### Post by bisurge on 2013-09-02
Hello,
In **13.04**, the mouse settings have been consolidated into one slider. I want fast sensitivity but no mouse acceleration. Is there any way to do this? I searched the forums and there is no real set answer.

Thanks in advance!

---

### Post by CatKiller on 2013-09-02
That's exactly my preference, too. Can't check the settings because I'm on my phone & I've got a driving lesson in a tick, but I'll post them later if I get a chance. One of gconf-editor or dconf-editor had a key for the setting you're found; you'll want to set that to default since otherwise you get some annoying latency. Then in xorg.conf you can put in two settings for the scaling numerator and denominator. For a fast movement you'll want this ratio to be greater than 1. There's another setting for turning off the acceleration. You can fiddle with the settings from the command line to find the settings you're happy with before you put them in xorg.conf. You might find all the details yourself before I get a chance to come back to it.

---

### Post by CatKiller on 2013-09-02
The section I've got in my xorg.conf is ```
Section "InputDevice"
    Identifier "Logitech USB Gaming Mouse"
    Driver    "evdev"
    Option    "SampleRate"        "1000"
    Option    "Resolution"        "2000"
    Option     "AccelerationProfile"    "-1"
    Option    "AccelerationNumerator"    "3"
    Option    "AccelerationDenominator" "2"
EndSection
```
You might need to adjust them to correspond to your mouse. I found the ratio I was after with ```
xset m 3/2 0
``` **man xset** and **man xorg.conf** can tell you more about your options.

---

### Post by bisurge on 2013-09-02
> **CatKiller said:**
> The section I've got in my xorg.conf is ```
Section "InputDevice"
    Identifier "Logitech USB Gaming Mouse"
    Driver    "evdev"
    Option    "SampleRate"        "1000"
    Option    "Resolution"        "2000"
    Option     "AccelerationProfile"    "-1"
    Option    "AccelerationNumerator"    "3"
    Option    "AccelerationDenominator" "2"
EndSection
```
You might need to adjust them to correspond to your mouse. I found the ratio I was after with ```
xset m 3/2 0
``` **man xset** and **man xorg.conf** can tell you more about your options.
Wow, that seems awfully complicated for such a basic setting. Do I have to change these settings for every mouse I have, since the identifier is the mouse name? Thanks for the information!

---

### Post by CatKiller on 2013-09-03
The Identifier is mostly for my benefit; I believe it only has to be a unique name in xorg.conf, and those are the settings for that particular mouse because of the resolution line.

A couple of lines in a config file doesn't seem too complicated to me, but I agree that all of the changes in Gnome 3 that take away the sensible means of configuration are annoying. See also printers, networking, Bluetooth, theming, fonts, and so on.

---

### Post by bisurge on 2013-09-03
Alright so now the problem is that I can't find the xorg.conf file in my /etc/X11 folder.

---

### Post by CatKiller on 2013-09-03
It's not there by default any more, but it will be used if you put one there. It's possible that you need more in there than just the Input Section (I have the other Sections anyway for other reasons) but I'm sure the manpage will tell you, or that you can find a skeleton config somewhere.

Shout if you get stuck and I'll post the rest of my xorg.conf.

EDIT: If it all goes pear-shaped, Ctrl-Alt-F1 will get you a command line without X, and nano is a nice command-line text editor.

---

