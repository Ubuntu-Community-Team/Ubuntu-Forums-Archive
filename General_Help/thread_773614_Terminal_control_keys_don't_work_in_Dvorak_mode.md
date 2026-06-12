---
title: "Terminal control keys don't work in Dvorak mode"
date: 2008-04-29
forum: General Help
---

### Post by yang on 2008-04-29
I realize that this sounds like such a minor issue, but it's actually a huge annoyance, simply due to the frequency with which I use the ctrl-w key for backspacing over a word.

Before the upgrade from Ubuntu 7.10 to 8.04, I could use ctrl keyboard combos in Gnome Terminal (specifically, ctrl-w for erasing words) when in Dvorak layout mode (ctrl-w would actually use the 'w' in the qwerty layout, and not the 'w' in Dvorak layout/',' in the qwerty layout).

However, now after the upgrade, I find that these keys don't seem to work anymore.    ctrl-w seems to be the only broken thing.  ctrl-u (the Dvorak 'u') erases to beginning of line just fine, but ctrl-w just causes ',' to appear (the Dvorak 'w' is a qwerty ',').  Any hints?  Things still work fine in qwerty.

Thanks in advance for any answers!

---

### Post by highstead on 2008-05-03
out of curiosity if you hit the QWERTY equivalent while in dvorak layout does it work?  eg: ctrl+w->ctrl+,


If you don't mind me asking do you have any problems with default dvorak layout?  and how did you set that?  Mine seems to force me into QWERTY every boot even though i don't have qwerty as a layout, let alone have it set as tde default.

---

### Post by yang on 2008-05-03
No, the qwerty control keys didn't work either (I tried both, of course).

Sorry, I don't know about your latter problem.  (Perhaps you'll have better luck asking in a new thread?)

---

### Post by yang on 2008-05-10
Update - this is actually only broken for ctrl-w; I've updated the topmost post to reflect this.  And...bump!

---

### Post by raequin on 2010-04-20
Wow this is old, but I just performed a fresh install of 9.10 and am having a similar problem.  <Control>p in Dvorak gets me (reverse-i-search), as if I had pressed <Control>r.  The p-key in Dvorak is the r-key in QWERTY.  So all these commands work if I press the QWERTY key, but not the Dvorak, e.g. <Control>c or <Control>d.

Any help?

---

### Post by yang on 2010-04-20
Yeah now I'm seeing all ctrl shortcut keys behaving as if I were in qwerty layout.

---

### Post by selliott4 on 2010-06-13
For the last few years there have been similar issues with Dvorak for Fedora users.  I finally have my Fedora 13 system working they way I want it to (layout applies regardless of modifiers) for all applications after applying the patch attached to this gnome bug:
  [https://bugzilla.gnome.org/show_bug.cgi?id=589557](https://bugzilla.gnome.org/show_bug.cgi?id=589557)
Anyway, I just wanted to make sure you guys were aware of it.

---

