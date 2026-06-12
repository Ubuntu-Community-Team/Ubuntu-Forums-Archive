---
title: "Screen dims and goes to sleep when watching videos"
date: 2015-03-26
forum: General Help
---

### Post by New_buntu_89 on 2015-03-26
So, I'm using Ubuntu Mate 14.04 (64-bit) and I'm having some trouble when watching videos, which seems like a common complaint. When I'm watching any kind of video (fullscreen or not), the display is considered idle, so it dims quickly and goes to sleep within a few minutes. I tried both of the recommendations on this site: 

[http://www.webupd8.org/2012/05/2-ways-to-temporarily-disable.html](http://www.webupd8.org/2012/05/2-ways-to-temporarily-disable.html)

However, none of them worked. In fact, I tried disabling it all together through the power options and the screen saver options, and that didn't work for me either. Any clues as to what may be going on?

---

### Post by Dennis N on 2015-03-26
It could be caused by the DPMS system - see post #4 of this thread for more information and a solution that works in the 14.04 releases.

[http://ubuntuforums.org/showthread.php?t=2262763](http://ubuntuforums.org/showthread.php?t=2262763)

Note:
That post is about Xubuntu (and Ubuntu Studio), but the solution applies to Ubuntu Mate 14.04 as well. You can have Mate Screensaver and Xscreensaver both installed. If you want to use Mate screensaver, leave Xscreensaver in the startup applications but set it to disabled in the configuration dialog.

---

### Post by New_buntu_89 on 2015-03-27
I'm baffled. I installed Xscreensaver and set it to disabled. Then, I changed the power settings and the Mate Screensaver settings, and now the system is actually doing what I tell it to do, so... I guess it helped. Thanks! However, it would still be nice to have it work the way it is supposed to, acknowledging fullscreen video as activity and not considering the computer to be idle while watching them. I'll report back if I find anything funny in the next few days...

---

