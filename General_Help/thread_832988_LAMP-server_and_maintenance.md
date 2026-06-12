---
title: "LAMP-server and maintenance"
date: 2008-06-18
forum: General Help
---

### Post by The Keeper on 2008-06-18
I may have to set up a lightweight Ubuntu LAMP-server to host forums, wiki, etc random stuff for an active web community.

Initial set up aside, I'm more concerned about maintenance.

Certainly security updates are the most important thing, but automatic updates are shunned upon because real server admins are supposed to test these updates before applying them on production environment. And for a good reason I guess.

The problem is that unless I set up automatic updates, nobody is going to do the maintenance for me and I may not be able to when there is need to.

So either it is automatic updates or I risk the server to be updated maybe twice a year. Which is the worse case? Or is there a better solution, other than buying managed server from a hosting company which is way too expensive.

Anyway, if I set up a cron job for apt-get, what are the chances of updates actually breaking something? Apparently custom config files may be in danger, is this true?

Now another question, if Apache, PHP, MySQL, ProFTPD or any other running application receives an update, does the updater automatically restart the app?

Basically I'm just trying to find out how little manual maintenance an Ubuntu server can stay up operational and secure.

Thanks for your insights. :)

---

### Post by The Keeper on 2008-08-20
*bump*

---

