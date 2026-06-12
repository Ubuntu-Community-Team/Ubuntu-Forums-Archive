---
title: "[SOLVED] Root Password"
date: 2008-01-22
forum: General Help
---

### Post by Raccoon1400 on 2008-01-22
My root password wasn't working in the logon screen, but it would work when asked for admin password in my user. I changed it to password B and then back with system>admin>users and groups. Password A now works only for logon, and B only works for admin duties within my user. I have also had this problem on previous installations.
How can I get password A to work for logon and admin duties?

---

### Post by bodhi.zazen on 2008-01-22
the root account is locked by default and Ubuntu uses sudo.

so you would need to enable the root account and then enable root logins.

with a default install the password for sudo and admin tools is your user log in, although your user must be a member of the admin group.

---

### Post by Raccoon1400 on 2008-01-22
I got all tasks to require the same password. I changed my user password, and now that password works for everything.

---

