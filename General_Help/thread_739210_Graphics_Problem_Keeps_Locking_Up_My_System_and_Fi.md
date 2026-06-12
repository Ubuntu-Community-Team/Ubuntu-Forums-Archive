---
title: "Graphics Problem Keeps Locking Up My System and Filesystem is Damaged"
date: 2008-03-29
forum: General Help
---

### Post by GenuineXP on 2008-03-29
Argh, I've been having this problem ever since I first tried Ubuntu and have yet to get any help. Any ideas are *greatly* appreciated.

My system always crashes when I play (3D) games like Doom 3 and Sauerbraten. It's really only a matter of time. Usually these games last about 25 minutes on average, but as of late they seem to crash almost immediately (I get about five minutes). The whole screen just freezes in place and becomes completely unresponsive. In some cases, pressing Ctrl+Alt+Backspace successfully restarts X and I can kill the old process after logging back in. Sometimes, the entire system is unresponsive and I need to do a hard reset.

A couple of days ago, one of these crashes somehow destroyed my filesystem. Upon booting, I got tons of cryptic error messages, failures, and complaints about unreadable files or files that don't exist. Another hard reset seemed to miraculously eliminate these errors, but after a forced disk check today I was hit with another slew of strange error messages. Note that the check was started after my system once again locked while playing Sauerbraten for no more than five minutes!

I'm running Gutsy and have an NVIDIA GeForce 6600 GT video card. I know that NVIDIA cards tend to be better supported than ATI cards on Linux systems, and I believe since I own a ThinkPad with a terrible ATI graphics adaptor, but this is ridiculous. My system seems completely stable in any other situation except for 3D applications (particularly the games mentioned).

Is there something I can do to get to the bottom of this? I'm backing up my data now and thinking about installing Fedora 8 (I already downloaded the live CD). Can anyone recommend this distro? Since it's much more cutting edge than Ubuntu, I'm hoping it'll offer some better drivers or other software that may improve graphics stability. RPM FTW.

I'd prefer to stick to Ubuntu for now, but if I can't figure this out then I'll have to try something else.

Thanks! I could really use some help with this. I've been dealing with this for a year now and it's a pain (same thing happened in Feisty).

---

### Post by pointone on 2008-03-29
Crashes that only occur after running a 3D application for a short while usually would lead me to suggest overheating video card / failing PSU. Check your GPU temperature while running a simple 3D benchmark like glxgears for a few minutes.

---

### Post by GenuineXP on 2008-03-29
What would be the best (easiest) way to check the GPU temperature?

Thanks for the suggestion. :)

---

