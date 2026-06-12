---
title: "Problems running cron jobs"
date: 2007-04-20
forum: General Help
---

### Post by NaughtyusMaximus on 2007-04-20
I need a hand getting my cron jobs to work properly under XUbuntu 6.06.  I have some scripts that need to run every 10 minutes by root, so what I have done is the following:

Placed the scripts into /opt/scripts/myscript
chmod u+x /opt/scripts/myscript

sudo crontab -e

10 * * * * /opt/scripts/myscript

If I run the script manually as root, it works as advertised, but it is not running when I have it in a cron job as above.  Is there something obvious that I'm missing here?  I did the same thing under CentOS, and it is working without issue.

---

