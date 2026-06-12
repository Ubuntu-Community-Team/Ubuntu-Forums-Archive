---
title: "Blank screen after 10mins; halfway solved"
date: 2007-11-08
forum: General Help
---

### Post by tokinux on 2007-11-08
I discovered a fix for the blank screen after 10 minutes issue, located here: _[http://ubuntuforums.org/showthread.php?p=2160598](http://ubuntuforums.org/showthread.php?p=2160598)_

However.. while my screensaver preferences still work in gnome-screensaver.. the power management options do not. The code that I added to my xorg.conf to fix the 10 minute blank screen issue is overriding my standard power management preferences.

I think that this issue of xgl running on display:1 is also affecting my ability to get my dual-monitor setup working correctly.. as I have to consistently "export display=:0" to get aticonfig to recognize my monitors after every restart of X. Anyone know of a solution? Or how to get my xgl session to boot using display:0 instead of :1?

Running Gutsy w/gnome.

---

