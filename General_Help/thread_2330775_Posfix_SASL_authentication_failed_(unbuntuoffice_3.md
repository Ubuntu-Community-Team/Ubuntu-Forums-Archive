---
title: "Posfix: SASL authentication failed (unbuntu/office 365)"
date: 2016-07-14
forum: General Help
---

### Post by clintonlee83 on 2016-07-14
[COLOR=#242729][FONT=Arial]I'm unable to get postfix to work with our office 365 mail.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]here's the main.cf file:[/FONT][/COLOR]
```
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

append_dot_mydomain = no

readme_directory = no

smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache


smtpd_relay_restrictions = permit_mynetworks permit_sasl_authenticated defer_unauth_destination
myhostname = signa-01
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = signa.com, signa-01, localhost.localdomain, localhost
relayhost = [smtp.office365.com]:587
mynetworks = 127.0.0.0/
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = loopback-only
inet_protocols = all
smtp_use_tls = yes
smtp_always_send_ehlo = yes
smtp_sasl_auth_enable = yes
smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd
smtp_sasl_security_options = noanonymous
smtp_sasl_tls_security_options = noanonymous
smtp_tls_security_level = encrypt
smtp_generic_maps = hash:/etc/postfix/generic
smtp_tls_CAfile = /etc/ssl/certs/ca-certificates.crt
smtp_sasl_mechanism_filter = login

```[COLOR=#242729][FONT=Arial]
And here is the error from mail.log:[/FONT][/COLOR]
```
 Jul 14 11:54:59 signa-01 postfix/error[17234]: DB0D6184D29: to=<clgsplace@gmail.com>, relay=none, delay=0.03, delays=0.02/0/0/0.01, dsn=4.7.3, status=deferred (delivery temporarily suspended: SASL authentication failed; server smtp.office365.com[132.245.25.2] said: 535 5.7.3 Authentication unsuccessful)

```

[COLOR=#242729][FONT=Arial]How can I fix this?[/FONT][/COLOR]

---

