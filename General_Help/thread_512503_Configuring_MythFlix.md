---
title: "Configuring MythFlix"
date: 2007-07-29
forum: General Help
---

### Post by Billrobt on 2007-07-29
[SIZE="4"]I am following the community documentation on configuring MythFlix.   When I get to configuring Mysql and type in the command Mysql  -u root -p it asks for a password and I enter my password it always comes back Access denied (Using password: Yes).  My account is the only account on the PC.  Any suggestions or reasons why this is failing?  Thanks for your help.[[/SIZE]

---

### Post by FluffyElmo on 2007-07-29
By default the mysql packages don't have a password set, so when it asks for a password just hit enter. In general mysql security and user accounts are completely separate from your regular Ubuntu accounts. 

In case you've actually set a mysql password and have forgotten it, here is how to reset the root password:
[http://www.debian-administration.org/articles/442]("http://www.debian-administration.org/articles/442")

---

### Post by Billrobt on 2007-07-29
Thanks for your help!  Figured it had to be something simple.

---

