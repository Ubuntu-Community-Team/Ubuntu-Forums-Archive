---
title: "Can't send email from outside network"
date: 2007-10-18
forum: General Help
---

### Post by Akebono on 2007-10-18
Just installed Gutsy Gibbon and I am having a problem sending an email to myself from outside the local network. When I try to send an email thru my GMail account, I get a bounceback saying "The followng recipient cannot be reached: [email]myname@mydomain.com[/email]. The error is 550 5.1.1 User unknown. However, I can send the mail within the local network using telnet and I have no errors. Is this a configuration problem?

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
smtpd_tls_cert_file = /etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file = /etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = Orac
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = mydomain.com, Orac, localhost.localdomain, localhost
relayhost = 
mynetworks = 127.0.0.0/8
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
smtpd_recipient_restrictions = permit_mynetworks reject_unauth_destination

---

### Post by dcstar on 2007-10-18
> **Akebono said:**
> Just installed Gutsy Gibbon and I am having a problem sending an email to myself from outside the local network. When I try to send an email thru my GMail account, I get a bounceback saying "The followng recipient cannot be reached: [email]myname@mydomain.com[/email]. The error is 550 5.1.1 User unknown. However, I can send the mail within the local network using telnet and I have no errors. Is this a configuration problem?
.........

And exactly what is in your /etc/hostname and hosts files?

---

