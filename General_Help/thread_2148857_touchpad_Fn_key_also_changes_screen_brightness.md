---
title: "touchpad Fn key also changes screen brightness"
date: 2013-05-26
forum: General Help
---

### Post by chellrose on 2013-05-26
On my Fujitsu Lifebook running Xubuntu 12.04, if I hit Fn+F4 (to enable/disable the touchpad), it also changes the screen brightness.  I can also change the screen brightness using the actual brightness hotkeys (F6 and F7), so it's not a major issue, but I was just curious if there is a known workaround to make Fn+F4 *only* control the touchpad.

Fn+F4 can change the brightness up or down -- it appears to go in the direction that corresponds to the last intentional brightness change.

Thanks :)

---

### Post by ohnonot on 2013-05-29
funny, my brightness keys are fn+f4/f5 - 

wouldn't it be easier to map the touchpad on/off key to a different combination?

i always map something to ctrl+alt+z (or y on some keymaps) because it's easy to press with one hand. and close to the touchpad.

---

### Post by mikeym on 2013-05-29
You can see what's happening with a command *xev* which will show you what keypresses are being generated when you press Fn+F4. You can remap them using *xmodmap* see [here]("http://askubuntu.com/questions/24916/how-do-i-remap-certain-keys") for a good description howto (see the winning answer).

I think some systems have some shortcuts hardcoded to certain function keys, so that's worth considering when diagnosing the issue.

---

### Post by ohnonot on 2013-05-29
> **mikeym said:**
> I think some systems have some shortcuts hardcoded to certain function keys, so that's worth considering when diagnosing the issue.
you mean the laptop itself, not the operating system?

---

