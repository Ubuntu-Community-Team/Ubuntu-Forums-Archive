---
title: "Root sending Apache Logs in Email?"
date: 2012-10-16
forum: General Help
---

### Post by DaleHutch1 on 2012-10-16
Greetings!!!

I have been running an Ubuntu 21.04 server for many months now. Recently the root started E-mailing me Apache logs. I did not make any changes to the system. Where could I go to see what has changed? I checked the CRON jobs and there is nothing in there to suggest sending me logs.

Thanks

---

### Post by greenpeace on 2012-10-16
Hey!

Do you have logrotate running on your box?  Could it be that sending you the emails?

conf file should be here: **/etc/logrotate.conf**

Hope that helps.

G

---

