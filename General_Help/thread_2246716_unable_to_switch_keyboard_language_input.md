---
title: "unable to switch keyboard language input"
date: 2014-10-02
forum: General Help
---

### Post by petran79 on 2014-10-02
Hallo, 

I am using Ubuntu 14.04 with Classic Gnome Desktop
 I have 3 languages in language indicator applet (English, Greek, German)

Lately I've been unable to switch languages as I type. I used the Alt+Left Shift command and I can register it in the keyboard settings.
I did the same in dconf-editor and ibus is running.

But nothing happens with either combination of Shift, Crtl or Alt. I can change the language only if I click the indicator with the left mouse button.
But not when I enter a keyboard command. 

In Unity keyboard works though, only in Gnome do I get this issue

Any advice would be helpful.

---

### Post by Jonor on 2014-10-04
Try a simpler key choice such as (using Tweak Tool > Typing > Switching to another layout) using scroll lock.

---

### Post by petran79 on 2014-10-16
it was another issue. Had to reinstall dbus, now language-switch works fine.
thing is, this worked for a while, then today I get the same issue!
had to reinstall dbus again for it to work.

It seems Ubuntu has quite some issues during boot time. Had to add also sudo alsa force-reload because soundcard wouldnt be recognized half the time.

---

