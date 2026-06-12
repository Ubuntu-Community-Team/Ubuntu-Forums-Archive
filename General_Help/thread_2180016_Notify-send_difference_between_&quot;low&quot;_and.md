---
title: "Notify-send: difference between &quot;low&quot; and &quot;normal&quot; urgency levels"
date: 2013-10-11
forum: General Help
---

### Post by vasa1 on 2013-10-11
A notification seen by running```
#!/usr/bin/env bash
#Critical
notify-send -u critical 'Hello world!' 'This is an example notification.'
```needs to be dismissed by the user but there doesn't seem to be any difference between```
#!/usr/bin/env bash
#Normal
notify-send -u normal 'Hello world!' 'This is an example notification.'
```and```
#!/usr/bin/env bash
#Low
notify-send -u low 'Hello world!' 'This is an example notification.'
```
Both "normal" and "low" stay for about five seconds. How do they differ then? I looked at the man page for **notify-send** and at the link provided:  [http://www.galago-project.org/specs/notification/0.9/x320.html](http://www.galago-project.org/specs/notification/0.9/x320.html)

The link indicates that "For low and normal urgencies, **server implementations** may display the notifications how they choose." So how do I find out what my "server implementation" is?

---

### Post by stinkeye on 2013-10-11
Hi vasa1.
I believe "normal" will not show when running a fullscreen application while "critical" will....
and both timeout after 10 secs.

"Low" I don't know, D'oh.

---

### Post by vasa1 on 2013-10-11
> **stinkeye said:**
> Hi vasa1.
I believe "normal" will not show when running a fullscreen application while "critical" will....
and both timeout after 10 secs.

"Low" I don't know, D'oh.
That's interesting. I'm not seeing the "critical" one timeout at all. I have to dismiss it. This is not with anything running full screen because I don't know how to get the critical one to show. I have a script that I launch by double-clicking from the file manager. Plus, I'm using Lubuntu. I don't know if that makes a difference. It uses xfce4-notifyd.

What do you see with non-fullscreen apps?

---

### Post by stinkeye on 2013-10-11
In previous post I was using ubuntu's notify-osd.

I have an xfce session installed so removed notify-osd and tested using xfce4-notifyd.
In both the the xfce-session, using xfce4-notifyd, the notification was always on top whether "normal" or "critical".
"normal" closes with a click or after 30 seconds.
"critical" remains until clicked.

---

### Post by vasa1 on 2013-10-11
> **stinkeye said:**
> In previous post I was using ubuntu's notify-osd.

I have an xfce session installed so removed notify-osd and tested using xfce4-notifyd.
In both the the xfce-session, using xfce4-notifyd, the notification was always on top whether "normal" or "critical".
"normal" closes with a click or after 30 seconds.
"critical" remains until clicked.
Thanks for checking. That "critical" remains until clicked is what I see as well. The time of 30s depends on what we set in "xfce4-notifyd-config". I set notifications to appear in the lower left corner and to go away in 5s (other than for "critical", which must be dismissed).

---

