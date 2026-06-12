---
title: "HPLIP Toolbox &quot;No System Tray Detected On This System&quot;"
date: 2013-05-11
forum: General Help
---

### Post by coljohnhannibalsmith on 2013-05-11
Hello,

I just upgraded to 12.10 and I got the following message on boot-up:

HPLIP STATUS SERVICE:
No system tray detected on this system.
Unable to start, exiting.

Please see attachment below:

---

### Post by fantab on 2013-05-11
Try reinstalling 'hplip' package.

---

### Post by coljohnhannibalsmith on 2013-05-12
Thank you for the suggestion; but it didn't work.

Hannibal

---

### Post by fantab on 2013-05-12
Did you install hplip-gui package?

---

### Post by oldfred on 2013-05-12
Are you installing from the repository or the much newer version from HP?

I had that error and ignored it for a while as I use gnome-panel and assumed it was related. But I think the latest update from HP fixed it. But I do not have that printer on my desktop so not sure now.

HP Deskjet 3520
[http://ubuntuforums.org/showthread.php?t=2109050](http://ubuntuforums.org/showthread.php?t=2109050)
HP's newest On this website you can download the HPLIP software which supports 2,211 HP printers on nearly any Linux distribution available today.
[http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html)
Ubuntu's older
sudo apt-get install hplip-gui
gksudo hp-setup
# new version
hp-upgrade

No system tray error:
open up the "startup applications" editor from the admin menu.
add a new program, for the command put:
sleep 10;/usr/bin/hp-systray

---

