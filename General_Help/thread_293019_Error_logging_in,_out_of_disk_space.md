---
title: "Error logging in, out of disk space"
date: 2006-11-04
forum: General Help
---

### Post by hemple on 2006-11-04
I am having difficulty logging into my laptop. I run Ubuntu 6.06 (Drake). and an error is popping up after i enter my password.

along the lines ..." you have been loogged out while bo logged in for less that ten seconds. this may be in part to an installation error. or you may be out of disk space."

i have been runninng linux for about three months now so it seems unlikely for it to be about the installation. And I did click on more details and it said near the bottom..that i was out of disk space.but this seeems very wrong. i should have almost 30 GB free.

what do i do?

thanks -dan

---

### Post by jordilin on 2006-11-04
It's really weird. I would boot with a Linux live cd and I would take a look at system logs /var/log/messages to see why you can't log in. Perhaps this is sth related to the filesystem (permissions, type of format, etc...)

---

### Post by chriscando on 2006-11-04
My school account give me the same error, to bypass I choose to login to a failsafe terminal and then type gnome-session. This works and gets me in okay, tho kinda annoying to do everytime. In your case if you can at least get a failsafe terminal you can try something like 'df -h' to see if indeed you are out of disk space.

---

