---
title: "Postfix giving 550 Administrative prohibition"
date: 2012-12-21
forum: General Help
---

### Post by madbadger89 on 2012-12-21
Hello,

We run a local Ubuntu server environment.  I was thrust into the server management role, and consider myself a barely functional Ubuntu user (I can navigate command line, troubleshoot basic issues, add users, install stuff) but this error is beyond me.

550 550 Administrative prohibition (state 13).
This occurs on 3 mailing lists, any email address (Gmail, yahoo, etc).  The users are authorized.  I restarted the mail services, and the server to no avail.
There have been no system changes, to my knowledge.  Mailman runs correctly, and this is a postfix specific error.  We run our own mail server etc, and do not use Blacklists. Does anyone have any suggestions?

Also, using telnet mail.domain.co 25 connects. And I escaped chroot using this document [https://help.ubuntu.com/8.04/serverguide/postfix.html](https://help.ubuntu.com/8.04/serverguide/postfix.html)

So I am a liar.  This is an issue with exim4.  For some reason we have postfix and exim4.

---

### Post by Rexilion on 2012-12-21
Could you post the postfix configuration? E.g. /etc/postfix/main.cf and maybe anything else in /etc/postfix/*.

---

### Post by madbadger89 on 2012-12-21
> **Rexilion said:**
> Could you post the postfix configuration? E.g. /etc/postfix/main.cf and maybe anything else in /etc/postfix/*.

 See /usr/share/postfix/main.cf.dist for a commented, more complete version


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

myhostname = peaches
alias_maps = hash:/etc/aliases, hash:/var/lib/mailman/data/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = [myhostname], peaches, localhost.localdomain, localhost
relayhost =
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
relay_domains = [myhostname]
transport_maps = hash:/etc/postfix/transport
mailman_destination_recipient_limit = 1
------------------------------------------------------------

---

