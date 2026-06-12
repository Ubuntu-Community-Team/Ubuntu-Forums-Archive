---
title: "Displaying the current Keymap in Console"
date: 2013-06-14
forum: General Help
---

### Post by grounds on 2013-06-14
I am a native Dvorak user, but when I take my virtual machine to and from class, or onto other desktops, I'll type in Qwerty to account for the keyboard that is in-front of me. This is never a problem in Unity because I can easily switch my layout with a shortcut, console is the same way.

When I would like to get into the Console TTY (Ctrl+Alt+F1), my keymap is reverted back to the default (Qwerty). I have already figured out how to execute the loadkeys command to switch my layout to one defined in /usr/share/keymaps/ However, I would like to simplify this process.

I understand a little of bash scripting, enough to write a script that will change the layout for me. I would like to make a script that allows me to toggle my layout to the other one. This requires me to find out what the current keymap is set to, and although I can figure this out easily by typing, I have not been able to find any command which will do this. (Except for setxkbmap but this is not in the X environment!) I'm not asking any of you to write my script for me (I want to have that fun!), but if anyone knows how to figure out whether it's qwerty or dvorak, that would be wonderful so I can conditionally switch the keymap in my script.

---

### Post by HiImTye on 2013-06-14
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]
[http://unix.stackexchange.com/questions/2884/toggle-between-dvorak-and-qwerty](http://unix.stackexchange.com/questions/2884/toggle-between-dvorak-and-qwerty)

---

