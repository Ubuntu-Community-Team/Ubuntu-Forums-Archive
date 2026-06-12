---
title: "Power manager error"
date: 2015-10-09
forum: General Help
---

### Post by ric_Poirier on 2015-10-09
Hello everyone,

I have set up my computer such that after some time the screen shuts down and the session locks via the power manager in Xubuntu 14.04. For about a week now, I have started getting a notification that says "**Power Manager not authorized**" every time I unlock the screen and re-enter my session. Here is the notification:

[ATTACH=CONFIG]264866[/ATTACH]

On the computer though, everything seems to work fine.

Has anyone got the same problem? How could I get rid of this, it is really annoying...

Thanks,

---

### Post by egeezer on 2015-10-09
Did you check the permissions?

---

### Post by ric_Poirier on 2015-10-10
I'm sorry egeezer, which permissions are you talking about? I usually change settings in the power manager in my user account, without root privileges.

---

### Post by egeezer on 2015-10-11
Uh-oh, I begin to think there's something screwy since the latest update.  I just checked on Power Manager in the Settings on my Xubuntu installation (actually Ubuntu + Xfce + Xfce-goodies), and I get no response at all - just an error message that it didn't respond.

Again, all seems to work just fine, but I can't get the Setting for it to respond.  I will check on another computer and report back.

About 15 minutes later: Checked another computer which I set up to be almost identical, and the Power Manager does permit access.  Power management ehavior of the two computers is the same.  Only difference is that first one (no PM access) runs on kernel 3,13.0-65, the other on 3.19.0-30.

Looks like the original 14.04 kernel is aging fast! ;-)

---

### Post by ric_Poirier on 2015-10-12
Hi egeezer,

Thanks for your reply. Si I guess I will juste wait for the next kernel update to see if they fixed the issue!

Thanks for the test!!

---

