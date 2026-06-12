---
title: "ubuntu os restarts, not the computer but the os"
date: 2007-01-26
forum: General Help
---

### Post by Tucatts on 2007-01-26
Interesting thing lately. I have the OS up and running just fine and after about three hours or so Ubuntu on it's own mind you, goes right back to the log in screen. I can log back in with no trouble. I have checked this computer out as to temperature and it is not running hot. This system and case is dual booted with another HD with XP and XP never does this. Again the computer is NOT rebooting, just the OS. Any thoughts? 
Thanks,
Tucatts

---

### Post by Ramses de Norre on 2007-01-26
Not even the OS, just your X server. Look for error messages in ~./xsession-errors and /var/log/Xorg.0.log.old right after it has done it again and post them here.

---

### Post by Tucatts on 2007-01-26
AH, thanks, I am a newbie and not sure where I would find that error message. However, could I not just reconfigure x server again? Use dpkg-reconfigure xserver-xorg startx. Or use sudo apt-get update then sudo apt get upgrade . Thanks

---

### Post by Ramses de Norre on 2007-01-26
You can indeed try **sudo dpkg-reconfigure -phigh xserver-xorg** it might help.

---

