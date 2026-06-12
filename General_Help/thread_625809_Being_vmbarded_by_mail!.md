---
title: "Being vmbarded by mail!"
date: 2007-11-28
forum: General Help
---

### Post by t_ras on 2007-11-28
Hi
It seems I'm being bombarded by delivery failure mails.
It seems some one is sending through my system, though I cant see hoe it si possible without username and password.
I have postfix on kubuntu 7.10
Here are some log entries:
```
11/28/2007 07:16:31 PM	serversrv1	postfix/cleanup[17671]	1D31A8B877: message-id=<20071128171631.1D31A8B877@serversrv1.servers.net>

11/28/2007 07:16:31 PM	serversrv1	postfix/local[17739]	1D31A8B877: to=<admispconfig@localhost.localdomain>, relay=local, delay=0.96, delays=0.9/0/0/0.06, dsn=2.0.0, status=sent (delivered to command: /usr/bin/procmail -f-)

11/28/2007 07:16:31 PM	serversrv1	postfix/pickup[17626]	1D31A8B877: uid=10003 from=<martin>

11/28/2007 07:16:31 PM	serversrv1	postfix/qmgr[17627]	1D31A8B877: from=<martin@servers.net>, size=375, nrcpt=1 (queue active)

11/28/2007 07:16:31 PM	serversrv1	postfix/qmgr[17627]	1D31A8B877: removed

11/28/2007 07:16:44 PM	serversrv1	postfix/cleanup[17667]	B4F8C8B877: message-id=<20071128171644.B4F8C8B877@serversrv1.servers.net>

11/28/2007 07:16:44 PM	serversrv1	postfix/local[17630]	8B9A18B963: to=<martin@servers.net>, orig_to=<Vaidhyaneyfdw@servers.net>, relay=local, delay=188675, delays=188611/49/0/15, dsn=2.0.0, status=sent (delivered to command: /usr/bin/procmail -f-)

11/28/2007 07:16:44 PM	serversrv1	postfix/local[17739]	B4F8C8B877: to=<admispconfig@localhost.localdomain>, relay=local, delay=0.47, delays=0.3/0/0/0.17, dsn=2.0.0, status=sent (delivered to command: /usr/bin/procmail -f-)

11/28/2007 07:16:44 PM	serversrv1	postfix/pickup[17626]	B4F8C8B877: uid=10003 from=<martin>

11/28/2007 07:16:44 PM	serversrv1	postfix/qmgr[17627]	8B9A18B963: removed

11/28/2007 07:16:44 PM	serversrv1	postfix/qmgr[17627]	B4F8C8B877: from=<martin@servers.net>, size=375, nrcpt=1 (queue active)

11/28/2007 07:16:45 PM	serversrv1	postfix/cleanup[17737]	C251A8B863: message-id=<20071128171645.C251A8B863@serversrv1.servers.net>

11/28/2007 07:16:45 PM	serversrv1	postfix/local[17629]	994D38B863: to=<martin@servers.net>, orig_to=<Lyon@servers.net>, relay=local, delay=188552, delays=188487/50/0/15, dsn=2.0.0, status=sent (delivered to command: /usr/bin/procmail -f-)

11/28/2007 07:16:45 PM	serversrv1	postfix/pickup[17626]	C251A8B863: uid=10003 from=<martin>

11/28/2007 07:16:45 PM	serversrv1	postfix/qmgr[17627]	994D38B863: removed

11/28/2007 07:16:46 PM	serversrv1	postfix/qmgr[17627]	C251A8B863: from=<martin@servers.net>, size=375, nrcpt=1 (queue active)

11/28/2007 07:16:47 PM	serversrv1	postfix/local[17739]	C251A8B863: to=<admispconfig@localhost.localdomain>, relay=local, delay=2.3, delays=0.74/0/0/1.6, dsn=2.0.0, status=sent (delivered to command: /usr/bin/procmail -f-)

11/28/2007 07:16:47 PM	serversrv1	postfix/qmgr[17627]	C251A8B863: removed

11/28/2007 07:16:47 PM	serversrv1	postfix/smtpd[17698]	connect from firebrick.mullerholdings.co.uk[81.187.254.66]

11/28/2007 07:16:48 PM	serversrv1	postfix/cleanup[17671]	2F5E98B85F: message-id=<blQmlEbrX00002df2@mail.mullerholdings.co.uk>

11/28/2007 07:16:48 PM	serversrv1	postfix/qmgr[17627]	2F5E98B85F: from=<>, size=2761, nrcpt=1 (queue active)

11/28/2007 07:16:48 PM	serversrv1	postfix/smtpd[17698]	2F5E98B85F: client=firebrick.mullerholdings.co.uk[81.187.254.66]

11/28/2007 07:16:49 PM	serversrv1	postfix/smtpd[17698]	disconnect from firebrick.mullerholdings.co.uk[81.187.254.66]

11/28/2007 07:16:58 PM	serversrv1	postfix/local[17672]	BF9A58B86E: to=<martin@servers.net>, orig_to=<itsPomykalski@servers.net>, relay=local, delay=117, delays=38/64/0/14, dsn=2.0.0, status=sent (delivered to command: /usr/bin/procmail -f-)

11/28/2007 07:16:58 PM	serversrv1	postfix/qmgr[17627]	BF9A58B86E: removed

11/28/2007 07:16:59 PM	serversrv1	postfix/cleanup[17667]	074688B86E: message-id=<20071128171659.074688B86E@serversrv1.servers.net>

11/28/2007 07:16:59 PM	serversrv1	postfix/local[17739]	074688B86E: to=<admispconfig@localhost.localdomain>, relay=local, delay=0.29, delays=0.11/0/0/0.18, dsn=2.0.0, status=sent (delivered to command: /usr/bin/procmail -f-)

11/28/2007 07:16:59 PM	serversrv1	postfix/pickup[17626]	074688B86E: uid=10003 from=<martin>

11/28/2007 07:16:59 PM	serversrv1	postfix/qmgr[17627]	074688B86E: from=<martin@servers.net>, size=375, nrcpt=1 (queue active)

11/28/2007 07:16:59 PM	serversrv1	postfix/qmgr[17627]	074688B86E: removed

11/28/2007 07:17:04 PM	serversrv1	postfix/cleanup[17737]	022D38B86E: message-id=<20071128171704.022D38B86E@serversrv1.servers.net>

11/28/2007 07:17:04 PM	serversrv1	postfix/local[17630]	65C798BA0C: to=<martin@servers.net>, orig_to=<HOEFMAN@servers.net>, relay=local, delay=188608, delays=188525/65/0/17, dsn=2.0.0, status=sent (delivered to command: /usr/bin/procmail -f-)

11/28/2007 07:17:04 PM	serversrv1	postfix/local[17739]	022D38B86E: to=<admispconfig@localhost.localdomain>, relay=local, delay=1.5, delays=1.4/0/0/0.04, dsn=2.0.0, status=sent (delivered to command: /usr/bin/procmail -f-)

11/28/2007 07:17:04 PM	serversrv1	postfix/pickup[17626]	022D38B86E: uid=10003 from=<martin>

11/28/2007 07:17:04 PM	serversrv1	postfix/qmgr[17627]	022D38B86E: from=<martin@servers.net>, size=375, nrcpt=1 (queue active)

11/28/2007 07:17:04 PM	serversrv1	postfix/qmgr[17627]	022D38B86E: removed

11/28/2007 07:17:04 PM	serversrv1	postfix/qmgr[17627]	65C798BA0C: removed

11/28/2007 07:17:13 PM	serversrv1	postfix/cleanup[17671]	6E4D88B86E: message-id=<20071128171713.6E4D88B86E@serversrv1.servers.net>

11/28/2007 07:17:13 PM	serversrv1	postfix/local[17629]	775F88B888: to=<martin@servers.net>, orig_to=<Lisloisajjmk@servers.net>, relay=local, delay=270, delays=177/79/0/14, dsn=2.0.0, status=sent (delivered to command: /usr/bin/procmail -f-)

11/28/2007 07:17:13 PM	serversrv1	postfix/local[17739]	6E4D88B86E: to=<admispconfig@localhost.localdomain>, relay=local, delay=0.14, delays=0.11/0/0/0.03, dsn=2.0.0, status=sent (delivered to command: /usr/bin/procmail -f-)

11/28/2007 07:17:13 PM	serversrv1	postfix/pickup[17626]	6E4D88B86E: uid=10003 from=<martin>

11/28/2007 07:17:13 PM	serversrv1	postfix/qmgr[17627]	6E4D88B86E: from=<martin@servers.net>, size=375, nrcpt=1 (queue active)

11/28/2007 07:17:13 PM	serversrv1	postfix/qmgr[17627]	6E4D88B86E: removed

11/28/2007 07:17:13 PM	serversrv1	postfix/qmgr[17627]	775F88B888: removed

11/28/2007 07:17:16 PM	serversrv1	postfix/local[17672]	253378B84D: to=<martin@servers.net>, orig_to=<dsfa_evenson@servers.net>, relay=local, delay=188380, delays=188283/82/0/14, dsn=2.0.0, status=sent (delivered to command: /usr/bin/procmail -f-)

11/28/2007 07:17:16 PM	serversrv1	postfix/qmgr[17627]	253378B84D: removed

11/28/2007 07:17:17 PM	serversrv1	postfix/cleanup[17667]	5F0D48B863: message-id=<20071128171717.5F0D48B863@serversrv1.servers.net>

11/28/2007 07:17:17 PM	serversrv1	postfix/local[17739]	5F0D48B863: to=<admispconfig@localhost.localdomain>, relay=local, delay=0.65, delays=0.58/0/0/0.07, dsn=2.0.0, status=sent (delivered to command: /usr/bin/procmail -f-)

11/28/2007 07:17:17 PM	serversrv1	postfix/pickup[17626]	5F0D48B863: uid=10003 from=<martin>

11/28/2007 07:17:17 PM	serversrv1	postfix/qmgr[17627]	5F0D48B863: from=<martin@servers.net>, size=375, nrcpt=1 (queue active)

11/28/2007 07:17:17 PM	serversrv1	postfix/qmgr[17627]	5F0D48B863: removed


```
/etc/postfix/main.cf:
```
# See /usr/share/postfix/main.cf.dist for a commented, more complete version


# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
#myorigin = /etc/mailname

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

# TLS parameters
smtpd_tls_cert_file = /etc/postfix/ssl/smtpd.crt
smtpd_tls_key_file = /etc/postfix/ssl/smtpd.key
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = serversrv1.servers.net
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
#mydestination = servers.net, serversrv1, localhost.localdomain, localhost,mail.ter$
relayhost = localhost
mynetworks = 127.0.0.0/8
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all
smtpd_sasl_local_domain =
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_una$
smtpd_tls_auth_only = no
smtp_use_tls = yes
smtp_tls_note_starttls_offer = yes
smtpd_tls_CAfile = /etc/postfix/ssl/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom

virtual_maps = hash:/etc/postfix/virtusertable

mydestination = /etc/postfix/local-host-names

```
/etc/postfix/virtusertable:
```
###################################
#
# ISPConfig virtusertable Configuration File
#         Version 1.0
#
###################################
martin@mail.servers.net    martin
@mail.servers.net    martin
martin@servers.net    martin
@servers.net    martin
yulia@mail.servers.net    yulia
yulia@servers.net    yulia
dbadmin@mysql.servers.net    dbadmin
webmaster@www.servers.net    webmaster
plugagimel@plugagimel.servers.net    plugagimel
moderator@forum.servers.net    moderator
pics@pics.servers.net    pics
shai@shai.servers.net    shai
blogmaster@blogs.servers.net    blogmaster
csight@creativesight.servers.net    csight
spma@softdev.servers.net    spma
bc_user@imtbo2008.servers.net    bc_user
#### MAKE MANUAL ENTRIES BELOW THIS LINE! ####

```

And the "undelivered"  mails seem to be sent by non existing users....

Any Idea what can I do to solve this problem. right now my SMTP is down, but else way it all goes to my junk (thank to spamassasin).

---

### Post by t_ras on 2007-11-28
bump!

---

### Post by Mr. C. on 2007-11-29
Stop accepting email for unknown recipients.

You have the wildcard:

@servers.net    martin

in your virtual user table.  This disables recipient validation, so your server is subject to dictionary attacks, and it accepts bounced messages from server's that were sent bogus email claiming to be from your domain (backscatter).

If you need a form of wildcarding, learn about recipient_delimiter in postconf (5).

MrC

---

