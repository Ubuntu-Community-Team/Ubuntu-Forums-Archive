---
title: "Desktop freezes when I click the calendar?"
date: 2008-06-17
forum: General Help
---

### Post by mslade on 2008-06-17
Hey all,

I've been using Ubuntu 8.04 for about 3 weeks now.  "Recently", I've encountered a reoccurring problem.  I don't know when it started and therefore what I may have changed.

Clicking the calendar in the taskbar locks up the desktop.  It depresses the weath/calendar button, and it stays depressed.  From that point on my taskbar  if frozen (new programs and closed programs aren't reflected there, my workspace switcher doesn't reflect any changes to my workspaces, etc...).

How can I diagnose this?  Or is there at least a way for me to kickstart the desktop again without a full reboot?  It's becoming a time sink for me...

Thanks
Mark

---

### Post by JGrubbs on 2008-06-27
This has started happening on my wife's laptop, but not on my son's two Edubuntu systems. Any ideas on how to fix this?

---

### Post by MatthewPlanchard on 2008-06-29
I had this same problem, and though I don't remember exactly where in the forums I found it, the solution was to:

Go into Evolution and uncheck the Google calendar.

Apparently the clock tries to find and sync with an online GCal, which causes the panel to freeze, or something.

As a side note, you can use the command 'kill' to close and restart the panel, but you've got to use the process id which you can get with the command 'ps axu | more' and looking for the one that says 'gnome-panel'.

Good luck!
Blessings!

---

### Post by ksigler on 2008-07-30
man. thanks so much for the fix. Forgot I used to sync Evolution with G-cal and this was driving me crazy!!

BTW, you can quickly stop and restart the frozen gnome-panel via the pid with:

kill `pidof gnome-panel`

---

### Post by ivikas on 2008-07-31
I have installed advanced desktop effects (compiz fusion) and done some settings and later got it removed when i noticed that my desktop workspace switcher is not working.Only one is working now and all other are freezed,(unable to click and activate.Please give me a fix for this.

Thanks in advance

---

