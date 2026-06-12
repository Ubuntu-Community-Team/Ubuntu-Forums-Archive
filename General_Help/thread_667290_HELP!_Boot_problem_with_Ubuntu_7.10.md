---
title: "HELP! Boot problem with Ubuntu 7.10"
date: 2008-01-14
forum: General Help
---

### Post by kyp446 on 2008-01-14
Allright well I am not sure whats going on. First off i was installing libraries when ubuntu started acting wierd (windows begain refusing to open) so i restarted, now my boot gets as far as the login screen but hangs there with the spinning loading icon for the mouse. I can move the mouse but even after extended waiting the login screen does not load. recovery mode boots fine (although i dont know enough command line yet to attempt to fix the problem). I have no problems with reformatting as long as i can get my files from the home folder. I tried using the Live CD but it refuses to let me move my files at all. Any help with either problem would be much appriciated.

~kyp

---

### Post by smartboyathome on 2008-01-14
Boot up to where the mouse starts spinning and then press control+alt+f1. are there any errors on that page?

---

### Post by kyp446 on 2008-01-14
there is a bunch of:
```
NetworkManager: <debug> ...
```
lines then the following:
```

* Starting NTP Server ntpd                                            [ OK ]
* Starting periodic command scheduler crond                           [ OK ]
* Enableing additional executable binary formats binfmt-support       [ OK ]
* Checking battery state...                                           [ OK ]
* Running local boot scripts (/etc/rc.local)                          [ OK ]
                                                                            [

```
and hangs there.

---

### Post by kyp446 on 2008-01-14
ok well i did somhow mannage to get this prompt: (side note Shinsengumi being my computer name)
```
Ubuntu 7.10 Shinsengumi tty1
Shinsengumi login:
Password:
Linux Shinshengumi 2.6.22-14-generic #1 SMP Tues Dec 18 08:02:57 UTC 2007 i686
```
eventually yeilding a terminal command prompt. but i am not sure what to do from there. I am fearful to attempt to much on my own as i dont feel comfortable with my skills with terminal linux yet.
looked up and tried Ctrl + Alt+ F7 to get back to gui only to end up again with the spinning busy cursor.

---

