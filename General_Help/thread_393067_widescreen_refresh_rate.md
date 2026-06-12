---
title: "widescreen refresh rate"
date: 2007-03-25
forum: General Help
---

### Post by panurge77 on 2007-03-25
I`ve just installed feisty beta and nvidia drivers. Gladly I can use 1440x900 (I never managed to work it out in edgy, but dapper worked). I set xorg.conf to use this resolution and set the correct values for horizontal and vertical sync. The problem is: the screen resolution app only gives me two option for refresh rate: 50 or 54. It was supposed to be 59. Should I worry? or the problem would be only to set a higher than default number? Any idea on another setting that could help?

edit: it`s a lcd monitor, model AOC 193FW

---

### Post by dcstar on 2007-03-26
> **panurge77 said:**
> I`ve just installed feisty beta and nvidia drivers. Gladly I can use 1440x900 (I never managed to work it out in edgy, but dapper worked). I set xorg.conf to use this resolution and set the correct values for horizontal and vertical sync. The problem is: the screen resolution app only gives me two option for refresh rate: 50 or 54. It was supposed to be 59. Should I worry? or the problem would be only to set a higher than default number? Any idea on another setting that could help?

edit: it`s a lcd monitor, model AOC 193FW

I find commenting out any sync rate settings in /etc/X11/xorg.conf works well because the X system picks up all the correct settings from the monitor itself on startup (at least it does on mine....)

You may want to try this and see how it works on your setup.

---

### Post by panurge77 on 2007-03-26
That did not work, but thanks anyway. I tried nvidia-settings and it sees 60 refresh rate, which is max supported for the monitor (I never really got this one, but monitor manual says default is 59 and max is 60). I set it for 60 in nvidia-settings and now gnome screen resolution app says I'm running in refresh rate 89! I guess my monitor would have fried at 89 so I'll trust nvidia-settings. Any expert about this? Can I trust this app?

---

