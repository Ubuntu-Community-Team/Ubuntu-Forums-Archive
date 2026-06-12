---
title: "Sending mails with cron/nbsmtp"
date: 2008-03-21
forum: General Help
---

### Post by blissful on 2008-03-21
Hi,

I have nbsmtp as my MTA and I am pretty happy with it. I want to send mails from my overnight cron jobs and I can not find a way to make nbsmtp send mails from the command line (to be used in the crons). Any ideas?

Bliss

---

### Post by blissful on 2008-03-22
Hullo, anyone? Is there no solution?

---

### Post by dcstar on 2008-03-22
> **blissful said:**
> Hi,

I have nbsmtp as my MTA and I am pretty happy with it. I want to send mails from my overnight cron jobs and I can not find a way to make nbsmtp send mails from the command line (to be used in the crons). Any ideas?

Bliss

**mailx**

---

### Post by MONODA on 2008-03-22
i have never tried it, but maybe you can use mutt. it is a CLI mail client, maybe there are commands for sending emails like mutt-email.

---

### Post by blissful on 2008-03-23
Thank you guys. I have installed mailx, but can not get it working with nbsmtp. Whenever I try to send a mail -

[FONT="Courier New"]sphinx:~$ mailx -s "Test" [email]myaddress@gmail.com[/email]
Test
EOT
send-mail: invalid option -- i
Usage: send-mail -f [email]from@address.com[/email] -h relayhost [OPTIONS] (use -H for help)
Can't send mail: sendmail process failed with error code 1

sphinx:~$ ls -l `which sendmail`
lrwxrwxrwx 1 root root 13 2008-03-03 11:32 /usr/sbin/sendmail -> /usr/local/bin/nbsmtp
sphinx:~$[/FONT]

nbsmtp configuration is fine as I can send mails through my other applications. Just not through mailx. Oh BTW, my /etc/mail.rc looks like this

[FONT="Courier New"]sphinx:~$ cat /etc/mail.rc
set sendmail=/usr/local/bin/nbsmtp
set ask append dot save crt
ignore Received Message-Id Resent-Message-Id Status Mail-From Return-Path Via Delivered-To[/FONT]

It appears that mailx tries to insert option [FONT="Courier New"]-i[/FONT] while invoking nbsmtp which does not support this option. Any clues as to what is missing?

---

### Post by dcstar on 2008-03-23
> **blissful said:**
> Thank you guys. I have installed mailx, but can not get it working with nbsmtp. Whenever I try to send a mail -

[FONT="Courier New"]sphinx:~$** mailx** -s "Test" [email]myaddress@gmail.com[/email]
Test
EOT
send-mail: invalid option -- i
Usage: send-mail -f [email]from@address.com[/email] -h relayhost [OPTIONS] (use -H for help)
Can't send mail: sendmail process failed with error code 1

sphinx:~$ ls -l `which sendmail`
lrwxrwxrwx 1 root root 13 2008-03-03 11:32 /usr/sbin/sendmail -> /usr/local/bin/nbsmtp
sphinx:~$[/FONT]

nbsmtp configuration is fine as I can send mails through my other applications. Just not through mailx. Oh BTW, my /etc/mail.rc looks like this

[FONT="Courier New"]sphinx:~$ cat /etc/mail.rc
set sendmail=/usr/local/bin/nbsmtp
set ask append dot save crt
ignore Received Message-Id Resent-Message-Id Status Mail-From Return-Path Via Delivered-To[/FONT]

It appears that mailx tries to insert option [FONT="Courier New"]-i[/FONT] while invoking nbsmtp which does not support this option. Any clues as to what is missing?

Try using **mail**, not mailx.

---

### Post by blissful on 2008-03-23
Mail was not installed on my machine by default. So I just soft linked it to mailx. I have tight memory constraints and need to operate on as thin a configuration as I possibly can.

---

