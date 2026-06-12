---
title: "Xscreensaver only works while watching videos"
date: 2020-10-27
forum: General Help
---

### Post by dwinthrop on 2020-10-27
I installed Xscreensaver on my Ubuntu installation, version 20.04.  I also removed the default.  When the computer is left alone for the 10 minute delay I put into the settings, the screen goes black and no screen saver comes.  However, if I am watching videos on YouTube and the same 10 minutes passes, the screen saver engages.  How to fix this?

---

### Post by TheFu on 2020-10-27
When I want to watch videos, I disable the screen saver, run my preferred video player and when that program closes, re-enable the screen saver.

```
# Disable the screensaver
/usr/bin/xscreensaver-command -exit

# run some media player .... 
vlc 

# Enable the screensaver
/usr/bin/xscreensaver &
```

To create settings for xscreensaver, use the **xscreensaver-demo** program. I don't know whether any DE integrates DE settings with xscreensaver, but I have doubts.

---

### Post by Dennis N on 2020-10-27
> I installed Xscreensaver on my Ubuntu installation, version 20.04. I also removed the default.
What do you mean by default? There is no screensaver in Ubuntu 20.04 in the default install.

---

