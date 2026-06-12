---
title: "CRON error running script"
date: 2004-11-07
forum: General Help
---

### Post by grj on 2004-11-07
I have written a script to create a text file and e-mail the results to my work e-mail. The script works fine from the command line. But when I set up a cron job to execute the script I get the following error in my mail.err log:

Nov  7 09:29:02 debiantraveller sSMTP[3721]: 530 authentication required - for help go to [http://help.yahoo.com/help/us/mail/pop/pop-11.html](http://help.yahoo.com/help/us/mail/pop/pop-11.html)

The script has access to the user name and password as it runs fine from the command line. Why does it fail from cron? I used cron -e for my user account to set up the cron job.

Fix: I had to add PATH=/usr/sbin:/usr/bin:/bin:/home/*userdir* to the cron file.

Thanks,

grj

---

