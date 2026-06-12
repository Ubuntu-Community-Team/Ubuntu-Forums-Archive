---
title: "Dbus doesn't work !"
date: 2006-12-17
forum: General Help
---

### Post by roidelapluie on 2006-12-17
Hello,

For a month Dbus won't work!

When I try to launch a minimal program, like

```
#!/bin/bash
#./waterping.sh 0 0
#If you want to ping the coordinates x0, y0
dbus-send --type=method_call --dest=org.freedesktop.beryl /org/freedesktop/beryl/water/allscreens/point org.freedesktop.beryl.activate string:'root' int32:`xwininfo -root | grep id: | awk '{ print $4 }'` string:'amplitude' double:1 string:'x' int32:$1 string:'y' int32:$2
```

I've got this error:

```
jux@jux-desktop:~$ waterping.sh 10 10
Failed to open connection to session message bus: Failed to connect to socket /tmp/dbus-sKV4BWrcDK: Connection refused

```

It's very boring and i've tried to reinstall the dbus package.
When i restart the computer and try again, I get the same error, and after rebooting the name of the socket don't change.

Thank you. Appologies for my English.

---

### Post by hikaricore on 2006-12-17
I've been getting random dbus errors for awhile now that I think of it too.  Doesn't seem to cause any problems, just strikes me as odd.  Thought it was just me :P

Seems like it's been about a month here as well, other than that Edgy is running perfect.

---

### Post by roidelapluie on 2006-12-17
thanks

i think the poblemis that the spocket doesn't exist...

how to recreate it?

---

