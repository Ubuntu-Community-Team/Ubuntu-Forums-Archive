---
title: "Sound quit working suddenly"
date: 2007-01-19
forum: General Help
---

### Post by mssever on 2007-01-19
I recently upgraded from Dapper to Edgy (finally!). A day or two after the upgrade, when I booted my machine, there was no sound. It was working perfectly before that reboot, and as far as I know I didn't change any sound-related settings (I was mostly fiddling with Beryl)--since the whole system is quiet, it couldn't have been Beryl, which runs as my normal user, not root.

When I boot from the live CD (both Dapper and Edgy), I get sound just fine. I couldn't find anything meaningful that stuck out to me in the logs. I do have the following in /var/log/kern.log: ```
Jan 19 06:25:24 scott-laptop kernel: [17179604.428000] AC'97 1 does not respond - RESET
Jan 19 06:25:24 scott-laptop kernel: [17179604.444000] AC'97 1 access is not valid [0xffffffff], removing mixer.
Jan 19 06:25:24 scott-laptop kernel: [17179604.444000] ali mixer 1 creating error.
``` However, that same error appears in kern.log on the live CDs without impacting sound playback, so I don't think it's significant.

I don't know much about troubleshooting audio issues. Can someone point me in the right direction? I depend on sound ](*,)

EDIT: By the way, when the sound first quit working, I checked the volume and strangely it was all the way down. I turned it back up, but to no avail.

---

### Post by mssever on 2007-01-20
bump

---

### Post by mssever on 2007-01-21
bump

---

### Post by mssever on 2007-01-25
I don't know why, but after I installed kubuntu-desktop, I had sound (even in Gnome). I've now removed kubuntu-desktop and still have sound. So apparently something that got installed fixed whatever was wrong. I wish I knew what was wrong though...

---

### Post by kah00na on 2008-02-23
Mine quit working suddenly too.  I was watching a movie in movie player and the right sound channel cut out. Then about 10 seconds later, the left cut out.  I rebooted and still no sound.  My sound is turned up all the way too.  I'm not sure what I will do.  Reinstall something I guess.

---

