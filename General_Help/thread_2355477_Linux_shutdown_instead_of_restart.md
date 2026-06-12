---
title: "Linux shutdown instead of restart"
date: 2017-03-13
forum: General Help
---

### Post by ganduumar on 2017-03-13
Hello

I'm having issue with Linux. I use cron and put a line of script, to "shurtdown -r now" on 8:50 and 20:50, every day.
The unit runs the script, but seems to only shut down, not restart. Is there some kind of thing done wrong or what should I do differently?
I searched the forums and webs, but couldn't find anything that helped. Did update/upgrade, but still issue remains.

Any advice helps!

---

### Post by oldrocker99 on 2017-03-13
Welcome to the forums!

The command to restart is simply this:```
reboot
```

No **sudo** is needed, but you probably knew that.

---

### Post by efflandt on 2017-03-13
You might try "shutdown -r now &" or "reboot &" (which is the same thing). That is just a guess because I had to use the "&" to run in the background when trying to shut down a system remotely, otherwise the shutdown would stop proceeding when it killed sshd for my connection (maybe killing crond interferes).

But I have had a couple of computers that did not always seem to reboot properly as though something is not resetting properly. The screen goes dark, drive and fans remain running, but nothing else happens forever (doesn't actually reboot or shutdown). So I got into the habit of shutting down and cold booting.

---

