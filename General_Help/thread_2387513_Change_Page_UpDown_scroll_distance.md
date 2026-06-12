---
title: "Change Page Up/Down scroll distance"
date: 2018-03-20
forum: General Help
---

### Post by emnaki on 2018-03-20
Is it possible to change the number of lines scrolled when I use page up/down. I would like to scroll by fewer lines since I don't like reading from the top or bottom of the screen. Thanks.

---

### Post by TheFu on 2018-03-20
Don't believe that scroll controls are system-wide.  Each program  would have settings to control what, if anything, they do with pgup/pgdn keystrokes.  

If you like, you can use a tool like xdotool to make pgdn tied to 20 down-arrows.  That wouldn't have the scaling for the current window size, which would drive me nuts.  Also, it wouldn't work for a remote X11 connection either.

So ... the first question is answer is - what program are you talking about?  gedit?  some browser?  libreoffice?  some other programs?

[https://help.ubuntu.com/stable/ubuntu-help/keyboard-nav.html](https://help.ubuntu.com/stable/ubuntu-help/keyboard-nav.html) is all that I found.  Doesn't seem too helpful.

---

### Post by emnaki on 2018-03-25
The program that I would like this feature most is my coding ide which is spyder3. I would imagine not scaling for window size as you said would be annoying. what would be best would be a half page page up/down instead of a full page.

---

### Post by TheFu on 2018-03-25
Good news!   The source code is available and you can add this feature, submit a pull request and help everyone else too!
[https://github.com/spyder-ide](https://github.com/spyder-ide)

---

