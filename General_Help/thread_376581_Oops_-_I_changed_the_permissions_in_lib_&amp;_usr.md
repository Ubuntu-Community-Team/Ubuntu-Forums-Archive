---
title: "Oops - I changed the permissions in /lib &amp; /usr"
date: 2007-03-05
forum: General Help
---

### Post by GlitchNZ on 2007-03-05
I cleverly managed to alter the permissions in my /lib and /usr folders. After loosing X altogether and then battling with the loss of the SuperUser I'm almost back up and running. The only problems I'm having is that some applications won't run correctly or at all.

How to I reset the /lib and /usr permissions so that my system is back to normal?

---

### Post by kidders on 2007-03-05
Hi there and welcome,

/usr and /lib account for a large proportion of a Linux system, so undoing a permissions change would be quite an undertaking! Unfortunately, you can't afford any guesswork when it comes to the access privileges for these files ... mistakes can make your system unstable, and vulnerable to security issues. For this reason, Ubuntu makes it quite a tricky thing to do by accident.

Depending on exactly what the new privileges you've assigned to all your files are, I would seriously consider reinstalling the OS. For me, the prospect of having even one permissions bit out of place on critical system files would be unacceptable. :-(

Having said all that, I would be happy to try to help you sort this out *without* a reinstall. In theory, any application with Ubuntu-specific knowledge of the default system permissions settings could take care of this for you. I don't know of one (maybe another poster will), so if it were me, I would try to throw together a quick script to do the job, based on a clean permissions set from someone else's computer.

Let me know if you'd like me to go into more detail.

---

