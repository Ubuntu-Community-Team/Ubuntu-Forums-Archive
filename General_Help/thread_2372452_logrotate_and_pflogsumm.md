---
title: "logrotate and pflogsumm"
date: 2017-09-25
forum: General Help
---

### Post by cliffmitchell on 2017-09-25
Hi, 
We are using Ubuntu 16.04, ISPConfig 3.1.6, with pflogsumm to report  on our email logs. Something has changed over recent weeks and I don't  know if it's ISPConfig or Ubuntu, but once a week on Saturday night,  when I assume logrotate rotates the mail logs, pflgosumm stops reporting  any data. If I run 'sudo service rsyslog restart' it clears the  problem. I think the log file /var/log/mail.log rotates to  /var/log/mail.log.1 and this becomes the current log file. What should  happen, I think, is that /var/log/mail.log gets copied to  /var/log/mail.log.1 and a new /var/log/mail.log is created as the new  current log file. I can't figure out where this is going wrong - it used  to work just fine. Has something changed in the way logrotate works?  Any suggestions would be hugely appreciated as I'm really  struggling to sort this out.
Many thanks,
Cliff

---

### Post by untrustytahr on 2017-09-25
So it looks like logrotate was patched about a month ago.


LP: #1709670 [https://bugs.launchpad.net/ubuntu/+source/logrotate/+bug/1709670](https://bugs.launchpad.net/ubuntu/+source/logrotate/+bug/1709670)


Is that when your problem started?


Perhaps you can put a postrotate/endscript directive in to make it work until you get it sorted out.


Sorry I cannot offer more.  I do not run a mail server/pflogsumm.

---

### Post by SeijiSensei on 2017-09-25
Take a look at the various files for cron, especially /etc/cron.weekly.  See what time logrotate runs and what time the log summarizer runs.  Set the time for the summarizer to complete before logrotate.

You might need to fiddle with the times in /etc/crontab.  Here is the section that runs the various scripts in /etc/cron.daily, etc.

```

# m h dom mon dow user  command
17 *    * * *   root    cd / && run-parts --report /etc/cron.hourly
25 6    * * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47 6    * * 7   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 6    1 * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )

```

Right now these scripts start running at 6:25 am (for those in cron.daily).  You might want to change the order of these, or create a custom entry either for logrotate or the summarizer.

---

### Post by cliffmitchell on 2017-09-25
Thanks [**[COLOR=#000000]untrustytahr[/COLOR]**]("https://ubuntuforums.org/member.php?u=1895014"). Yes, a month ago sounds about right. If it's a known problem I can live with it until it's fixed. Many thanks for the quick response. Thanks also [**[COLOR=#000000]SeijiSensei[/COLOR]**]("https://ubuntuforums.org/member.php?u=698195") for the information. I'll have a play and see if I can find a workable combination.

---

