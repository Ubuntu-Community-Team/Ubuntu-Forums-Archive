---
title: "'System program problem detected' popup in Ubuntu 18.04"
date: 2020-02-25
forum: General Help
---

### Post by davy jones on 2020-02-25
I'm repeatedly getting the 'System program problem detected' popup in 18.04. When I checked the crash logs using ls -l /var/crash/ this is the output I got:

```
total 118956
-rw-r----- 1 gdm     whoopsie 20796272 Feb 24 14:44 _usr_bin_gnome-shell.121.crash
-rw-r----- 1 bhaskar whoopsie  3994828 Feb 24 18:41 _usr_bin_nemo.1000.crash
-rw-r----- 1 bhaskar whoopsie 94847003 Feb 25 19:07 _usr_bin_vlc.1000.crash
-rw-r----- 1 gdm     whoopsie  2162194 Feb 24 14:44 _usr_bin_Xwayland.121.crash

```

Do I need to be worried?

---

### Post by sdsurfer on 2020-02-25
Worried, no, if your system appears to be functioning normally. The cause appears to be multiple sources, I haven't found a definitive answer yet. Recent post:

[https://ubuntuforums.org/showthread.php?t=2437225](https://ubuntuforums.org/showthread.php?t=2437225)

---

### Post by CatKiller on 2020-02-25
One thing to be aware of is that the system is *supposed* to ask you to upload a report about the crash and then not bother you again. Sometimes it doesn't manage to do the latter: it keeps asking about the same reports over and over again. If that happens you can just delete those files from /var/crash. If you get another crash you'll get another report, but it will stop giving the prompt about the old ones.

---

