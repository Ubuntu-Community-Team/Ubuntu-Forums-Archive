---
title: "terminal settings"
date: 2017-10-29
forum: General Help
---

### Post by yuri-weinstein on 2017-10-29
I reinstalled 16.06 ubuntu and have a minor issue, but it drives me mad, in the terminal when I move cursor (with keyboard left or right arrows) it goes one character for one keyboard arrow press and I'd like it to go left and right when I press and hold arrow (left or right), how can I set it up ? 


Thx!

---

### Post by yetimon_64 on 2017-10-29
On Ubuntu 16.04 here the standard behaviour is to continue moving left or right when the key is held down.
There is a system setting for the keyboard that if deactivated will cause what you are describing.

To check, go to and click on the power cog icon at the top right hand corner of your desktop screen on the top panel and open "System Settings"; then open the "Keyboard" settings icon. On the "Typing" tab, "Repeat Keys" section, ensure the check box for "Key presses repeat when key is held down" is ticked (turned on), see attached screenshot. Then recheck the behaviour in the terminal if you have had to to reset this setting.
[ATTACH=CONFIG]277338[/ATTACH]
Regards, yeti.

**Edit**: you can also use the "Home" and "End" keys on the keyboard to jump to the start or end of a line in the terminal with one key press.

---

### Post by ajgreeny on 2017-10-30
And just in case you were not aware of it, Ctrl+R/L will move the cursor one word at a time, just as it does in any other text writing application.

---

