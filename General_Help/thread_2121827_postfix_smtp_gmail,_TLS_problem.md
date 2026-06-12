---
title: "postfix smtp gmail, TLS problem"
date: 2013-03-03
forum: General Help
---

### Post by Frozen Forest on 2013-03-03
I have tried to get postfix to send mails using gmail, but can't get it to work mail log mention STARTTLS
```

:~$ cat /var/log/mail.log
postfix/pickup[1849]: 3DA79101193: uid=0 from=<root>
postfix/cleanup[2374]: 3DA79101193: message-id=<20130303111447.3DA79101193@server>
postfix/qmgr[1850]: 3DA79101193: from=<root@user_name@gmail.com>, size=277, nrcpt=1 (queue active)
postfix/error[2376]: 3DA79101193: to=<user_name@gmail.com???>, relay=none, delay=0.28, delays=0.18/0.01/0/0.09, dsn=5.1.3, status=bounced (bad address syntax)
postfix/cleanup[2374]: 6E72A101196: message-id=<20130303111447.6E72A101196@server>
postfix/qmgr[1850]: 6E72A101196: from=<>, size=2048, nrcpt=1 (queue active)
postfix/bounce[2377]: 3DA79101193: sender non-delivery notification: 6E72A101196
postfix/qmgr[1850]: 3DA79101193: removed
postfix/smtp[2379]: cannot load Certificate Authority data: disabling TLS support
postfix/smtp[2379]: 6E72A101196: to=<root@user_name@gmail.com>, relay=smtp.gmail.com[74.125.143.109]:587, delay=0.43, delays=0.09/0.04/0.27/0.03, dsn=5.7.0, status=bounced (host smtp.gmail.com[74.125.143.109] said: 530 5.7.0 Must issue a STARTTLS command first. xw14sm9874925lab.6 - gsmtp (in reply to MAIL FROM command))
postfix/qmgr[1850]: 6E72A101196: removed

```

```

:~$ cat /etc/postfix/main.cf
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
smtpd_tls_auth_only = no
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache

# SMTP
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtp_tls_CAfile = /etc/ssl/certs
smtp_use_tls=yes

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = server
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = user_name@gmail.com, server, localhost.localdomain, localhost
relayhost = [smtp.gmail.com]:587
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all

# SASL
smtp_sasl_auth_enable = yes
smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd
smtp_sasl_security_options = 


```

```

:~$ echo "This is Content" | sudo sendmail user_name@gmail.com&#8203;

```

---

