---
title: "Detecting why a Cron task is cutting off"
date: 2007-06-28
forum: General Help
---

### Post by feenster on 2007-06-28
Hi all,
I have a PHP script that I run as a Cron task every day, at 8am (on a Ubuntu 7.04 server). It is fairly simple, and basically does the following:

1) Grab a list of users from MySQL
2) Loop through, executing a "du -hs" shell command on their home folder, and inserts the data back into MySQL

At the moment, there are only 13 users to go through. For some reason, the Cron task stops on user 6 every day. If i run the script manually, it works fine, with no complaints. 

Is there any easy why to check why this is happening when run from the Cron?

Cheers,
  Matt

---

