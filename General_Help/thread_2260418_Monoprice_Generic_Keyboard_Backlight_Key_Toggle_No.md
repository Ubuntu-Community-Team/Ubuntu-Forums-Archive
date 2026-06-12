---
title: "Monoprice Generic Keyboard Backlight Key Toggle Not Working"
date: 2015-01-11
forum: General Help
---

### Post by CaptainMikeRak on 2015-01-11
Basically, I have a Monoprice Generic Keyboard (which I suspect is actually a re-branded keyboard [hence why I don't know the model number of]) that has a blue backlight that is toggled on/off by pressing the "Scroll Lock" key, this functions perfectly in Windows but not in Ubuntu. I tried to research solutions to this but found fixes for particular models or laptops that don't seem to work for me. The volume keys and multimedia keys seem to work, so it looks like it's just the backlight. Before wiping my PC to install Ubuntu, I had it dual booted with Windows 7 and Ubuntu Studio (worked in Windows, not in Ubuntu Studio). If anyone can think of what command I should bind using the Custom Shortcuts (Settings Manage > Keyboard) or some other workaround it would be extremely helpful. Thanks to anyone that replies!

Additional: As far as I can tell it's NOT an issue with Ubuntu allowing USB power, that appears to work fine with my other devices.

---

### Post by Jonor on 2015-01-12
My 88 key Illuminant sk-020el keyboard blue backlight would switch on with :

```
xset led 3
```

I cannot remember for sure which of either, or possibly both of, would switch off :

```
xset led 3 off
```

```
xset led off
```

Don't use that keyboard regularly now and the keyboard won't work at all on Ubuntu Gnome 14.04 at the moment to test it.

See also [this thread]("http://forums.fedoraforum.org/showthread.php?t=235734") on Fedoraforum.org.

---

### Post by CaptainMikeRak on 2015-01-12
Thanks! This solved my issue! The backlight is finally working again. Using this I just set the "Screen Lock" key to on and the "Pause" key to off. This should make life a little easier. Thanks again for the help!

---

