---
title: "postfix with zoho smtp For Magento 2"
date: 2016-08-01
forum: General Help
---

### Post by shoutcast on 2016-08-01
Hello, I need help setting up my postfix to use zoho smtp so that my magento 2 can send emails with my zoho accounts.

My Server
Ubuntu 16.04
Managed by serverpilot

Serverpilot preinstalls postfix and i think that they have a special config.  Anyway below is my main.cf..  What i am trying to do is simply setup a zoho smtp and have magento 2 use postfix to send out emails to my zoho account. As well as using aliases.  Any help would be really great been at this for a few days now.

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


readme_directory = no


# TLS parameters
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache


# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.


smtpd_relay_restrictions = permit_mynetworks permit_sasl_authenticated defer_unauth_destination
myhostname = NATURE-DEVELOPMENT
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
mydestination = localhost
relayhost = 
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = loopback-only
inet_protocols = all
local_transport = error:local delivery is disabled
smtp_helo_name = $myhostname.example.com

```

---

