---
title: "Suspend/Hibernate in Hardy solved (for me)"
date: 2008-05-28
forum: General Help
---

### Post by wwalkersd on 2008-05-28
I've had suspend/hibernate problems on my eMachines VIA/AMD desktop starting with Gutsy (my first try at Ubuntu) and continuing with Hardy.  Under Hardy, if I told the computer to suspend manually (i.e., click power button in top right of screen, click suspend) it would always go to sleep and would always reawaken properly, but also would always give me the little error window in the bottom right telling me that my computer failed to suspend properly.

If, however, I left the computer alone until the suspend time came around, it would suspend (or maybe hibernate, I dunno), but upon waking would give me a black terminal screen with a couple of lines indicating failure, for example:
```
May 28 18:40:59 hostname kernel: [    0.303918] i8042 aux 00:0b: activation failed
May 28 18:40:59 hostname kernel: [    0.303926] i8042 kbd 00:0c: activation failed
```

After this, the system would shut down completely.  Upon booting it up again, it would return to the previously saved state.  Note that this is not the same behavior I had under Gutsy.

Based on a tip in a thread here, I started looking at gconf-editor.  I ran it and looked around for a while until I understood what I was seeing, then started playing hunches.  

What worked for me was 
[LIST=1]
[*]At a terminal prompt, type "gconf-editor" and hit return.
[*]Click the triangle next to "apps"
[*]Scroll down to "gnome-power-manager" and click the triangle.
[*]Click on the folder "general"
[*]In the panel on the right, click on the check boxes next to "check_type_cpu" and "network_sleep"
[/LIST] 
I rather suspect it was "network_sleep" which solved my problem.  Anyway, the computer is suspending and awaking just fine now, and with no messages. 

Your mileage may vary, of course, but it's worth a try.

---

### Post by wwalkersd on 2008-06-05
Apparently I spoke too soon.  It worked fine for a few days.  Now I'm getting various results.  Got the "failed to suspend" notice a few time, and the last two wakeups I got a blank screen and had to resort to the power button for a hard shutdown.  Sigh.

---

