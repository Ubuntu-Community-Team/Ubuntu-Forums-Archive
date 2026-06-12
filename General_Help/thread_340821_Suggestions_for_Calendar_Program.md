---
title: "Suggestions for Calendar Program"
date: 2007-01-17
forum: General Help
---

### Post by oracle5 on 2007-01-17
Evolution really isn't for me and I can't seem to get korganizer to work with gnome correctly. I've tried sunbird with kdocker so I could get reminders but it has a few annoyances like sunbird popping up and then going to the tray at system startup instead of going directly to the tray. I'm open to any suggestions.

Thanks,
oracle5

---

### Post by ynnhoj on 2007-01-17
i'm a big fan of orage.  it's nice and simple.

---

### Post by oracle5 on 2007-01-17
I can't get orage to start up while I'm in gnome. I went over into xfce and it worked fine but shouldn't an xfce program work fine in gnome?

oracle5

---

### Post by gjtoth on 2007-01-17
I use either Inbox.com or Google Calendar.  I prefer Inbox.com... much nicer but I can access it from my Google home page like I can with Google Calendar.  I would use Inbox's homepage in a minute if they had a box for bookmarks.

---

### Post by andreas64 on 2007-01-18
deleted

---

### Post by rosslaird on 2007-01-18
I'm a bit of a calendar freak, and have tried many (Lightning, Evolution, Korganizer, Orage, Google, etc.). For a while now I've been calendaring online:

30boxes.com

It's outstanding.

Ross

---

### Post by tc101 on 2007-01-31
I am using Evolution for email and calendar.  The one thing I miss from outlook is the popup window that reminds me of events on my calendar that are happening today or are past due.  Is there any way to get this to happen in Evolution?  If not, is there any other calendar program that does it?

---

### Post by sk8dork on 2007-03-27
thought i'd chime in and say that i just started using sunbird with alltray and it is working nicely. in my startup script (i use fluxbox/fluxbuntu) i have the following:
```
pidof sunbird || alltray sunbird &
```
pidof checks to see if sunbird is running, at times it is necessary to restart fluxbox to apply some changes, and it always runs the startup script, so pidof is necessary to make sure something isn't run again if it's already running. 'alltray sunbird &' is the necessary part to get sunbird to start up in a systemtray icon. working well so far.

oh, and of course i have a symlink in /usr/bin to point to sunbird so that it can be run with just 'sunbird' instead of './home/sk8dork/sunbird/sunbird'

---

