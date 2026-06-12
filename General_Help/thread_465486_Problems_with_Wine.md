---
title: "Problems with Wine"
date: 2007-06-05
forum: General Help
---

### Post by jrmclaugh on 2007-06-05
Trying to use Wine 0.9.33 in Fiesty, but I get the error:
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
when I try to run .exe's in terminal using:
jimbob@jimbob-laptop:/media/windows/downloads$ wine msgr8us.exe

I thought I had fixed this by specifying c:\ to be a specific folder in my home folder.

Also, when I run winecfg, I get the same error message, but twice.

Any help is appreciate, thanks.

- James

---

### Post by cookies on 2007-06-05
hmmm

Have you tried a full path like

wine "C:\Program Files\Application\Application.exe"

(That is assuming you installed the app.)

If you wanna run an exe somewhere else, say on your desktop

wine /home/*username*/Desktop/application.exe

---

### Post by scrooge_74 on 2007-06-05
Have you tried to use Gaim/Kopete/Ekiga instead of Yahoo messenger under wine?

Try uninstalling wine and installing it again.  To tell you the truth I have never had such problems

---

### Post by jrmclaugh on 2007-06-05
yeah, i was trying to run it from the same folder and even typing in the full path in terminal.  still same error.

i can use gaim to access yahoo, but i want to get the SMS message capability.  gaim can't do it, as far as i can tell, and i'd be surprised if any of those others do, but i'll check.

thanks for the replys.

- James

---

### Post by scrooge_74 on 2007-06-05
Check Kopete, is suppose to be made for KDE but it works under GNOME, Kopete has webcam support that GAIM still lacks.

There are also some pluggins for GAIM which enable some other things, but did not play with those

---

