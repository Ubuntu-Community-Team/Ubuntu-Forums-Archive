---
title: "Printer Shared from Lubuntu requires authentication; wont print! How do I avoid this?"
date: 2015-08-18
forum: General Help
---

### Post by 777funk on 2015-08-18
I type in the username and password from the machine accessing the printer on the Lubuntu machine and it just pops the box back up. I don't want any password authentication for my shared printer on my Lubuntu machine. What am I doing wrong?

---

### Post by 777funk on 2015-08-18
Edit, had to change the

/etc/samba/smb.conf 

to allow guest access (from = no to = yes) 

and now all is fine.

---

