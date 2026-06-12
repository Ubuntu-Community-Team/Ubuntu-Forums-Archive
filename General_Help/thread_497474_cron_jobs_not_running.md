---
title: "cron jobs not running?"
date: 2007-07-10
forum: General Help
---

### Post by IndieRockSteve on 2007-07-10
On Feisty. My crontab is:
> 
# /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file
# and files in /etc/cron.d. These files also have username fields,
# that none of the other crontabs do.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow user  command
17 *    * * *   root    cd / && run-parts --report /etc/cron.hourly
27,57 * * * *   mythtv  cd / && run-parts --report /etc/cron.mythhourly
25 6    * * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
25 6    * * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.mythtv)
47 6    * * 7   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly)
52 6    1 * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )
#


but running ***crontab -u root -l***  says "no crontab for root" and the two lines I added don't run at the times they should.

---

### Post by EndPerform on 2007-07-10
How did you add to the crontab?  Did you use crontab -e, or did you edit /etc/crontab?  Generally it's best to update cron via crontab -e.

---

### Post by IndieRockSteve on 2007-07-10
I just edited it with nano, like I've done on every other linux box I've used in the last few years.

of course, running 'sudo crontab -e' comes up with a blank crontab...

---

### Post by evaldas on 2007-07-10
/etc/crontab is not root's crontab. it's a system-wide crontab as the first line says.

Root's crontab is located in /var/spool/cron/crontabs/root

And when you run **sudo crontab -u root -l** and it says "no crontab for root", well, that is right, because there is really no crontab for root.

Why your lines doesn't run from /etc/crontab, I don't know. Try adding those lines to the root's crontab through **sudo crontab -e**

just my 2 cents

---

### Post by IndieRockSteve on 2007-07-11
> **evaldas said:**
> /etc/crontab is not root's crontab. it's a system-wide crontab as the first line says.

Root's crontab is located in /var/spool/cron/crontabs/root

And when you run **sudo crontab -u root -l** and it says "no crontab for root", well, that is right, because there is really no crontab for root.


I see/know that, but how do you use crontab -e to edit the systemwide crontab?

> **evaldas said:**
> Why your lines doesn't run from /etc/crontab, I don't know. Try adding those lines to the root's crontab through **sudo crontab -e**


I thought of that yesteday as well and added them to the mythtv users crontab with no such luck.

It seems as though the normal cron folders are being run, just not my mythtv ones. they have the same permissions and user.

---

### Post by mannheim on 2007-07-11
What are the filenames of the scripts in the folder /etc/mythtv.hourly ?

The "run-parts" command will only run scripts whose names contain a limited set of characters (I think its letters, digits, underscores and hyphens). If the file name of a script contains a period, for example, then it won't get run. This *might* be the problem

---

### Post by IndieRockSteve on 2007-07-15
> **mannheim said:**
> What are the filenames of the scripts in the folder /etc/mythtv.hourly ?

The "run-parts" command will only run scripts whose names contain a limited set of characters (I think its letters, digits, underscores and hyphens). If the file name of a script contains a period, for example, then it won't get run. This *might* be the problem

AH! that might be it, the file not running has .sh in the name, I'll remove that and see what happens.

thanks!

---

### Post by IndieRockSteve on 2007-07-15
that seems to have been it! the script i was checking if running now seems to be running fine.

thanks!!

---

