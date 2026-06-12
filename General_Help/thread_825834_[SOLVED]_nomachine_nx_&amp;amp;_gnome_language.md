---
title: "[SOLVED] nomachine nx &amp;amp; gnome language"
date: 2008-06-11
forum: General Help
---

### Post by francky_51 on 2008-06-11
Hi all,

I have just installed nx on my pc (hardy) and everything is working fine except the session's language.
Even if Gnome is configured to use French language by default, when I opened a new session with nx it's in English.
I have modified my .dmrc but it's still not working.
[Desktop]
Session=default
Language=fr_FR.UTF-8

I will be very happy if one of you can give me some help.

Thanks

---

### Post by francky_51 on 2008-06-12
I found the solution :)

1) In /usr/NX/bin create a file called gnome.sh for example and give it the right permissions with a chmod 755 gnome.sh

```

#! /bin/bash
export LANG=fr_FR.UTF-8
/usr/bin/dbus-launch --exit-with-session gnome-session

```

2) Modify the end of the file node.cfg in /usr/NX/etc/ to launch gnome.sh
```

#
# Specify path and name of the command to start the GNOME session.
#
#CommandStartGnome="/usr/bin/dbus-launch --exit-with-session gnome-session"
CommandStartGnome="/usr/NX/bin/gnome.sh"

```

3) Restart the server

```

sudo /etc/init.d/nxserver restart

```

Et voila :)

---

