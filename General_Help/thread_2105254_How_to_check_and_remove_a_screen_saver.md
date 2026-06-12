---
title: "How to check and remove a screen saver?"
date: 2013-01-15
forum: General Help
---

### Post by PeterTaps on 2013-01-15
Folks,

Environment: Ubuntu 12.04 minimal + Openbox.

I need to remove any screen saver that I may be running. Since I haven't specifically installed any gnome related packages, I am assuming I have xscreensaver and not gnome screen saver. How do I find out what screen saver I am actually running?

If I run the following command, I don't see any matching process.

$ ps -e | grep -i screen

Assuming I am running xscreensaver, would the following command work to remove this package?

$ sudo apt-get remove xscreensaver

Thank you in advance for your help.

Regards,
Peter

---

