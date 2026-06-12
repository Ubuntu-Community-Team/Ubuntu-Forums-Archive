---
title: "Not saving my settings"
date: 2008-04-26
forum: General Help
---

### Post by phantom1976 on 2008-04-26
HI all

 Totally new here to the world of Linux and loving it over Windows so far. I have one issue however that I have on the most up to date version of Ubuntu.. I had set my system up to dual boot with Vista but then decided to just delete the windows partition and reinstall Linux again, since then my weather information has not been displaying along with my time and date on the bar... Any ideas?

Thanks so much

Further I don't have the Firestater icon on the panel either from each start to another..

Thanks again

---

### Post by ryanhaigh on 2008-04-27
If you have reinstalled ubuntu then you will need to re-add those applets and reinstall firestarter.

---

### Post by phantom1976 on 2008-04-27
> **ryanhaigh said:**
> If you have reinstalled ubuntu then you will need to re-add those applets and reinstall firestarter.


Thanks for the reply, I have done that however my settings still seem to have been forgotten with each new session

---

### Post by ryanhaigh on 2008-04-27
Sounds like an issue with gnomes session management. I don't know much about that so sorry I canot be any more help.

---

### Post by ghost_ryder35 on 2008-04-27
You could try
System, Prefrences, Sessions, then click "Auto Remember Sessions on Logout"

---

### Post by phantom1976 on 2008-04-27
> **ghost_ryder35 said:**
> You could try
System, Prefrences, Sessions, then click "Auto Remember Sessions on Logout"

Thank you again for your reply, I'll have to have a look and see if that fixes it..

Thanks again

Update: Nope that didn't fix it either, dang.. Ah well thanks for the help anyway

---

### Post by ryanhaigh on 2008-04-27
Using ```
ps ax | grep gnome-settings 
``` see if you get a line mentioning /usr/lib/gnome-control-center/gnome-settings-daemon

---

