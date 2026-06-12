---
title: "hit by KDE bug, any workarrounds?"
date: 2013-04-27
forum: General Help
---

### Post by mastablasta on 2013-04-27
These kind of things really should get into LTS.
previous updates made my keyboard and mouse to stop working. this time the time is wrong.

Attempting to change it in bios doesn't help. Neither does changing the server, as the aplication crashes on change. Changing time manually in application has no effect. anyone has any idea about a workarround?
this is how it looks like: [http://ubuntuone.com/3x0nhKJCaWKzz34YxGCk5A](http://ubuntuone.com/3x0nhKJCaWKzz34YxGCk5A)

---

### Post by mastablasta on 2013-05-08
not solved yet. it's getting annoying. it appears the time is showing some sort of UTC time or something. in any case this should have happened.

---

### Post by SeijiSensei on 2013-05-08
There's nothing wrong with the clock; it's just showing the time in UTC and your local time zone.

To remove the UTC entries, right-click the clock in the panel, then pick Digital Clock Settings.  In the Time Zones list uncheck UTC, or make sure you have it set to use the local time zone in the drop-down box in that menu.  I usually disable the timezone display in the Appearance menu as well.

---

### Post by mastablasta on 2013-05-13
wow that was it? i tried to change the server settings in contorl panel and it crashed the GUI. 

an update changed it to UTC for no good reason.

---

