---
title: "Runnung a bash script when on &quot;Switch User&quot;"
date: 2015-04-09
forum: General Help
---

### Post by ch1mp on 2015-04-09
Hi,

I've had my first dabbel with bash and got a working script going for each user on session start which checks if a NAS share is mounted and if it is unmounts it and mounts as the current user. This works great but now I have a problem, on the first "Switch User" the script is executed as the session for the new user starts. Switching back however the drive is mounted as the previous user, running the script works so it appears that what works for the session start (.config/autostart) doesn't handle this user switching and I guess that makes sense.

Sooooo, question is, how to run my little script again when a session restarts for each user after a "Switch User" happens?

Thanks in advance for any pointers, I've looked for a list of events I could hook in to but had no luck so I guess I'm not using the right terminology for Ubuntu?

---

### Post by ch1mp on 2015-04-10
Me again :)

Is there a better place to ask this? I see lots of views but no answers...

---

### Post by Holger_Gehrke on 2015-04-10
Switching users produces a lot of activity on the dbus. You might be able to do something using 'gdbus' or 'dbus-monitor' on the system dbus on the path '/org/freedesktop/login1' and the interface 'org.freedesktop.login1.Session'

---

### Post by CaptainMark on 2015-04-10
What's your overall goal here. If I were in this situation I wouldn't have the share remount each time someone logs out, this seems excessive. You would be better investing a little time into setting up correct user directories and having the overall nas just mounted by one (main/admin) user. Alternatively the nas would be owned by the main user and permissions would be applied to other users via groups.

---

