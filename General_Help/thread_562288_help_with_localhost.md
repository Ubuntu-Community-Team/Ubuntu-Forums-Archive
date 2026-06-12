---
title: "help with localhost:"
date: 2007-09-28
forum: General Help
---

### Post by bazz on 2007-09-28
How can I add a extra display? I can logon the first display no problems. When I login the second I get an error.
I am using ltsp and need two displays running an environment. I get the error in my xsession-errors, The application gnome-session lost its connection to the display localhost:10:0 (thats because its in use by my firs session.) So I need to add an extra display. Any advice or help out there?

---

### Post by prince_niceguy on 2007-09-28
are you trying to create the new session on the same box or from different box?

In the login window there is option to configure if the login of the same user be allowed or not.

i see that your session is giving error on localhost:10:0. I think it should be localhost:0.0

can you confirm the same.

Thanks
Mehul

---

### Post by bazz on 2007-09-28
Its on the ltsp thin client, so yes I am trying to create the new session on the same box.
 I have both ctrl+alt+f5 and ctrl+alt+f6 start ldm. I can only log on one at at time. for example
I can log on to ctrl+alt+f5 and enter a gnome session, but I can not login to ctrl+alt+f6 untill I log out of ctrl+alt+f5.
So I think I need to add an extra display for the thin clients second session.

For the server its self it is localhost:0

I think the thin clients run on 10

---

