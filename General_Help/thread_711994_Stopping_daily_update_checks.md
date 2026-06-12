---
title: "Stopping daily update checks?"
date: 2008-03-01
forum: General Help
---

### Post by QCompson on 2008-03-01
My gutsy install checks for updates every morning at the same time.  For a minute or two it sounds like my computer is also working as a tree-shredder.

In update preferences (software sources), under the "Updates" tab, I have it set to check for updates every two weeks, but nevertheless it checks every day.

Any suggestions?  Ideally I'd like to actually check for updates weekly, but I'd rather turn it off completely than have it check every day.

Thanks.

---

### Post by bwhite82 on 2008-03-01
Move the daily entries in your cronttab to weekly. Check in: /etc/cron.daily
On my Debian system, the entries are: apt and aptitude
They may be different for Ubuntu. Anyways, all I'd have to do is move those entries to weekly:

> cd /etc/cron.daily
> sudo mv apt* /etc/cron.weekly

---

### Post by Gillingham on 2008-03-01
I f you are using gnome then under System>Administration you will find an option Software Sources.  There is a tab called updates from which you can set the frequency of the updates.

---

### Post by QCompson on 2008-03-01
Thanks Soldierboy, I will try that.

Gillingham, as I mentioned in my original post, I tried changing the frequency of update checks in "Software Sources".  It doesn't work, and still checks daily.  I will post a bug report if I don't find a similar one.

---

### Post by QCompson on 2008-03-26
So I tried what Soldierboy suggested, and my computer *still* grinds and chuggs (presumably still checking for updates) at precisely 7:35 every morning.  No one else notices their box checking for updates every day despite what you choose on the Updates tab in Software Sources?

---

### Post by oldos2er on 2008-03-26
I had this problem in the past. I finally had to uncheck the box next to 'Check for Updates:'.

---

