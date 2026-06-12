---
title: "Cron/Sendmail Defunct Processes"
date: 2007-12-04
forum: General Help
---

### Post by Schiz0 on 2007-12-04
Hey everyone,

I'm running Ubuntu 7.10 Server Edition. I have a cron script ( [http://pastebin.ca/803903](http://pastebin.ca/803903) ). I edited crontab using "crontab -e" (Running as the ircd user) and added the line ( [http://pastebin.ca/805617](http://pastebin.ca/805617) ). I have exim4 installed and running (I have send emails successfully from command line and also php scripts). It was installed and configured via apt-get and dpkg.

My problem is as follows: When the anope services daemon is not running, the cron script starts it, and outputs some text (Which I want to to be emailed to me). But instead of emailing the output to me, cron opens up defunct zombie processes for sh and sendmail and I must kill the cron process to get rid of other processes.

The output of "ps -ef" showing the defunct processes is at [http://pastebin.ca/803916](http://pastebin.ca/803916)
The sendmail process stays there until I kill the "/USR/SBIN/CRON" process.

I tested this by manually stopping the anope services, then waiting 10 minutes for the cron script to run. The cron script runs, and the services start back up, but I never get the email from the output of the cron script. The sendmail process that started from cron freezes up somehow for some reason and becomes a defunct zombie process.

Basically all I want is to be notified with the output of cron. I don't know if this is a cron problem or a exim4 problem.

I tested this with both the sendmail MTA and the exim4 MTA. They both did the same exact, which makes me suspect more so that it is some sort of cron setting that I have misconfigured.

Thank you for everyone's time and responses.
~Schiz0

PS. I also posted this to the ubuntu-users mailing list.

---

