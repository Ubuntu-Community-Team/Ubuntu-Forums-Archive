---
title: "xbindkeys with xte not working in wine"
date: 2012-11-03
forum: General Help
---

### Post by J V on 2012-11-03
I just bought a logitech G500 and it's working beautifully, I have xbindkeys setup like so:
```
# Third thumb button
"xte 'keydown 0'"
b:10
"xte 'keyup 0'"
Release + b:10

# 2 extra index buttons
"xte 'keydown 9'"
b:13
"xte 'keyup 9'"
Release + b:13

"xte 'keydown 8'"
b:14
"xte 'keyup 8'"
Release + b:14
```I bound them to these numbers as they are often keybindable in games but far enough away from my wasd hand that I'd never use them.

While using a terminal, browser, file manager etc, these binds all work as expected. Pressing the buttons is the same as if I pressed one of the matching keys.

However, when playing guild wars 2, dishonored, or other games in wine, they do not "Catch" the event.

Which is strange because manually running these commands (delayed by sleep 5s) creates the entry in the controls menu just fine.

Is it possible the button press event from the mouse is causing the games to conflict the input from xte? In that case is there a way to halt the mouse button press event?

Edit: Would evrouter work for what I'm looking for? What about xorg.conf?

**Edit:** evrouter worked like a charm using this code:
```
"Logitech G500" "/dev/input/event4" any key/277 "XKey/0"
"Logitech G500" "/dev/input/event4" any key/280 "XKey/9"
"Logitech G500" "/dev/input/event4" any key/281 "XKey/8"
```It required running as sudo to stick so this may need to be run every time I log in (In which case I have a brand new problem in how do I make a program automatically run as sudo when I log in)

Edit: Now it's strange... It's behaving like xbindkeys in that it works in most linux windows but not in wine... then *after* I run "sudo evrouter /dev/input/event4" it works in wine too... Now I'm wondering where the "works outside of wine" button presses are coming from and also need to find a way to run that on login.

Edit: evrouter + lightdm session-setup-script ftw :)

---

