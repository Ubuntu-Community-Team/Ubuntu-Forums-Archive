---
title: "Can't turn off sound notifications/alerts in ubuntu 17.10"
date: 2018-04-07
forum: General Help
---

### Post by lucemferre on 2018-04-07
I really don't like alert sounds and want to turn them off. I have tried to turn of sound effects in system settings, but that doesn't work for some reason. I also deleted all the sounds in /usr/share/sounds/gnome/default/alerts, but the sound remains. What am I doing wrong?

---

### Post by TheFu on 2018-04-07
Have you tried **pavucontrol**?

I'm making all sorts of reasonable assumptions, based on the little information provided.

---

### Post by lucemferre on 2018-04-09
Yeah, sorry about that, I don't really know what information would be relevant for this. Thanks for trying anyway. I have tried pavucontrol though and the sound is still there.

---

### Post by TheFu on 2018-04-09
"I have tried pavucontrol though and the sound is still there. " is pretty vague. Exactly what did you change inside that program?  Did you find the system sounds slider and mute it?

---

### Post by lucemferre on 2018-04-09
Yes, I turned the slider to 0 and muted the sound (on the first tab in pavucontrol).

---

### Post by lucemferre on 2018-04-09
Sorry that I can't provide more info, I have tried to mute the sounds in system settings, pavucontrol and deleting the files I mentioned. I was hoping that this would be a known bug (even though I didn't manage to find anything about such a bug).

---

### Post by TheFu on 2018-04-09
I would check that other system sounds are gone too, which I suspect. The programs providing the alerts may not be doing it the correct way, so those sounds come through some other channel. If muting all sounds doesn't mute this too, that is just scary.

Or it could be a bug.  Have you checked the bug DB? [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)  It is good to ask here first, since sometimes it is something simple.

---

### Post by lucemferre on 2018-04-09
I did not find any bug report, but I did find this: [https://askubuntu.com/questions/980046/2-different-alert-sounds-playing-at-once-in-ubuntu-17-10](https://askubuntu.com/questions/980046/2-different-alert-sounds-playing-at-once-in-ubuntu-17-10). Not exactly the same as my problem, but I turned off all event-sounds, like you suggested, in dconf-editor and now it is silent. Not sure if I should mark this as solved, but it worked. Thanks for the help!

---

