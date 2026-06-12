---
title: "Kubuntu Login Screen Doesn't appear"
date: 2007-11-01
forum: General Help
---

### Post by CodeWarMonkey on 2007-11-01
I was using Kunbuntu 7.04 and followed the steps in thread: [Howto: Simple kernel upgrade (Feisty or Edgy)]("http://ubuntuforums.org/showthread.php?t=511974") to upgrade to Gutsy (7.10).

I used the Python script and it appears to have messed up my login screen or X server settings. My computer appears to boot as it should but when the login screen should appear, I get a blank screen that I can type in but nothing happens. I looked at the /var/log/Xorg.0.log and the last entry is "Fatal server error: no screens found".

Anyone know what might have happened to mess up my X server?

Thanks.

---

### Post by CodeWarMonkey on 2007-11-01
Does anybody know what I can do or where I can find help for this?

---

### Post by perlluver on 2007-11-01
Could have to do with your video card settings.  Run sudo dpkg-reconfigure xserver-xorg.  That should fix any video problems.

---

