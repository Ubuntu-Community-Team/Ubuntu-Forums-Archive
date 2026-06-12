---
title: "fglrz results in no shutdown"
date: 2007-06-25
forum: General Help
---

### Post by Tauhshi on 2007-06-25
When I enable the fglrx driver via xorg.conf, my computer refuses to shutdown, logoff, or restart. I then switched back to the ati driver, and it shuts down/reboots fine.

When I shutdown, the desktop dissapears, but the usplash (the Ubuntu Logo and progress bar) never show up, and my screen is just blank. And, it just sits there forever.

---

### Post by strabes on 2007-06-25
Could you be more specific? What guide did you use to install fglrx? I suggest using this one: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-d8c6fd05bce340dfc3ad483abf0e18997868540b](https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-d8c6fd05bce340dfc3ad483abf0e18997868540b)

Yes, the one for edgy.

---

### Post by Tauhshi on 2007-06-25
Uh, guide? I just used "sudo apt-get install xorg-driver-fglrx", and then added the "Composite Enable 0" line to my xorg.conf after changing "ati" to "flgrx:".

---

