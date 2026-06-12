---
title: "[SOLVED] gnome-session-save --kill , logging out by clicking or that command locks sy"
date: 2008-06-19
forum: General Help
---

### Post by darkazurka on 2008-06-19
**This thread was solved because the problem is described in the following post and bug report with many replies from many people**:
*[http://ubuntuforums.org/showthread.php?t=732245](http://ubuntuforums.org/showthread.php?t=732245)
*[https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/203668](https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/203668)

My input is locked each time I either press the quit button or in terminal: ```
gnome-session-save --kill
```

The time continues to go on, like nothing has happened and I can still see the monitor bars showing stats, so it seems only the input gets locked (mouse, keyboard).

After any of the 2 logouts I'm not being able to communicate at all with the computer. I pull off the plug after 5 minutes of nothing happening.

I wish I could remove some settings folders in my /home/user/ folder to clear up the matter. I'm looking forward to replies.

---

### Post by darkazurka on 2008-06-19
More info and experimentation provided:

This time before I clicked on the "doom icon", I fired up a terminal used sudo su, to become root, and then typed ```
shutdown -P 17:10
```

Then it gave the message > The system is going down for power off in 2 minutes!
Right after that I click the icon, and keyboard gets locked, as well as mouse clicks. (I can only move mouse, but it doesn't have no effect at all and doesn't change the shape of ANY icon as it usually does any desktop environment)

...guess what happens after 1 minute.(?) It goes: > The system is going down for power off IN ONE MINUTE!
and it unlocks! Though I don't want it to shutdown. I want it to LOG OUT. There are more users on this computer. I wish I can find the "/.~" or is it "/~." folder which I can delete in home directory to resolve problem

(the other user accounts on this computer don't have this problem)

---

