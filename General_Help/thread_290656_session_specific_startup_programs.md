---
title: "session specific startup programs"
date: 2006-11-01
forum: General Help
---

### Post by giants_fan on 2006-11-01
Hi,

Is it possible to have session specific startup programs?  Lemme explain...

If I start a Xgl session, I want to run "beryl-manager" on startup.  If I start a regular gnome session, I don't.  

I know you can add programs to startup via System->Preferences->Sessions->Startup Programs (tab), but those aren't specific to a particular session.

Thanks!

---

### Post by zaziork on 2006-11-13
Have you found a solution to this? I have exactly the same problem.

---

### Post by dbbolton on 2006-11-13
the last time i went messing with that stuff, i ended up sans graphical interface, and had to reconfigure everything in nano. boy, that was a hoot.

---

### Post by giants_fan on 2006-11-15
I haven't found an elegant solution...but did manage to hack together something.  

Basically, create an executable script (startup.sh) and put it somewhere (I put mine in ~/bin) and execute it on startup.  In that  script, you can see what session you're running (via environment variables) and run/not-run things accordingly.

---

