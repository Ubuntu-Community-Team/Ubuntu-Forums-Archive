---
title: "Setting default email address for at command"
date: 2015-07-23
forum: General Help
---

### Post by SageOfSmeg on 2015-07-23
Can anybody help please?
I am trying to set the default email recipient for when using the "at" command, which I use from time to time.

When using:
```
at -m -f/home/gjd/jobs/housekeeping.sh now + 1 min
warning: commands will be executed using /bin/sh

```
(I notice that is mentions /bin/sh rather than /bin/bash)

I get the following notice on my gmail account:
> Delivery to the following recipient failed permanently:

     [EMAIL="gjd@gmail.com"]gjd@gmail.com[/EMAIL]

Technical details of permanent failure:
Google tried to deliver your message, but it was rejected by the server for the recipient domain gmail.com by gmail-smtp-in.l.google.com. [2a00:1450:400c:c0b::1b].

The error that the other server returned was:
550-5.1.1 The email account that you tried to reach does not exist. Please try
550-5.1.1 double-checking the recipient's email address for typos or
550-5.1.1 unnecessary spaces. <etc.>


My username is "gjd", obviously. It is the only user on that machine.

I want to send mail, via gmail, to email address: [EMAIL="gjdlinux@gmail.com"]gjdlinux@gmail.com[/EMAIL] (not my real address but used for illustration).

I have tried the following:
```
export LOGNAME=gjdlinux

sudo nano /etc/aliases
root:gjdlinux@gmail.com        (followed by a newline)

sudo nano /etc/mail/aliases
root:gjdlinux@gmail.com        (followed by a newline)

sudo nano /root/.forward
gjdlinux@gmail.com        (followed by a newline)
```

I have rebooted but still no success.

I have sSMTP installed but not postfix. Both /etc/ssmtp/ssmtp.conf and /etc/ssmtp/revaliases are set up.
When using 'cron' I receive email correctly, but not when using 'at'.

---
lubuntu 12.04.5 LTS precise

---

### Post by TheFu on 2015-07-23
The fact that cron works, but at doesn't is troubling. I don't see that issue here.

**at** sends the email to the userid on the system.  That means if you want it to go somewhere else, you need to setup an MTA and an alias for delivery.  I've never used any mailer other than a real MTA - postfix, sendmail, so cannot help with any others.  All my non-email servers are configured as "satellite systems" on the network - all email is forwarded to the main email server.  No inbound email is accepted on any satellite system, just local-to-the-box originated emails, if that makes sense.

I suspect some special config is needed for a non-mailserver to send email to gmail.com. Some sort of authentication, a static IP, and an ISP who doesn't trap output SMTP traffic, at a minimum. gmail is picky about who it accepts email.  Does sSMTP rewrite the FROM address to be valid?

Inside the /etc/aliases file, I forward all emails to root, postmaster, webmaster, my-local-userid and a few others to my real email server [email]id@domain.com[/email].  After editing the aliases files, be certain to rehash it - **sudo newaliases**.  I find it handy to do this stuff through an ansible playbook to keep consistency across all the servers.  **man 5 aliases** explains the file format. It is simple.

Looking at your /etc/aliases ... perhaps adding a space or a tab after the ':' would help?  I dunno, just never seen them without one.

Just tested it here - and it worked for **at**, as expected.

---

### Post by SageOfSmeg on 2015-07-24
After editing /etc/aliases I tried:
```
sudo newaliases
newaliases: Aliases are not used in sSMTP
```


I noticed something this morning:
```
tail /var/log/syslog
Jul 24 08:16:06 gjdpc1 sSMTP[8399]: Creating SSL connection to host
Jul 24 08:16:07 gjdpc1 sSMTP[8399]: SSL connection using RSA_ARCFOUR_SHA1
Jul 24 08:16:10 gjdpc1 sSMTP[8399]: Sent mail for root@gmail.com (221 2.0.0 closing connection v9sm11076670wjq.41 - gsmtp) uid=1000 username=gjd outbytes=1030
...
Jul 24 08:58:01 gjdpc1 sSMTP[9189]: Creating SSL connection to host
Jul 24 08:58:01 gjdpc1 sSMTP[9189]: SSL connection using RSA_ARCFOUR_SHA1
Jul 24 08:58:03 gjdpc1 sSMTP[9189]: Sent mail for gjd@gmail.com (221 2.0.0 closing connection gc4sm2136902wib.23 - gsmtp) uid=1000 username=gjd outbytes=384
```

The first sSMTP group was issued by cron, the latter group was issued by "at". 
It is interesting that the cron group shows "sent mail for **root**@gmail.com" and it was delivered to the correct email address specifed in crontab using the MAILTO: variable, whereas the "at" group shows "sent mail for **gjd**@gmail.com" and still fails to deliver to the desired email address.
It may be irrelevant but I thought it stood out.

---

