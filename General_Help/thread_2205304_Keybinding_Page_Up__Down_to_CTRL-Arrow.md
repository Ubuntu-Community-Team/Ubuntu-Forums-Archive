---
title: "Keybinding Page Up / Down to CTRL-Arrow"
date: 2014-02-13
forum: General Help
---

### Post by majest on 2014-02-13
In regard to a previouis thread ([http://ubuntuforums.org/showthread.php?t=1218221](http://ubuntuforums.org/showthread.php?t=1218221)) that is now closed.

The problem was to map the CTRL-Arrow key combination to produce Page Up / Down, rather than FN-Arrow which is cumbersome on some keyboards (a 2 handed operaton).

A solution was mentioned in the thread using .Xmodmap but not exactly what I was looking for. Anyway, the solution is to create a file called ~/.Xmodmap containing the following:

  keycode 62 = Mode_switch
  keycode 105 = Mode_switch
  keycode 116 = Down NoSymbol Next
  keycode 111 = Up NoSymbol Prior
  keycode 113 = Left NoSymbol Home
  keycode 114 = Right NoSymbol End

The difficulty is that there is no code for the FN modifier but there is one for MODE SWITCH even tho there is no physical key for this! So what the first two lines do is change CTRL-R and SHIFT-R (keys 105 and 62) to produce Mode_switch. Now we can assign the Down arrow key (116) to produce Down when pressed alone, nothing (NoSymbol) when pressed with SHIFT and Next when pressed with Mode_switch.

The .Xmodmap is run automatically on login on XFCE otherwise you need to call it from .xinitrc as follows: xmodmap ~/.Xmodmap

---

