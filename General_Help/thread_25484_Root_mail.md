---
title: "Root mail"
date: 2005-04-10
forum: General Help
---

### Post by plewisfdx on 2005-04-10
After bugfix d/l, I now get root mail in my sylpheed inbox.  Only Cron and anacron mail.  How can I stop this?  I didn't get it before I apt-get upgraded...

---

### Post by soul_rebel on 2005-04-10
Those mails must be read by someone and must "land" into some mailbox. Usually "system" mail is sent to root, and mail for root is sent to a user. See /etc/aliases to configure this. You can let root receive mails and read them with sudo.

---

### Post by plewisfdx on 2005-04-10
Thanks for the reply.  So I guess its a Sylpheed question then.  I have tried to set a rule, 2 in fact, to both delete and not download these messages, but it doesn't stop.  Every 15 mins I get another email.

I didn't have this email sent before I did the upgrade.  How can I NOT get these in Sylpheed, and still read my spool?  (Yosucker sends them here.)

---

### Post by soul_rebel on 2005-04-11
/etc/aliases not sylpheed

can you post a couple of those mails?

---

### Post by plewisfdx on 2005-04-11
Here is the email I get every 15 mins:


"From: root@laptop (Cron Daemon)
To: root@laptop
Subject: Cron <root@laptop> /home/lewis/phil/ym
Date: Mon, 11 Apr 2005 07:15:12 -0500 (CDT)

Using phil.conf
Login... OK.
INBOX
-> Reading list of messages...
-> Matching repository...
-> No new messages.
Emptying bulk folder... OK.
Logout OK.

Using phil2.conf
Login... OK.
INBOX
-> Reading list of messages...
-> Matching repository...
-> No new messages.
Emptying bulk folder... OK.
Logout OK.

Done."

I looked at /etc/aliases, and I saw my username as the initial user.

thanks,

phil

---

### Post by soul_rebel on 2005-04-11
you shouldn't be receiving a mail every 15 minutes. Did you add any cron job? cron executes commands and mail someone (root) with the ouput. So cron job are expected to have no output in 99% of the cases. Look at  /etc/crontab and /etc/cron.d/ to see if you find the script responsible for all those mail. maybe is this one: /home/lewis/phil/ym

---

### Post by plewisfdx on 2005-04-11
Yes, I added a cron job every 15 mins to execute that script.  I added it before the upgrade, and I only started getting the email AFTER the upgrade.  I don't care if root gets the mail, I just don't want them to show up in my Sylpheed inbox.

I don't want the CRON email.

---

### Post by soul_rebel on 2005-04-12
So just edit /etc/aliases and leave root mail to root.

But it would be better to use a couple of ">/dev/null" to make that script shut up, or within one month you'll have a lot of mails

---

