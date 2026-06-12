---
title: "AcceptPathInfo On in apache2"
date: 2015-04-16
forum: General Help
---

### Post by ELMIT on 2015-04-16
Moodle requires: AcceptPathInfo On 

I added the following line in /etc/apache2/conf-available/security.conf

#
# Accept pathname information that follows an actual filename into the
# PATH_INFO environment variable.
#
AcceptPathinfo On 


restarted apache and still moodle complaints that the check failed.

I added to the /etc/apache2/apache2.conf the same, restarted apache and still moodle complaints that the check failed.

What am I missing?

---

