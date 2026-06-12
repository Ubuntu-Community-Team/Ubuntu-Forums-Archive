---
title: "Launch Evolution at startup as an applet?"
date: 2007-12-27
forum: General Help
---

### Post by bgryderclock on 2007-12-27
I would like evolution to launch during my gnome session start up in a hidden or applet status and pop up calendar event reminders when they are due.

 Is there a command line option that I can pass on the session start up or an applet that I can install to do this?

---

### Post by Nonno Bassotto on 2007-12-27
The service evolution-alarm-notify should already start hidden at login, and you should get a reminder for your alarms, even with Evolution closed. If this doesn't happen, try to add evolution-alarm-notify to your startup session (under System->Preferences, ask again if you need more details).

Are you trying to get automatic reminder for  birthdays? There is a known long-standing evolution bug about this, and [gBirthday]("http://dernalis.googlepages.com/gbirthday.html") is a reasonable solution.

---

