---
title: "Postfix &amp; SSL"
date: 2014-01-25
forum: General Help
---

### Post by kj6eo2 on 2014-01-25
I'd like to ask a Postfix question.  I'd like to set up SMTP Authentication on Postfix so that I can relay when sending mail from my Android.  What would be the easiest way to accomplish that?  I'm running 12.04 LTS on a generic kernel with Postfix/Dovecot.  Any suggestions you might have would be appreciated!

Regards,

Bill - KJ6EO

---

### Post by kj6eo2 on 2014-01-25
Sorry, I got busy this morning and had to leave.  Here is some more information.  Postfix/Dovecot was installed from the "mailstack package".  It looks like everything is configured correctly but Postfix has no AUTH statement after EHLO.  Here are some more details:

main.cf

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
smtpd_tls_cert_file = /etc/ssl/certs/ssl-mail.pem
smtpd_tls_key_file = /etc/ssl/private/ssl-mail.key
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = mail.example.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = example.com, localhost.com, , localhost
relayhost = 
mynetworks = 127.0.0.0/8, 192.168.1.0/24, 
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
home_mailbox = Maildir/
smtpd_sasl_auth_enable = yes
smtpd_sasl_type = dovecot
smtpd_sasl_path = private/dovecot-auth
smtpd_sasl_authenticated_header = yes
smtpd_sasl_security_options = noanonymous
smtpd_sasl_local_domain = $myhostname
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = reject_unknown_sender_domain, reject_unknown_recipient_domain, reject_unauth_pipelining, permit_mynetworks, permit_sasl_authenticated, reject_unauth_destination
smtpd_sender_restrictions = reject_unknown_sender_domain, reject_rbl_client list.dsbl.org, reject_rbl_client sbl.spamhaus.org, reject_rbl_client cbl.abuseat.org, reject_rbl_client dul.dnsbl.sorbs.net
mailbox_command = /usr/lib/dovecot/deliver -c /etc/dovecot/conf.d/01-mail-stack-delivery.conf -m "${EXTENSION}"
smtp_use_tls = yes
smtpd_tls_received_header = yes
smtpd_tls_mandatory_protocols = SSLv3, TLSv1
smtpd_tls_mandatory_ciphers = medium
smtpd_tls_auth_only = yes
tls_random_source = dev:/dev/urandom

Dovecot (10.master.conf)

# Postfix smtp-auth
  unix_listener /var/spool/postfix/private/auth {
    mode = 0666
  }

Postfix login: (no AUTH)

example@example:/etc/postfix$ telnet localhost 25
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
220 mail.example.com ESMTP Postfix (Ubuntu)
ehlo example.com
250-mail.example.com
250-PIPELINING
250-SIZE 10240000
250-VRFY
250-ETRN
250-STARTTLS
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN

Any thoughts you might have would be appreciated!

Regards,

Bill - KJ6EO

---

