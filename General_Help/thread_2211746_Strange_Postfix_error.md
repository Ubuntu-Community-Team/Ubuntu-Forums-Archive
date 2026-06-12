---
title: "Strange Postfix error"
date: 2014-03-17
forum: General Help
---

### Post by s-stefanov on 2014-03-17
There are a few hosts which ocasionally throw errors like these:

1286:Mar 17 15:01:08 Server postfix/smtpd[1324]: connect from mail-ob0-f169.google.com[209.85.214.169]
1287:Mar 17 15:01:09 Server postfix/smtpd[1324]: Anonymous TLS connection established from mail-ob0-f169.google.com[209.85.214.169]: TLSv1 with cipher ECDHE-RSA-RC4-SHA (128/128 bits)
1291:Mar 17 15:01:10 Server postfix/smtpd[1324]: 69A87280008: client=mail-ob0-f169.google.com[209.85.214.169]
1301:Mar 17 15:01:15 Server postfix/smtpd[1324]: disconnect from mail-ob0-f169.google.com[209.85.214.169]
1313:Mar 17 15:02:20 Server postfix/smtpd[1324]: connect from unknown[113.11.251.194]
1314:Mar 17 15:02:21 Server postfix/smtpd[1324]: Anonymous TLS connection established from unknown[113.11.251.194]: TLSv1.2 with cipher ECDHE-RSA-AES256-GCM-SHA384 (256/256 bits)
1315:Mar 17 15:02:22 Server postfix/smtpd[1324]: warning: unknown smtpd restriction: "????"
1316:Mar 17 15:02:22 Server postfix/smtpd[1324]: NOQUEUE: reject: RCPT from unknown[113.11.251.194]: 451 4.3.5 Server configuration error; from=<> to=<user@mydomain.com> proto=ESMTP helo=<vps.enggsol.com>

Postfix reloads do not throw any errors so it's not a syntax problem within the config files. Checked the different restriction files too - nothing suspicious. Any clues what might be throwing these four exclamation marks?

Here is postconf -n output:

```


alias_database = hash:/etc/postfix/aliases
alias_maps = hash:/etc/postfix/aliases
append_dot_mydomain = no
biff = no
body_checks = regexp:/etc/postfix/sender_access.regexp
broken_sasl_auth_clients = no
config_directory = /etc/postfix
content_filter = amavis:[127.0.0.1]:10024
disable_vrfy_command = yes
header_checks = regexp:/etc/postfix/sender_access.regexp
inet_interfaces = all
inet_protocols = ipv4
invalid_hostname_reject_code = 450
mailbox_size_limit = 0
maps_rbl_reject_code = 450
maximal_backoff_time = 8000s
maximal_queue_lifetime = 7d
message_size_limit = 0
milter_default_action = accept
milter_protocol = 6
minimal_backoff_time = 1000s
myhostname = mail.mydomain.com
mynetworks = 127.0.0.0/8, 192.168.0.0/24
mynetworks_style = subnet
myorigin = /etc/mailname
non_fqdn_reject_code = 450
non_smtpd_milters = inet:localhost:8891
notify_classes = bounce, delay, policy, protocol, resource, software
policy-spf_time_limit = 3600s
readme_directory = no
recipient_delimiter = +
reject_code = 450
relayhost =
smtp_helo_timeout = 60s
smtp_tls_CAfile = /etc/ssl/certs/ca-certificates.crt
smtp_tls_note_starttls_offer = yes
smtp_tls_security_level = may
smtpd_banner = $myhostname ESMTP $mail_name
smtpd_data_restrictions = reject_unauth_pipelining, permit
smtpd_delay_reject = yes
smtpd_hard_error_limit = 12
smtpd_helo_required = yes
smtpd_milters = inet:localhost:8891
smtpd_recipient_limit = 16
smtpd_recipient_restrictions = permit_mynetworks permit_sasl_authenticated reject_unauth_destination check_client_access hash:/etc/postfix/client_access check_helo_access hash:/etc/postfix/helo_access check_sender_access hash:/etc/postfix/sender_access.list check_sender_mx_access cidr:/etc/postfix/mx_access reject_unknown_client_hostname reject_invalid_helo_hostname reject_non_fqdn_helo_hostname reject_unknown_helo_hostname reject_non_fqdn_sender reject_sender_login_mismatch reject_unknown_sender_domain reject_non_fqdn_recipient reject_unknown_recipient_domain check_policy_service inet:127.0.0.1:10023 check_policy_service unix:private/policy-spf permit_dnswl_client list.dnswl.org reject_rhsbl_sender dbl.spamhaus.org reject_rhsbl_sender fresh15.spameatingmonkey.net reject_rhsbl_sender uribl.spameatingmonkey.net reject_rhsbl_sender urired.spameatingmonkey.net reject_rbl_client aspews.ext.sorbs.net reject_rbl_client b.barracudacentral.org reject_rbl_client backscatter.spameatingmonkey.net reject_rbl_client bl.mailspike.net reject_rbl_client bl.spameatingmonkey.net reject_rbl_client cidr.bl.mcafee.com reject_rbl_client ix.dnsbl.manitu.net reject_rbl_client psbl.surriel.com reject_rbl_client spam.spamrats.com reject_rbl_client spamsources.fabel.dk reject_rbl_client truncate.gbudb.net reject_rbl_client zen.spamhaus.org reject_rhsbl_client dbl.spamhaus.org reject_rhsbl_client fresh15.spameatingmonkey.net reject_rhsbl_client hostkarma.junkemailfilter.com=127.0.0.2 reject_rhsbl_client uribl.spameatingmonkey.net reject_rhsbl_client urired.spameatingmonkey.net reject_rhsbl_reverse_client dbl.spamhaus.org permit
smtpd_sasl_auth_enable = yes
smtpd_sasl_local_domain =
smtpd_sasl_security_options = noanonymous
smtpd_sender_login_maps = mysql:/etc/postfix/mysql_sender_login_maps.cf
smtpd_soft_error_limit = 3
smtpd_tls_cert_file = /etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file = /etc/ssl/private/ssl-cert-snakeoil.key
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_security_level = may
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom
unknown_address_reject_code = 450
unknown_client_reject_code = 450
unknown_hostname_reject_code = 450
unknown_local_recipient_reject_code = 450
unverified_sender_reject_code = 450
virtual_alias_maps = mysql:/etc/postfix/mysql_alias.cf
virtual_gid_maps = static:5000
virtual_mailbox_base = /var/spool/mail/virtual
virtual_mailbox_domains = mysql:/etc/postfix/mysql_domains.cf
virtual_mailbox_limit = 0
virtual_mailbox_maps = mysql:/etc/postfix/mysql_mailbox.cf
virtual_uid_maps = static:5000

```

---

### Post by s-stefanov on 2014-03-31
Really, noone?

---

