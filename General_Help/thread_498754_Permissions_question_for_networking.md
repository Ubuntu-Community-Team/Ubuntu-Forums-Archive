---
title: "Permissions question for networking"
date: 2007-07-11
forum: General Help
---

### Post by jbysmith on 2007-07-11
Have a question about permissions and networking.  Using Delphi 7 with Wine with good results.  However, I installed the Indy sockets library, and I'm running into a problem.

When I try to run a program that access the network (TCP or UDP) it comes back with winsock error 10013, permission denied.  It does work properly if I use sudo however.

I'm sure it's a simple chown or chmod issue, but not sure where to look.  Any suggestions?  Thanks

---

### Post by jbysmith on 2007-07-11
Never mind, found my problem.  Was due to using a low port number, and didn't know that's not permitted for regular users.

---

