---
title: "Unwanted email from anacron"
date: 2015-07-05
forum: General Help
---

### Post by Keith_Helms on 2015-07-05
I created an ssmtp.conf file on a desktop system in order to allow a script I wrote to explicitly send an email to me with the ssmtp command.  That works fine.  However, the system is now also trying to send an email with results from cron.daily because a command named logrotate is getting an error trying to rotate a non-existant logfile.  The email fails, but my mail provider is getting an error message from the send attempt and it is annoying them.

I see the following in syslog:

```
Jul  5 07:36:31 linux-quadcore anacron[3890]: Job `cron.daily' terminated (exit status: 1) (mailing output)
Jul  5 07:36:31 linux-quadcore sSMTP[4124]: Creating SSL connection to host
Jul  5 07:36:32 linux-quadcore sSMTP[4124]: SSL connection using DHE_RSA_AES_256_CBC_SHA1
Jul  5 07:36:32 linux-quadcore sSMTP[4124]: RCPT TO:<""@linux-quadcore> (504 5.5.2 <root@linux-quadcore>: Sender address rejected: need fully-qualified address)
Jul  5 07:36:32 linux-quadcore anacron[3890]: Tried to mail output of job `cron.daily', but mailer process (/usr/sbin/sendmail) exited with ststus 1
Jul  5 07:36:32 linux-quadcore anacron[3890]: Normal exit (1 job run)

```

I have tried to make it stop attempting to send me mail by adding an empty MAILTO to both anacrontab and crontab.

/etc/anacrontab
```
#/etc/anacrontab: configuration file for anacron

# See anacron(8) and anacrontab(5) for details.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
HOME=/root
LOGNAME=root
MAILTO=""

# These replace cron's entries
1    5    cron.daily    run-parts --report /etc/cron.daily
7    10    cron.weekly    run-parts --report /etc/cron.weekly
@monthly    15    cron.monthly    run-parts --report /etc/cron.monthly
```

/etc/crontab
```
# /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file
# and files in /etc/cron.d. These files also have username fields,
# that none of the other crontabs do.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
MAILTO=""

# m h dom mon dow user    command
17 *    * * *    root    cd / && run-parts --report /etc/cron.hourly
25 6    * * *    root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47 6    * * 7    root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 6    1 * *    root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )
#

```

What else do I need to do to get cron/anacron to quit trying to send email to me?

---

### Post by ian-weisser on 2015-07-06
Well one alternative is to use your correct e-mail address so cron can properly send you error messages, and to simply disable that logrotate job.

---

### Post by Keith_Helms on 2015-07-06
Can you elaborate?  I see dozens of postings on many websites that all claim the way to disable email is to set MAILTO to an empty string.  Are those all incorrect?

---

### Post by nerdtron on 2015-07-06
Have you tried, nulling the output of the crontab scripts? [http://www.cyberciti.biz/faq/disable-the-mail-alert-by-crontab-command/](http://www.cyberciti.biz/faq/disable-the-mail-alert-by-crontab-command/)

---

### Post by Keith_Helms on 2015-07-06
I saw that I could get rid of this specific email attempt by eliminating its output.  I kind of wanted to get rid of any future email attempts too.  I may set the job to output to /dev/null if I can't figure out how to make anacron stop trying to send mail.

---

### Post by Keith_Helms on 2015-07-06
I may have figured out a way to get rid of email.  The ssmtp command has a -C option that allows you to supply an alternate config file.  I copied my /etc/ssmtp/ssmtp.conf file to my home directory, replaced the modified /etc/ssmtp./ssmtp.conf file with the original one, then modified my script to use the -C option and pull in the version from my home directory.  When I ran the script manually it sent the email correctly.  I think this solution will stop generating error messages for my mail provider.

I still find it annoying that you can't seem to configure anacron to not try and send email.

---

### Post by ian-weisser on 2015-07-06
Redirecting output to /dev/null can be done on a per-job basis. You already know that, of course.
I think it would be unnecessarily confusing to have layers of possible overrides and redirects in cron and anacron.
I think it's understandable that the cron and anacron authors decided to keep things simple and avoid the issue.

---

