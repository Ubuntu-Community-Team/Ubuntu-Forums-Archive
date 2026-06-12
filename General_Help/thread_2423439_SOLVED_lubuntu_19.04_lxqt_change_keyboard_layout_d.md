---
title: "SOLVED: lubuntu 19.04 lxqt change keyboard layout does not persist"
date: 2019-07-23
forum: General Help
---

### Post by minimalisp on 2019-07-23
In *Menu->Preferences->LXQt settings->Keyboard and Mouse->Keyboard Layout  *I can't get the "keys to change layout" setting to persist so I can conveniently switch between the *English, US* and the *English, **US International with dead keys* keyboards.

Edit 1:

Ok, I'm now into xkb; perhaps the switch doesn't work because (a) *English (US, Int'l)* is just a flavor of *English (US)* and, maybe (b) my choice of change-layout-key was right-alt, which might conflict with level3(ralt_switch) in /usr/share/X11/xkb/symbols/us :-( .

Annoying that LXQt makes it look simpler, though.

SOLVED: After reboot *Menu->Preferences->Fcitx Configuration* does not open the first time you click it ... which led me to believe that it was not installed or deprecated.  It works; you just have to click it a second time :-/ .

Also pay attention to using *lxqt-sudo* to launch graphical programs as *sudo*.

```
$ lxqt-sudo gui-program
```

(also [RTFM]("https://manual.lubuntu.me/index.html") -- it's short, succinct and sometimes essential.)

---

