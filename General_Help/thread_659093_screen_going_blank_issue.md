---
title: "screen going blank issue"
date: 2008-01-05
forum: General Help
---

### Post by kashey_be on 2008-01-05
hey all,
there is a "feature" in X called blank screen saver.
It is being set by typing the command "xset s tttt" where tttt stands for the time.
I tried to disable it using "xset s off" which works very well until the next reboot.
I also added it to my .bash_profile and yet it being overridden by something and keep reseting to 310.
this setting can be viewed using "xset q" and looking at this section:

Screen Saver:
  prefer blanking:  yes    allow exposures:  yes
  timeout:  0    cycle:  0

does anybody know where/how can I disable it for good?

---

