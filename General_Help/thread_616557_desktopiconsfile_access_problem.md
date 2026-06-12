---
title: "desktop/icons/file access problem"
date: 2007-11-18
forum: General Help
---

### Post by dubstar on 2007-11-18
upgraded from feisty to gutsy, problems ever since.

load pc up, generally all is ok, desktop background and icons work, as does sccessing home folder from places.

after say ten mins, my desktop icons disappear, i cant access my home folder (nothing loads for about 5mins) right clicking on the desktop - no menu.


and sometime on reboot nothing is fixed, and also the desktop background isnt applied. and going into the appearances properties doesnt work, it just hangs if it loads the window......


also any program that accesses storage, local or networked also seems to load then hang....

---

### Post by cosborn72 on 2007-12-05
I am having the same symptoms.  It only occurs once every few logins, and restarting the computer fixes the problem.  It is annoying.

The no-background issue is, I believe, a compiz issue.  Go to appearance visual effects an change from whatever you have set to normal.  You could try some of the other settings.  I haven't tried them out, but choosing normal changes back to the default desktop from Compiz.

I will let you know if I figure out the file browsing thing.  I ran ps -ux and it stated that Nautilus is running in five different instances- but each includes an odd message.  


I don't know what this means, but someone out there might be able to translate it for us.;-)



<<<<<<<<<<<<<<<<<<<<<<<<<<<<
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND

chris     5652 62.0 10.2 163632 106124 ?       R    Dec04 904:10 nautilus --no-default-window --sm-client-id default2

chris     5794  0.0  0.0   2660   896 ?        S    Dec04   0:00 /usr/lib/nautilus-cd-burner/mapping-daemon

chris     8477  0.0  0.8  30764  8328 ?        S    08:32   0:00 nautilus --no-default-window --sm-client-id default2

chris     8718  0.0  0.8  30764  8344 ?        S    08:34   0:00 nautilus --no-desktop file:///media/cprcd01

chris     8761  0.0  0.8  30768  8336 ?        S    08:44   0:00 nautilus --no-desktop computer:

>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>

---

