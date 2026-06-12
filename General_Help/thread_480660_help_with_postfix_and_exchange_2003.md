---
title: "help with postfix and exchange 2003"
date: 2007-06-21
forum: General Help
---

### Post by dpcamp on 2007-06-21
I'm trying to set up smtp on my ubuntu box to send our emails to users on the LAN. I followed this instructions on this topic [http://ubuntuforums.org/showthread.php?t=316711&highlight=sendmail+exchange]("http://ubuntuforums.org/showthread.php?t=316711&highlight=sendmail+exchange")
and am still recieving the following error : 
> Jun 21 13:38:17 websrvr postfix/local[10427]: 8DBEA1E843F: to=<derek@royalcabinets.com>, relay=local, delay=0.07, delays=0.04/0.02/0/0.02, dsn=5.1.1, status=bounced (unknown user: "derek")
Jun 21 13:38:17 websrvr postfix/cleanup[10425]: 9B6AD1E8441: message-id=<20070621203817.9B6AD1E8441@royalcabinets.com>
Jun 21 13:38:17 websrvr postfix/bounce[10428]: 8DBEA1E843F: sender non-delivery notification: 9B6AD1E8441
Jun 21 13:38:17 websrvr postfix/qmgr[10417]: 9B6AD1E8441: from=<>, size=2100, nrcpt=1 (queue active)
Jun 21 13:38:17 websrvr postfix/qmgr[10417]: 8DBEA1E843F: removed
Jun 21 13:38:17 websrvr postfix/local[10427]: 9B6AD1E8441: to=<www-data@royalcabinets.com>, relay=local, delay=0.03, delays=0.02/0/0/0.01, dsn=2.0.0, status=sent (delivered to mailbox)
Jun 21 13:38:17 websrvr postfix/qmgr[10417]: 9B6AD1E8441: removed

my files are as follows:
main.cf:
```
# See /usr/share/postfix/main.cf.dist for a commented, more complete version


# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname., localhost.local
#myorigin = /etc/mailname

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

# TLS parameters
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache
smtp_sasl_auth_enable = yes
smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = royalcabinets.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
mydestination = smtp.royalcabinets.com, local.royalcabinets.com, royalcabinets.com
relayhost = [smtp.royalcabinets.com]
mynetworks = 127.0.0.0/8 10.0.0.0/255
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
```

here is my sasl_passwd:
```
smtp.royalcabinets.com *myusername*:*mypasswd*
```

any help would be appreciated.

---

### Post by dpcamp on 2007-06-21
also our LAN domain and internet domain are both the same.. i don't know if thats screwing things up.

---

### Post by dpcamp on 2007-06-25
anyone?? i'm kind of in a bind right now.

---

### Post by dpcamp on 2007-06-25
Ok, I got it working. The A records on my domain didn't have the exchange IP address pointed to the domain name.

---

