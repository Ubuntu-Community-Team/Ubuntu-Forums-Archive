---
title: "sendmail permissions problems"
date: 2006-07-10
forum: General Help
---

### Post by maino82 on 2006-07-10
I am receiving the following error in /var/log/mail.log that seems to point to a permissions problem with the www-data user (apache) not being able to send mail or create the needed directories. The problem is that I have been unable to find any information about which files/directories need to have their permissions changed, or if it's a problem inherent in the www-data user that needs to be corrected. I checked to make sure that the /var/spool/mail directory exists and is writable by the www-data user, but that has not done anything either. Any help you could offer would be greatly appreciated!

> Jul 7 12:34:07 localhost sendmail[16364]: k67GY74N016364: from=www-data, size=87, class=0, nrcpts=1, msgid=<200607071634.k67GY74N016364@localhost.local domain>, relay=www-data@localhost
Jul 7 12:34:07 localhost sm-mta[16365]: k67GY7lH016365: SYSERR(root): collect: Cannot write ./dfk67GY7lH016365 (bfcommit, uid=0, gid=122): No such file or directory
Jul 7 12:34:07 localhost sm-mta[16365]: k67GY7lH016365: from=<www-data@localhost.localdomain>, size=324, class=0, nrcpts=1, proto=ESMTP, daemon=MSP-v4, relay=localhost.localdomain [127.0.0.1]
Jul 7 12:34:07 localhost sendmail[16364]: k67GY74N016364: to=ADDRESS@gmail.com, ctladdr=www-data (33/33), delay=00:00:00, xdelay=00:00:00, mailer=relay, pri=30087, relay=[127.0.0.1] [127.0.0.1], dsn=4.0.0, stat=Deferred: 421 4.3.0 collect: Cannot write ./dfk67GY7lH016365 (bfcommit, uid=0, gid=122): No such file or directory

---

### Post by dcherryholmes on 2006-08-29
I am also having the same problem, and tearing my hair out from it.  I'd like to get rid of my last Suse box and go all-Ubuntu, but I can't get the mail server up.

---

### Post by dcherryholmes on 2006-08-29
Oops, jumped the gun.  My error message is similiar, but not quite the same:

 sm-mta[6457]: k7TBVOVh006457: SYSERR(root): collect: Cannot write ./dfk7TBVOVh006457 (sm_io_flush||sm_io_error, uid=0, gid=116): Input/output error

I've read some things that suggest this might be due to a misconfiguration of submit.cf, possibly to do with trustedusers.

---

