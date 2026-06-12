---
title: "Windows Borders in 14.04"
date: 2014-04-19
forum: General Help
---

### Post by apollothethird on 2014-04-19
Can someone assist me in getting Windows Borders in 14.04?  Every since Unity I have been using Gnome-Tweak to install the Dust theme which has excellent borders around the windows.  However after upgrading to 14.04 this doesn't work.  There are no borders around the windows, and this makes it very hard to tell where one window starts and another ends.  It's also very hard to tell which window is active because the title bar in both the active window and the inactive window are so much alike.

I tried using Windows Decorator in CCSM, however, you have to disable Unity to use that feature.

Thanks in advance for anyone who has input on this.

It appears to be insane to not have borders around the windows and have both the activate and inactive title bars looking so much a like.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/~ljames")

---

### Post by sbandeira on 2014-06-03
-> install unity-tweak-tool

-> run: sudo service lightdm restart

-> Press Ctrl-Alt 1 (to go to console)

-> run as normal user: unity-tweak-tool --reset-unity

---

