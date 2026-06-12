---
title: "Ubuntu 14.04 - compiz shade function/animation broken by upgrade"
date: 2014-05-20
forum: General Help
---

### Post by LifeEnemy on 2014-05-20
Hi all,

Hopefully this is a simple problem. I recently upgraded 12.04 --> 14.04. There have a been a few hiccups, though minor. I noticed that I can no longer use the 'shade' or roll-up animation from compiz (it reels the window up into it's title bar, really handy for quickly peeking underneath). Instead, it seems to minimize the windows (kind of). I'm now getting an outline of a transparent 'window' over my browser, which seems to be the remnant of a 'save' dialog box.

Any suggestions? I'd like to be able to make use of this feature.

---

### Post by jamapii on 2014-05-24
bump

i found this by searching, maybe it gets more responses in "Desktop Environments"?

---

### Post by LifeEnemy on 2014-06-01
For some reason I didn't get a notification of your reply. How do I move this to another forum? Or should I just repost it?

---

### Post by LifeEnemy on 2014-06-06
bump


Also, I'm suddenly not getting notifications for any threads here. Any suggestions on why that might be?

---

### Post by rick30 on 2014-07-08
I've got same problem!  Any luck solving this yet?

---

### Post by grumblebum2 on 2014-07-08
Shade no longer works with unity because the unity plugin for compiz
has taken over the drawing of window decorations.
Still works in a non unity session where the window decorations plugin is enabled.

---

### Post by opensource3141 on 2014-10-01
Hello,

Is there any activity on this issue?  Window shading is such an important function to some people's daily use window management.  It is frustrating that something that has been a fundamental feature of X Windows window managers for the last 20 years is not working and that there has been no public discussion of a fix in the 1/2 year since Trusty was released.

See also:
[http://askubuntu.com/questions/462996/problem-with-double-click-on-title-bar-or-right-click-on-it-or-any-window-washed](http://askubuntu.com/questions/462996/problem-with-double-click-on-title-bar-or-right-click-on-it-or-any-window-washed)
[https://bugs.launchpad.net/compiz-core/+bug/985430](https://bugs.launchpad.net/compiz-core/+bug/985430)
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1293740](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1293740)
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1313446](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1313446)

Thanks in advance,
Paarvai

---

