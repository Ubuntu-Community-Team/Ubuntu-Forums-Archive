---
title: "multimedia codecs"
date: 2013-10-06
forum: General Help
---

### Post by MagisterDixit on 2013-10-06
How do I update my multimedia codecs?

---

### Post by mastablasta on 2013-10-07
what do you mean update? do you mean upgrade?

Because all updates are provided regulary with all other stuff (bug pathces, security pathces...) via update manager.

---

### Post by MagisterDixit on 2013-10-07
All I know is VLC once worked and now it doesn't. I have updated and upgraded everything I know how and am now reduced to drawing at straws. Ubuntu is up to date and VLC is up to date. I was wondering if the problem was in the codecs. I'm still fairly new to Linux.

---

### Post by Copper_City on 2013-10-07
Are you trying to play the same file that played before? Explain what you mean by "now it doesn't work". Any errors?

---

### Post by oldos2er on 2013-10-07
> **FpCrPnW said:**
> All I know is VLC once worked and now it doesn't. I have updated and upgraded everything I know how and am now reduced to drawing at straws. Ubuntu is up to date and VLC is up to date. I was wondering if the problem was in the codecs. I'm still fairly new to Linux.

```
sudo apt-get update && sudo apt-get dist-upgrade
``` will get the latest and greatest.

To troubleshoot vlc, start it in a terminal (Ctrl-Alt-t): ```
vlc
``` It may show some messages that help pin down the problem.

---

