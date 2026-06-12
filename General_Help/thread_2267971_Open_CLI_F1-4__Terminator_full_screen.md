---
title: "Open CLI F1-4 / Terminator full screen"
date: 2015-03-05
forum: General Help
---

### Post by Drenriza on 2015-03-05
Hi all
I havent used ubuntu in a good while, but when i started at version 6.x i remember a feature where you could use F1 through F4 to open 4 different full screen
terminal windows. And F5 took you back to the graphical gui.

How does this work today? Using 14.04 LTS

Also a feature i have looked for in ages is
Is it possible to open a full screen terminal (like with F1-F4), and than use terminator that allows for splitting the screen vertical and horizontal.

Thanks in advance
Kind regards

---

### Post by Holger_Gehrke on 2015-03-05
You are talking about the "virtual terminals", aren't you ? They are still there, the key-combination are ctrl-alt-F1 - ctrl-alt-F6 and ctrl-alt-F7 gets you back into the GUI.

And for splitting up one terminal into several windows there's several tools, 'screen' and 'byobu' are the best known. The manual pages for these should be available on your system.

---

### Post by Lars Noodén on 2015-03-05
> **Holger_Gehrke said:**
> And for splitting up one terminal into several windows there's several tools, 'screen' and 'byobu' are the best known. The manual pages for these should be available on your system.

byobu is just a front end.  screen is well established but tmux is gaining in popularity having a cleaner code base and being simpler to use.  EIther one, screen or tmux, are well worth getting to know.  I used screen for a long time but have pretty much gone 100% over to tmux these days.

---

