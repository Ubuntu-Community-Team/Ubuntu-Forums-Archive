---
title: "crontab every five minutes. bug?"
date: 2005-10-28
forum: General Help
---

### Post by Sparrow on 2005-10-28
I did a search and came back with nothing, so I hope this isn't a repeated post.

I setup a test installation of MRTG on Breezy, and was attempting to setup a cron job to run every five minutes using the following command in crontab:

*/5 * * * * env LANG=C mrtg /var/www/mrtg/cfg/mrtg.cfg --logging /var/log/mrtg/mrtg.log

But, after I save it I get an error "bad minute errors in crontab file, can't install."

There are no other entries in my crontab.  If I manually edit my crontab file, cron has no problems executing every five minutes.  And if I use crontab to add a second entry that runs every five minutes, there's not problem adding it.

S

---

### Post by Remmelas on 2005-10-28
0-59/5 * * * * env LANG=C mrtg /var/www/mrtg/cfg/mrtg.cfg --

will get you every 5 minutes

---

