---
title: "Why is &quot;admin&quot; a reserved username in 6.10?"
date: 2006-11-10
forum: General Help
---

### Post by danfluidmind on 2006-11-10
Could someone please explain why the username "admin" is suddenly reserved in Ubuntu 6.10? It seems like that username is fairly commonly used to have a separate user account for doing sysadmin stuff (as opposed to your day-to-day user account). Yet now I can't make a user named "admin" when I install a new server using 6.10.

And what about upgrading a 6.06 system that already has an "admin" username? Is that gonna cause problems for whatever the new reserved admin user is being set aside for?

--Dan

---

### Post by foxmulder881 on 2006-11-10
You should never create a user named Admin for security purposes. I suggest that's why 6.10 won't allow it.

It's the first username that hackers try when attempting to break into a network.

---

