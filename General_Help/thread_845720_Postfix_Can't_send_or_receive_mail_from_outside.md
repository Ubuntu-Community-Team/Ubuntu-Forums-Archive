---
title: "Postfix: Can't send or receive mail from outside"
date: 2008-06-30
forum: General Help
---

### Post by adam35413 on 2008-06-30
I am at a complete loss as to what to do. I have followed several guides online to setup my postfix server, and I have installed postfix and SASL. I can send email to my local users, but when I try to send email out to gmail, I get the message: 554 5.7.1 <myname@gmail.com> Relay access denied. When I try to send email to my server from gmail, the mail gets bounced back with a PERM_FAILURE 550-5.1.1. However, when I look in /var/log/mail.log, I don't see any error message to correspond with the gmail attempt at sending me mail.

I have gone through all the guides I can find and nothing is helping. Here is my main.cf:


```
# See /usr/share/postfix/main.cf.dist for a commented, more complete version


# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
myorigin = mydomain.com
myhostname = mydomain.com

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

alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
mydestination = mydomain.com, domU-12-...-1.internal, localhost.compute-1.internal, localhost
relayhost =
mynetworks = 127.0.0.0/8
mynetworks_style = host
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
mailbox_command = procmail -a "$EXTENSION"
inet_protocols = all
smtpd_sasl_local_domain =
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_sasl_authenticated_header = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtpd_tls_auth_only = no
smtp_use_tls = yes
smtp_tls_note_starttls_offer = yes
smtpd_tls_CAfile = /etc/postfix/ssl/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom

```
I can telnet mydomain.com 25 fine as well as telnet mydomain.com 587 fine. In both cases I get 220 mydomain.com ESMTP Postfix (Ubuntu)
Any help would be GREATLY appreciated.

---

