---
title: "Help! Repeated &quot;Screenshot&quot; window."
date: 2007-04-19
forum: General Help
---

### Post by matthewdhandley on 2007-04-19
I just convinced a friend to switch from Windows and install Ubuntu Edgy on his Pavillion ze5300 laptop. The install went fine, and it runs great except for one minor detail:

Every so often, at random times, the "Screenshot" applet (which is the program gnome-screenshot) will run about 20 times in immediate succession for no apparent reason. This slows down the system, not to mention is extremely annoying. I tried simply deleting gnome-screenshot, but now it just brings up error messages all the time, because it is looking for the missing gnome-screenshot program. Any help would be great, as I don't want to lose this new convert to Ubuntu.

---

### Post by gepatino on 2007-04-19
Check the hot keys configuration at System/Preferences. By default, <PrntSrcn> launches gnome-screenshot, maybe the user changed that by mistake to some other key used more commonly.

If that's not the case, maybe he/she has a problem with the keyboard, some sticky key maybe? Try asigning no key to the screenshot item.

---

### Post by fanatik on 2007-04-19
well programs usually don't just start themselves... the Print Screen key is mapped to take a screenshot when it is pressed (alt+Print Screen will take a windowshot) perhaps the Print Screen key on this laptop is easily pressed? You could try unmapping this key.

Either that, or its configured to run in cron for some bizzare reason - check the contents of your crontab.

---

