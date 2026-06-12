---
title: "Exim4 on Edgy, smarthost to ISP errors - 550 relaying mail to xxx is not allowed"
date: 2006-11-12
forum: General Help
---

### Post by Rich99 on 2006-11-12
I've got a fresh install of edgy here, with exim4 setup & confiugured as local mail only, sent via smarthost.  Here's my update-exim4.conf.conf:

dc_eximconfig_configtype='smarthost'
dc_other_hostnames='ubuntu-server'
dc_local_interfaces='127.0.0.1'
dc_readhost=''
dc_relay_domains=''
dc_minimaldns='false'
dc_relay_nets=''
dc_smarthost='smtp.ntlworld.com'
CFILEMODE='644'
dc_use_split_config='false'
dc_hide_mailname='false'
dc_mailname_in_oh='true'

I have a .forward in my home directory set to my work email address.  When local mail is sent (eg from cron jobs), I get the following error in /var/log/exim4/mainlog:

2006-11-12 14:29:21 1GjB2a-0001Fv-Ah ** [email]me@work.ac.uk[/email] <root@ubuntu-server> R=smarthost T=remote_smtp_smarthost: SMTP error from remote mail server after RCPT TO:<me@work.ac.uk>: host smtp.ntlworld.com [81.103.221.11]: 550 relaying mail to work.ac.uk is not allowed

If I send mail to that smtp server from another windows machine on my network it's fine.

Any ideas?

---

### Post by Rich99 on 2006-11-12
I tried changing the settings from 'mail delivered by smtp & sent by smarthost' to 'no local mail, sent by smarthost' such that my conf file looked like this:

dc_eximconfig_configtype='satellite'
dc_other_hostnames=''
dc_local_interfaces='127.0.0.1'
dc_readhost='ubuntu-server'
dc_relay_domains=''
dc_minimaldns='false'
dc_relay_nets=''
dc_smarthost='smtp.ntlworld.com'
CFILEMODE='644'
dc_use_split_config='false'
dc_hide_mailname='true'
dc_mailname_in_oh='true'

If I then unfreeze my queue I get this error message:

 ** rich@ubuntu-server R=hub_user_smarthost T=remote_smtp_smarthost: SMTP error from remote mail server after RCPT TO:<rich@ubuntu-server>: host smtp.ntlworld.com [81.103.221.11]: 553 Invalid address syntax

The other thing I've found is that the start/stop script in /etc/init.d doesn't stop exim.  I have to kill the process manually before I can restart the daemon from the exim4 script.

---

### Post by Rich99 on 2006-11-13
I also tried postix & get the same error (configured as internet email with smarthost).  Error is:

Nov 13 21:20:06 ubuntu-server postfix/smtp[4950]: B6FE16D818B: to=<me@work.ac.uk>, orig_to=<root@ubuntu-server>, relay=smtp.ntlworld.com[81.103.221.11]:25, delay=7.2, delays=0.01/0/7.2/0.03, dsn=5.0.0, status=bounced (host smtp.ntlworld.com[81.103.221.11] said: 550 relaying mail to work.ac.uk is not allowed (in reply to RCPT TO command))

---

### Post by gcc on 2007-12-24
smtp.ntlworld.com does not deliver bounces for me:

[root@mcnally mail]# telnet smtp.ntlworld.com 25
Trying 81.103.221.11...
Connected to smtp.ntlworld.com.
Escape character is '^]'.
220 ESMTP server ready
helo 0
250 aamtaout01-winn.ispmail.ntl.com
mail from: <>
250 Sender <> Ok
rcpt to: [email]spam@qwirx.com[/email]
550 relaying mail to qwirx.com is not allowed
quit
221 aamtaout01-winn.ispmail.ntl.com ESMTP server closing connection

(rejected message with MAIL FROM: <>)

[root@mcnally mail]# telnet smtp.ntlworld.com 25
Trying 81.103.221.11...
Connected to smtp.ntlworld.com.
Escape character is '^]'.
220 ESMTP server ready
helo 0
250 aamtaout02-winn.ispmail.ntl.com
mail from: <spam@qwirx.com>
250 Sender <spam@qwirx.com> Ok
rcpt to: [email]spam@qwirx.com[/email]
250 Recipient <spam@qwirx.com> Ok
quit
221 aamtaout02-winn.ispmail.ntl.com ESMTP server closing connection

(accepted message with MAIL FROM: <valid>)

This error of yours is quite reasonable:

** rich@ubuntu-server R=hub_user_smarthost T=remote_smtp_smarthost: SMTP error from remote mail server after RCPT TO:<rich@ubuntu-server>: host smtp.ntlworld.com [81.103.221.11]: 553 Invalid address syntax

rich@ubuntu-server is not a valid email address, so that's why they don't accept your mail when you claim that it's your address. Set up Exim to claim something more reasonable as a server name.

---

