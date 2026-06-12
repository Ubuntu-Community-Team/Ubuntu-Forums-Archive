---
title: "Postfix Alias Not Working"
date: 2007-11-30
forum: General Help
---

### Post by jakestaby on 2007-11-30
To give you a little background, I've been working with Linux on and off for the past couple years.  I currently run a web server with a few virtual domains, ssh, ftp, snort on an Ubuntu server.

I'm in need of setting up an email server, so I followed flurdy's tutorial [here](http://flurdy.com/docs/postfix/). (Much thanks)

My problem is in setting up aliases.  I'll take a few snapshots to show my settings.

aliases table
```
+------+--------------------------------+---------------------------+---------+
| pkid | mail                           | destination               | enabled |
+------+--------------------------------+---------------------------+---------+
|    8 | jake@domain.com       | jake@domain.com  |       1 |
|    9 | postmaster@domain.com | jake@domain.com  |       1 |
|   11 | sarah@domain.com      | sarah@domain.com |       1 |
|   12 | info@domain.com       | sarah@domain.com |       1 |
|   13 | webmaster@domain.com  | jake@domain.com  |       1 |
+------+--------------------------------+---------------------------+---------+
```

I've changed the real domain to domain.com, obviously.

/etc/aliases file
```
root:   jake
clamav: root
postmaster:     jake
webmaster:      jake
abuse:  jake
admin:  jake
info:   sarah
```

And here is the output of postconf -n
```
root@webstaby:/etc/postfix# postconf -n
alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
broken_sasl_auth_clients = yes
config_directory = /etc/postfix
delay_warning_time = 4h
disable_vrfy_command = yes
inet_interfaces = all
local_recipient_maps =
mailbox_size_limit = 0
masquerade_domains = mail.domain.com
masquerade_exceptions = root
maximal_backoff_time = 8000s
maximal_queue_lifetime = 3d
minimal_backoff_time = 1000s
mydestination =
myhostname = mail.domain.com
mynetworks = 127.0.0.0/8
recipient_delimiter = +
relayhost = mail.wavelink.com
smtp_helo_timeout = 60s
smtp_sasl_auth_enable = yes
smtp_sasl_password_maps = hash:/etc/postfix/saslpw
smtp_sasl_security_options =
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_client_restrictions = reject_rbl_client sbl.spamhaus.org, reject_rbl_client relays.ordb.org, reject_rbl_client blackholes.easynet.nl, reject_rbl_client dnsbl.njabl.org
smtpd_data_restrictions = reject_unauth_pipelining
smtpd_delay_reject = yes
smtpd_hard_error_limit = 12
smtpd_helo_required = yes
smtpd_helo_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_hostname, reject_invalid_hostname, permit
smtpd_recipient_limit = 16
smtpd_recipient_restrictions = reject_unauth_pipelining, permit_mynetworks, permit_sasl_authenticated, reject_non_fqdn_recipient, reject_unauth_destination, check_policy_service inet:127.0.0.1:60000, permit
smtpd_sasl_auth_enable = yes
smtpd_sasl_local_domain =
smtpd_sasl_security_options = noanonymous
smtpd_sender_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_sender, reject_unknown_sender_domain, reject_unauth_pipelining, permit #
smtpd_soft_error_limit = 3
smtpd_tls_cert_file = /etc/postfix/postfix.cert
smtpd_tls_key_file = /etc/postfix/postfix.key
smtpd_use_tls = yes
unknown_local_recipient_reject_code = 450
virtual_alias_maps = mysql:/etc/postfix/mysql_alias.cf
virtual_gid_maps = mysql:/etc/postfix/mysql_gid.cf
virtual_mailbox_base = /var/spool/mail/virtual
virtual_mailbox_domains = mysql:/etc/postfix/mysql_domains.cf
virtual_mailbox_maps = mysql:/etc/postfix/mysql_mailbox.cf
virtual_uid_maps = mysql:/etc/postfix/mysql_uid.cf
```

Any help would be very much appreciated.  Thanks in advance.

---

