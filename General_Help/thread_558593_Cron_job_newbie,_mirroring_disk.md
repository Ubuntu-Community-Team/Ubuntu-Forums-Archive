---
title: "Cron job newbie, mirroring disk"
date: 2007-09-24
forum: General Help
---

### Post by TheLemming on 2007-09-24
Hi,

I've set up rsync to mirror one drive to another, now I need to set it up in a cron job.

I've done some reading up and I've edited the /etc/crontab file and just added my job to the info already in there. Before I edited the file it looked like this:

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow user  command
17 *    * * *   root    run-parts --report /etc/cron.hourly
25 6    * * *   root    test -x /usr/sbin/anacron || run-parts --report /etc/cr
47 6    * * 7   root    test -x /usr/sbin/anacron || run-parts --report /etc/cr
52 6    1 * *   root    test -x /usr/sbin/anacron || run-parts --report /etc/cr
#

Then I added the following lines:

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
**MAILTO= email address of recipient**

# m h dom mon dow user  command
17 *    * * *   root    run-parts --report /etc/cron.hourly
25 6    * * *   root    test -x /usr/sbin/anacron || run-parts --report /etc/cr
47 6    * * 7   root    test -x /usr/sbin/anacron || run-parts --report /etc/cr
52 6    1 * *   root    test -x /usr/sbin/anacron || run-parts --report /etc/cr
**10 * * * * root rsync -avzu /path to copy from /path to copy to**
#


So I should have it running the rsync command every 10 minutes and emailing the address I've added in the MAILTO section.

It doesn't seem to be working however, any idea where I'm going wrong?

Thanks for your time.

---

### Post by jrib on 2007-09-24
1. make sure there is not really a space in your file at 
```
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/us r/sbin:/usr/bin
```

2. Instead of /etc/crontab, I would recommend using either 'crontab -e' to edit your user's crontab or 'sudo crontab -e' for root's crontab.

3.  You probably need to be careful with having spaces after the equal sign when you define the email too.

4.  If the cron job still fails, install "mutt" and type ```
mutt
``` in a terminal to read your user's local mail.  When cron fails it will send you mail with more info.

[edit] I didn't know about MAILTO before, but from the man page, it seems to want a user, not an email address.

> any output is mailed to the owner of the crontab  (or  to  the user  named  in  the  MAILTO  environment  variable  in the crontab, if such exists)

---

