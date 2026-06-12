---
title: "Changing email configuration for sending"
date: 2023-06-25
forum: General Help
---

### Post by David_Partridge on 2023-06-25
Running Ubuntu Linux 20.04.6.

I recently changed my email provider.

My new email settings require connection via a different smtp server at port 465 and using SSL/TLS and also require authentication with a username and password.

I think that I use sendmail on the (infrequently accessed) Ubuntu system to send e.g. email with cron job statuses.

I cannot for the life of me remember what I needed to do to set this up (if was over two years back IIRC).

Please could a kind soul guide me through the steps to set this up correctly?

/etc/mail/sendmail.mc currently reads:

> dnl # Default Mailer setup
define(`SMART_HOST', `relay.plus.net')dnl
define(`RELAY_MAILER_ARGS', `TCP $h 587')dnl
define(`ESMTP_MAILER_ARGS', `TCP $h 587')dnl
define(`confAUTH_OPTIONS', `A p')dnl
TRUST_AUTH_MECH(`EXTERNAL DIGEST-MD5 CRAM-MD5 LOGIN PLAIN')dnl
define(`confAUTH_MECHANISMS', `EXTERNAL GSSAPI DIGEST-MD5 CRAM-MD5 LOGIN PLAIN')dnl
FEATURE(`authinfo',`hash -o /etc/mail/auth/client-info.db')dnl
MAILER_DEFINITIONS
MAILER(`local')dnl
MAILER(`smtp')dnl



Thanks
David

---

### Post by dragonfly41 on 2023-06-25
I use Thunderbird.

---

### Post by David_Partridge on 2023-06-25
That doesn't help a fat lot for configuring sendmail for cron output

---

### Post by dragonfly41 on 2023-06-25
If you insist ..

Open Phind.com in browser and type in search field ..

configuring sendmail for cron output

or the fat option I suggested .. since I like Thunderbird

configuring sendmail for cron output via Thunderbird

---

### Post by David_Partridge on 2023-06-25
Except that phind.com didn't tell me how to do that ...

---

### Post by dragonfly41 on 2023-06-26
Trying hard to help regardless of your frustration .. and I can learn too .. 

I used your issue as a test case (again) with Phind and chose this query (your output) ..

sendmail[82759]: NOQUEUE: SYSERR(root): /etc/mail/sendmail.cf: line 71: unknown configuration line "465"

I think that Phind should help with cases *provided that the query is carefully selected*. Certainly citations are listed (but not Ubuntu forum it seems). Note the option to use searchengines such as !g

---

