---
title: "Gnome Software Will Not Shut Up!"
date: 2016-06-05
forum: General Help
---

### Post by jim_deadlock on 2016-06-05
My 50unattended-upgrades is set to auto-update everything so I don't need any reminder prompts about system updates, but Gnome Software keeps pestering me all the time before my system has had a chance to update itself, it's really annoying. I've removed all of the following files but it's relentless! How do you make it stop?

/etc/apt/apt.conf.d/99update-notifier
/etc/cron.daily/update-notifier-common
/etc/cron.weekly/update-notifier-common
/etc/xdg/autostart/update-notifier-common

Oh, and 'Software and Updates' is set to automatically check for updates *Never* so it can't be that.

---

### Post by deadflowr on 2016-06-05
Turn it off in the Startup Applications.
I found that to be the quickest way, 

But if you want to remove the startup .desktop file, it's a local user startup, 
so it's in the home folder's autostart folder, instead of the /etc/xdg folder.
Look for *~/.config/autostart/gnome-software-service.desktop*

---

### Post by DuckHook on 2016-06-05
> **jim_deadlock said:**
> My 50unattended-upgrades is set to auto-update everything so I don't need any reminder prompts about system updates... How do you make it stop?I may very well be stepping out of line here and I know that this was not your question, but do you *really* want to do that? I'm just wondering about your thoughts on security. I won't let my system auto-update because I want to review every single update before allowing it.

Maybe I'm just paranoid.

---

### Post by jim_deadlock on 2016-06-06
> **deadflowr said:**
> *~/.config/autostart/gnome-software-service.desktop*

Damn, how did I miss that? Thanks!

> **DuckHook said:**
> I'm just wondering about your thoughts on security.

Well, my stuff all comes from the official repositories so my feeling is that I wouldn't know better than the experts who put it there even if I inspected every line of code.

---

### Post by jim_deadlock on 2016-07-03
With all of the aforementioned steps taken, I'm STILL getting notifications from Gnome Software. Any other suggestions?

---

### Post by vasa1 on 2016-07-03
What happens if you have something like```
pkill update-notifier
```somewhere in your autostart?

---

### Post by jim_deadlock on 2016-07-03
I've just noticed /etc/xdg/autostart/update-notifier.desktop so I'll remove that and see what happens.

---

### Post by deadflowr on 2016-07-03
> **jim_deadlock said:**
> I've just noticed /etc/xdg/autostart/update-notifier.desktop so I'll remove that and see what happens.

No need to remove it.
You can simply add the line
```
X-GNOME-Autostart-enabled=false
```
to the file.

---

