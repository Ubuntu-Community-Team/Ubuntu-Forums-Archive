---
title: "Problem with CTRL+Arrow"
date: 2007-04-17
forum: General Help
---

### Post by HiSPEC on 2007-04-17
When clicking CTRL + Left/Right in gnome-terminal, it is supposed to go one word left or right, but instead it just prints: 5D or 5C.
How do I change this behavior ?

Thanks a lot!

---

### Post by HiSPEC on 2007-04-18
anyone?

---

### Post by stylishpants on 2007-04-18
Isn't that supposed to be Ctrl-PgUP and Ctrl-PgDn?

If you want to change the default shortcut keys for gnome-terminal, choose "Edit->Shortcut Keys" from the menubar.  If you have disabled the menubar, you can re-enable it by right clicking in the terminal window and clicking "show menubar".

---

### Post by strabes on 2007-04-18
No, in most other applications, ctrl+left/right arrow key moves the cursor 1 word to the left or right. It does the some thing when using Ctrl+backspace or Ctrl+delete - it deletes 1 word to the left or right. I would love to have this behavior in konsole since I ues kde.

---

### Post by stylishpants on 2007-04-19
Ahh, my mistake.  I misread the OP and thought we were talking about moving between tabs, not words.  So my earlier advice is bogus.

I don't know yet how to solve this one.  I've always had this working until my recent upgrade to Feisty, which has broken this functionality.  As a heavy shell user myself I certainly miss it.

I suspect that the answer may involve changing "Keyboard Model" option to something else (maybe try Generic 104-key keyboard?)  in the Layouts tab under System->Preferences->Keyboard.  Then log out and log in again.  I have not tested this myself since I have some work open here that I can't close right now, so remember the original Keyboard Model setting in case I'm wrong.

---

### Post by fangx1980s on 2007-04-20
Notice what Andrew Marks posted in [https://bugs.launchpad.net/ubuntu/+source/bash/+bug/89235](this page)

---

### Post by stylishpants on 2007-04-20
> **fangx1980s said:**
> Notice what Andrew Marks posted in [https://bugs.launchpad.net/ubuntu/+source/bash/+bug/89235](this page)

Ahh, that's useful. Thank you.

---

