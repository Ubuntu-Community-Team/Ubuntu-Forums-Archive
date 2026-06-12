---
title: "Can't remove notification applet in Saucy 13.10"
date: 2014-02-10
forum: General Help
---

### Post by amadis2009 on 2014-02-10
Just upgraded to 13.10 and I'm now getting an envelope icon in my panel whenever I play music or get an email. I already have other means of getting notifications so this is redundant. How do I remove this? I already tried uninstalling indicator-mesages and indicator-applet-complete. Didn't work. I'm using Gnome Flashback.

---

### Post by amadis2009 on 2014-02-10
Found my own answer here. [http://askubuntu.com/questions/367961/no-notifications-from-notify-osd-on-13-10/368447#368447](http://askubuntu.com/questions/367961/no-notifications-from-notify-osd-on-13-10/368447#368447)
I needed to kill the notification-daemon and then prevent it from restarting at the beginning of each session.

---

