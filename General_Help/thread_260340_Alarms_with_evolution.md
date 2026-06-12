---
title: "Alarms with evolution"
date: 2006-09-18
forum: General Help
---

### Post by Nonno Bassotto on 2006-09-18
I know this question has been posted quite alot of times, but it seems that all the answers are outdated, and sound like "it will be better in Dapper". Now, I'm using Dapper, so I ask: is there a way to make Evolution remind me anything? Better: is there a way to make Evolution remind me anniversaries with a sound? Do I have to have Evolution open for this? If I really have to, there's really something wrong. I mean: I need an alarm because I forget things, how do I remember to open Evolution just before the alarm sounds? ](*,)

---

### Post by yopnono on 2006-09-18
Yes I know I also what it to make a sound of some kind, Like now it's only pop up a dialog that tells me about the event. But I really would like to be able to add sound to it.

---

### Post by Nonno Bassotto on 2006-09-19
I'm not even able to obtain a popup :sad:

---

### Post by yopnono on 2006-09-19
> **Nonno Bassotto said:**
> I'm not even able to obtain a popup :sad:
 
Open the evolution then Edit - Preferences - Calendar and Task
there you have "alerts"

---

### Post by Nonno Bassotto on 2006-09-19
I know. Should alarm popup work even with evolution closed? It doesn't. Moreover my main problem is: I'm able to set a single alarm, but not to set alarm for all anniversaries.

---

### Post by glennric on 2006-10-01
I had the same problem.  I discovered that the problem is when you set an alarm the evolution-alarm-notify daemon is started.  Then if you reboot, this daemon is not restarted.  Hence your alarms will not be displayed or sounded.  The fix is to ad 
```
/usr/lib/evolution/2.6/evolution-alarm-notify --oaf-activate-iid=OAFIID:GNOME_Evolution_Calendar_AlarmNotify_Factory:2.6 --oaf-ior-fd=51
```
to the startup programs under System->Preferences->Sessions
At least this worked for me.

---

