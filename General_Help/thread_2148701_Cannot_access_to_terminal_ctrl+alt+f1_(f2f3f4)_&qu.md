---
title: "Cannot access to terminal ctrl+alt+f1 (f2/f3/f4) &quot;Incorrect login&quot;"
date: 2013-05-26
forum: General Help
---

### Post by UnUnlucker on 2013-05-26
After updating my Ubuntu from 12.04 to 13.04 I can't access to the terminal with my login, and the punctuation marks are some other staff like other language, I mean literas with two point above. So how can I make normal layout? P.S. my Terminal ctrl+alt+T working properly.

---

### Post by 2F4U on 2013-05-26
What exactly happens if you press Ctrl-Alt-F1 (or F2, F3)? Are you presented with a text based login?

> the punctuation marks are some other staff like other language

I am not sure what exactly that means. Are you saying that the keyboard layout is different from what it should be?

---

### Post by UnUnlucker on 2013-05-26
After pressing Ctrl+Alt+f1 I see the black screen and welcoming to type my login, then welcoming to type my password of course. After typing them completely correct he says something like "Your login is incorrect". 

Yeah, exactly, the letters is common, but when I tried to type some :;"'~./, he shows me some figures and other uncommon symbols

---

### Post by 2F4U on 2013-05-26
So it seems as if the keyboard layout in the console is wrong. Try if this helps to change the layout:

[http://ubuntuforums.org/showthread.php?t=1758915](http://ubuntuforums.org/showthread.php?t=1758915)
[https://help.ubuntu.com/community/LocaleConf](https://help.ubuntu.com/community/LocaleConf)

---

### Post by Habitual on 2013-05-26
ctrl+alt+f1 isn't a "terminal"
It's a console.

---

### Post by UnUnlucker on 2013-05-30
What about ctrl+alt+f2 and f3, they are too only consoles?

---

### Post by UnUnlucker on 2013-05-30
Yeah, Thanks a lot) first one helped me perfectly

---

### Post by UnUnlucker on 2013-06-10
No, it's not helped perfectly, I still got a problem: after rebooting the computer I got this problem again, in the same way.

---

### Post by thelegs on 2013-10-31
Got a similar problem, after upgrading to 13.10 from 12.04, once I'm in the GUI I can't switch to console by pressing Ctrl+Alt+F1..F6. I've tried with both Unity and Gnome-shell, they both trigger their own features as if you press Alt+F1..F6 without Ctrl, eg. Ctrl+Alt+F1 = Alt+F1 = Search.

I've seen a doc here: [http://www.computershowto.pro/2013/03/terminal-missing-in-ubuntu-when-you-press-altctrlf1-f6/](http://www.computershowto.pro/2013/03/terminal-missing-in-ubuntu-when-you-press-altctrlf1-f6/) where it explains that the problem may be related to a missing getty, and I'm going to try an adaptation of this, but if anybody has any more ideas on what happened please share... I can appreciate if the new GUI has got rid of the traditional console switches, but I would like to able to get them back easily if I miss them, no? ;)

*Edit: no, that doc didn't work.*

---

