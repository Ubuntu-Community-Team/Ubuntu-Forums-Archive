---
title: "Error at startup."
date: 2007-10-28
forum: General Help
---

### Post by exploder on 2007-10-28
Does anyone know how to stop this from happening?

There was an error starting the GNOME Settings Daemon. 

Some things, such as themes, sounds, or background settings may not work correctly. 

The last error message was: 

Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken. 

GNOME will still try to restart the Settings Daemon next time you log in.

I get this error fairly often and was wondering if anyone knew a solution?

---

### Post by strabes on 2007-10-28
I don't know how to prevent it from happening but after it happens you can simply restart the gnome-settings-daemon by hitting alt+f2 and typing in "gnome-settings-daemon"

---

### Post by exploder on 2007-10-28
I edited my /etc/hosts/ file, just added the computer name and it seems to be an improvement. Time will tell...

---

