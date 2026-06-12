---
title: "Monitor sleeps when not supposed to"
date: 2008-05-18
forum: General Help
---

### Post by CP` on 2008-05-18
When I set the sleep timer to never for the monitor in the gnome power manager it still goes to sleep after a period of time. I tried reinstalling it but that has done nothing. Any help is appreciated.

---

### Post by DaymItzJack on 2008-05-18
Sorry but:

[img]http://imgs.xkcd.com/comics/command_line_fu.png[/img]

---

### Post by wpshooter on 2008-05-18
> **CP` said:**
> When I set the sleep timer to never for the monitor in the gnome power manager it still goes to sleep after a period of time. I tried reinstalling it but that has done nothing. Any help is appreciated.

What version of Ubuntu is this ?

---

### Post by CP` on 2008-05-18
> **wpshooter said:**
> What version of Ubuntu is this ?
Hardy, completely updated. My gf had Gutsy and the monitor sleep worked perfectly on it so I figure its a problem with Hardy.

---

### Post by Shazaam on 2008-05-19
Try this....
Add to Section "ServerLayout" in xorg.conf

Option "BlankTime" "0"
Option "StandbyTime" "0"
Option "SuspendTime" "0"
Option "OffTime" "0"

and see if it helps.

---

### Post by CP` on 2008-05-19
I did that and restarted X and it did not help. That is assuming it was supposed to go in the xorg.conf in /etc/X11/ (I'm a newb at this stuff).

---

### Post by CP` on 2008-05-20
bump

---

