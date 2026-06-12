---
title: "Mutt with Gmail and local mail"
date: 2014-05-18
forum: General Help
---

### Post by Derek Karpinski on 2014-05-18
I've googled for the past few days, and none of it is clear to me.

I have my gmail working well in mutt.  But I run some cron jobs, apt changelogs, and fail2ban services that send emails to root.  I have changed my /etc/aliases file to forward to myself.  I can check these with 'mail'.

I would like to have mutt include my local mail account in /var/mail/.  It's an mbox file.  Can someone help me?  I can post my .muttrc if that will help.

Thanks in advance.

---

### Post by HermanAB on 2014-05-18
It should be as simple as:
$ mutt -f /var/mail/mailboxname

---

