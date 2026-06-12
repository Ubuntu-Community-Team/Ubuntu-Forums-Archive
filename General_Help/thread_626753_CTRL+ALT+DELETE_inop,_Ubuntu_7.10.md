---
title: "CTRL+ALT+DELETE inop, Ubuntu 7.10"
date: 2007-11-29
forum: General Help
---

### Post by Tristam Green on 2007-11-29
I reinstalled Ubuntu 7.10 about 2 weeks ago, following a severe flub I made with power-management.

Since then, Ctrl+alt+delete is not working.  It does show up in System>Preferences>Keyboard Shortcuts as the way to log me out, but it is not working.

Any ideas?  All help will be appreciated :-)

~Tristam

---

### Post by erginemr on 2007-11-29
Hello,

Can you use the red button to logout  on the top right corner of your desktop?

---

### Post by Tristam Green on 2007-11-29
yes, that works as does pressing the power button once.  also, ctrl+alt+L works to simply lock the screen.

CTRL+Backspace -> works, restarts X
CTRL+ALT+L -> works, locks screen
power button -> works, brings shutdown/restart menu up
red icon -> works, brings shutdown/restart menu up

---

### Post by erginemr on 2007-11-29
> **Tristam Green said:**
> I reinstalled Ubuntu 7.10 about 2 weeks ago, following a severe flub I made with power-management.

Since then, Ctrl+alt+delete is not working.  It does show up in System>Preferences>Keyboard Shortcuts as the way to log me out, but it is not working.

Any ideas?  All help will be appreciated :-)

~Tristam

When you assign another hotkey to the log out dialog, say Ctrl+Alt+P, via System>Preferences>Keyboard Shortcuts, does it work?

---

### Post by erginemr on 2007-11-29
> **erginemr said:**
> When you assign another hotkey to the log out dialog, say Ctrl+Alt+P, via System>Preferences>Keyboard Shortcuts, does it work?

Nevermind, When I do the same, mine does not work either. I think it has something to do with Compiz-Fusion. It should have its own shortcut settings somewhere else.

EDIT: It turns out that although Compiz-Fusion has its own settings as well, it does not deal with the one for the log out dialog. And for any new shortcut given via "Keyboard Shortcuts" to be put into effect, you need to logout and login back first.

---

