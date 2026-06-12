---
title: "[SOLVED] suspend not working after starting x11 app when resuming"
date: 2008-03-14
forum: General Help
---

### Post by NEI on 2008-03-14
I'm trying to start irxevent after a resume. I stop it when suspending and start it with this script in /etc/acpi/resume.d/990-htpc-stuff.sh
```

#!/bin/sh

export DISPLAY=":0.0"
export XAUTHORITY=/home/steph/.Xauthority
/usr/bin/irexec -d /home/steph/.lircrc
/usr/bin/irxevent /home/steph/.lircrc

```

Everything works, except that i can only sleep and resume the pc once, then i get following when trying to suspend:

```

steph@HTPC:~$ /usr/bin/gnome-power-cmd.sh suspend
Suspending
Error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

```

I think that it has something to do with .Xauthority, but no idea what? If i just start irexec and comment the exports, i can suspend and resume as many times as i like.

---

### Post by NEI on 2008-03-18
Ok, fixed! Had to sleep for 5 seconds before doing this. No idea why...

---

