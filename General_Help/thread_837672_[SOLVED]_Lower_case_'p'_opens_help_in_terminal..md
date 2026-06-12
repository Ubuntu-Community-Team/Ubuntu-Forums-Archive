---
title: "[SOLVED] Lower case 'p' opens help in terminal."
date: 2008-06-22
forum: General Help
---

### Post by NT4usB on 2008-06-22
I don't know what I did to change it and I don't know how to change it back but somehow p is assigned to open the help screen when typing in a terminal.
How do I un-assign p since p is one of the more popular keys in terminal, terminal is pretty much useless without it.
ed: This is on my Edgy box.

---

### Post by niyonk on 2008-06-22
I believe you can use the unalias command to remove the 'p' command

Give it a try and tell us

---

### Post by unutbu on 2008-06-22
Are you using gnome-terminal?
If so, click on the terminal's menu Edit>Keyboard Shortcuts. Scroll down to "Help". It should have one subfield called "Contents". If it is currently set to "p" then that explains where your problem is coming from. Clicking "Contents" will allow you to change the shortcut key to something else. I think Alt-d is the default.

---

### Post by NT4usB on 2008-06-22
Edit>Keyboard shortcuts fixed it. No idea how I managed to set in the first place...
Thanks for the quick replies!

---

