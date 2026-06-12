---
title: "POSTFIX on LAMP server sending tons of SPAM"
date: 2013-09-20
forum: General Help
---

### Post by Chris_Chaney on 2013-09-20
Hello,

we have a small Linux box that hosts a few websites. We are using a relay to send the mail through. Our relay queue got super high and all messages are submitted from our LAMP server. I have gone through the mail logs and I see they are coming from ourselves which would be the www-data account. how can I tell what is causing this. I have checked the cron jobs and do not see anything scheduled besides our backups. any help would be greatly appreciated as this is the third time in 2 months this has happened. It ranges from 6-10k emails that try and get blasted. Luckily our filter rate limits these. But I would like to get to the bottom of this. 

Here is the main.cf
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
readme_directory = no
# TLS parameters
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject _unauth_destination, reject_unauth_pipelining, re$
# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.
myhostname = LAMP-PROD.domain.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = Aries.domain.com, LAMP-PROD.domain.com, localhost.domain.com, localhost
relayhost = filter1.domain.com
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128 x.x.x.x, x.x.x.x, 10.0.0.0/16, reject
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all
smtp_generic_maps = hash:/etc/postfix/generic


Here is a grep of the log. 
Sep 20 18:14:07 LAMP-PROD postfix/cleanup[18994]: 504A81C30C4: message-id=<[EMAIL="20130920231407.504A81C30C4@LAMP-PROD.domain.com"]20130920231407.504A81C30C4@LAMP-PROD.domain.com[/EMAIL]>
Sep 20 18:14:07 LAMP-PROD postfix/qmgr[18904]: 504A81C30C4: from=<[EMAIL="support@domain.net"]support@domain.net[/EMAIL]>, size=650, nrcpt=1 (queue active)
Sep 20 18:18:34 LAMP-PROD postfix/error[19569]: 504A81C30C4: to=<[EMAIL="guydunlap26@yahoo.co.uk"]guydunlap26@yahoo.co.uk[/EMAIL]>, relay=none, delay=21142, delays=21142/0.02/0/0.01, dsn=4.4.2, status=deferred (delivery temporarily suspended: lost connection with filter1.domain.com[x.x.x.x] while sending DATA command)
Sep 20 18:19:15 LAMP-PROD postfix/error[19725]: 504A81C30C4: to=<[EMAIL="guydunlap26@yahoo.co.uk"]guydunlap26@yahoo.co.uk[/EMAIL]>, relay=none, delay=21183, delays=21183/0/0/0, dsn=4.4.2, status=deferred (delivery temporarily suspended: lost connection with filter1.domain.com[x.x.x.x] while sending DATA command)
 
Any help on how to debug further to find the root cause would be greatly appreciated. I looked through our firewall and say tons of ip addresses hitting the server's port 80 so I cannot go through them all and try and block.

Thanks,
Chris

---

### Post by dcstar on 2013-09-20
If you have someone/something hacking your web sites then it is nothing to to with your mail server, look in your web server logs to find out what is going on.

---

