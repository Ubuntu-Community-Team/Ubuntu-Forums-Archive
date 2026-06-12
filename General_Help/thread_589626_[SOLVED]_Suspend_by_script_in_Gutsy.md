---
title: "[SOLVED] Suspend by script in Gutsy"
date: 2007-10-24
forum: General Help
---

### Post by Greasyfingers on 2007-10-24
In Fiesty I found a script on the web (I'm no programmer) that would suspend the system. It seemed to work a bit better than using the built in suspend button, and could also be added to the end of other routines. But it doesn't do anything in Gutsy. 

Anyone got any clues how to make this work with 7.10, please?
```
#/bin/bash
#suspend script

dbus-send --session \
--dest=org.gnome.PowerManager \
--type=method_call \
--print-reply \
--reply-timeout=2000 \
/org/gnome/PowerManager \
org.gnome.PowerManager.Suspend
```

---

### Post by Greasyfingers on 2007-11-09
I found the answer, include it here in case anyone is interested:

```
#/bin/bash
#suspend script

dbus-send --session \
--dest=org.freedesktop.PowerManagement \
--type=method_call \
--print-reply \
--reply-timeout=2000 \
/org/freedesktop/PowerManagement \
org.freedesktop.PowerManagement.Suspend
```

---

### Post by Craigus on 2007-11-09
Thanks, I'm looking for some way to suspend my desktop, but I get this error when I run the script:

> # /usr/bin/snooze.sh
Error org.freedesktop.DBus.Error.Spawn.ChildExited: Process /usr/bin/gnome-power-manager exited with status 0
# 


Any thoughts ?

---

### Post by Greasyfingers on 2007-11-10
I'm not sure my understanding of things is up to problem solving yet! I found the original routine on a long forgotten website, and the modification to make it work in Gutsy came as a result of reading a post on another forum and a bit of trial and error.

I can run the routine directly in a terminal, or by setting up a launcher to call a script, and it works fine for me. I keep the script in a folder in my home directory, rather than in /usr/bin/ with permissions all set for the user to run it. However, I've also just tried it from /usr/bin/ and it worked OK.

Can anyone else help? Maybe I put the [SOLVED] flag up too soon.

Edit to add: Actually, running it from /usr/bin/ doesn't seem to be straightforward. For me, trying to run the script from a terminal doesn't work, though clicking on it directly does. Maybe try a different directory?

---

