---
title: "BLACK SCREEN after logo (black login screen)"
date: 2015-01-28
forum: General Help
---

### Post by albertredneck on 2015-01-28
Hi guys, I'm desperate looking for help on this problem.

I accidentally pulled the power cable from my laptop PC while the battery was removed. After that, I tried to log in again BUT I got the black screen of death! No new software was installed (but maybe there were some updates applied in the last session). My computer still can boot into Windows 8. 

I have an ASUS N56V with latest nvidia drivers (xorg-edgers).

Any suggestion?

---

### Post by mansonfan78 on 2015-01-28
Sounds like the video driver isn't loading.  Try using the "nomodeset" video option - [http://askubuntu.com/questions/38780/how-do-i-set-nomodeset-after-ive-already-installed-ubuntu](http://askubuntu.com/questions/38780/how-do-i-set-nomodeset-after-ive-already-installed-ubuntu) If that let's you in, you could try going to "additional drivers" and selecting a different option and then rebooting.  After that you could try going back to the latest driver (basically reinstalling it).

---

