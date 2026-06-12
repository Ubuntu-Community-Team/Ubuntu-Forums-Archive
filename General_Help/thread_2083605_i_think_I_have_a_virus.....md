---
title: "i think I have a virus...."
date: 2012-11-13
forum: General Help
---

### Post by pabc on 2012-11-13
I've noticed a lot of disk thrashing recently that I never had so a check of the forums suggested iotop would identify the the culprit - 

it did. 

Sendmail if running 2-3 times a second;

sendmail: MTA: ./q############ from queue

I'm assuming my box is compromised and I'm spewing spam.

rkhunter / chkhunter suggest nothing obvious. 

How can I confirm what infection I have?

Phil

---

### Post by quentinl on 2012-11-13
i used ClamTK and that just checks that would be a place to start

---

### Post by westie457 on 2012-11-13
Change the Email password, and log out of the email account. See if that stops it.

---

### Post by pabc on 2012-11-13
hmm,

looking at the files in the /var/spool/mqueue they are all local - not spam.

'MOperating system error' - being spewed out about 30 a minute.

time for more investigating

---

### Post by pabc on 2012-11-14
Solved.

a regular cron job was creating significant errors and emailing them. Output is now suppressed and the problem has gone away

---

