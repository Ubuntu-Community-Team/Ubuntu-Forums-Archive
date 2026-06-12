---
title: "Exim / Dovecot config errors"
date: 2014-08-27
forum: General Help
---

### Post by theDaveTheRave on 2014-08-27
Hello all,

I'm trying to set up my first VPS for my new business web site.

Everything is fine up to the point of getting email to function.

I've installed dovecot, and I use the default exim4.

I've tested using swaks, and sending to an outside email which works fine... (modified email addresses to protect the innocent ;) ),


```
 swaks --to david.myers@gmail.com from = david.myers@myHostname.com auth auth-user=david.myers@myHostname.com auth-password = [stringOfNonsense] server imap.myHostname.com
=== Trying spool.mail.gandi.net:25...
=== Connected to spool.mail.gandi.net.
<-  220 spool.mail.gandi.net ESMTP Postfix
 -> EHLO myHostname.com
<-  250-spool.mail.gandi.net
<-  250-PIPELINING
<-  250-SIZE 35651584
<-  250-ETRN
<-  250-STARTTLS
<-  250-ENHANCEDSTATUSCODES
<-  250-8BITMIME
<-  250 DSN
 -> MAIL FROM:<davem@myHostname.com>
<-  250 2.1.0 Ok
 -> RCPT TO:<david.myers@gmail.com>
<-  250 2.1.5 Ok
 -> DATA
<-  354 End data with <CR><LF>.<CR><LF>
 -> Date: Wed, 27 Aug 2014 12:17:48 +0000
 -> To: david.myers@gmail.com
 -> From: davem@myHostname.com
 -> Subject: test Wed, 27 Aug 2014 12:17:48 +0000
 -> X-Mailer: swaks v20100211.0 jetmore.org/john/code/swaks/
 -> 
 -> This is a test mailing
 -> 
 -> .
<-  250 2.0.0 Ok: queued as 2A10959DB7
 -> QUIT
<-  221 2.0.0 Bye
=== Connection closed with remote host.

```

However if I try to send an email from my other mail account I get the following errors in exim4 / dovecot.

__exim4__
```
2014-08-27 12:32:27 H=slow1-d.mail.gandi.net [217.70.178.86] F=<david.myers@myHostname.com> rejected RCPT <david.myers@exsportee.biz>: relay not permitted
```

__dovecot__
```
Aug 27 12:26:27 imap(david.myers@exsportee.biz): Debug: maildir++: root=/var/mail/virtual/exsportee.biz/david.myers/mail, index=, control=, inbox=/var/mail/virtual/exsportee.biz/david.myers/mail, alt=

```

so something somewhere isn't working right.

Also when I attempt to send from thunderbird on my local pc, it asks for the password to the mail.myHostname.com mail server (not the imap.myHostname.com server), which unsurprisingly fails authentication. In this instance exim4 logs the following error

___exim4___
```
2014-08-27 12:37:47 login_saslauthd_server authenticator failed for 85-170-90-200.rev.numericable.fr ([192.168.0.14]) [85.170.90.200]: 435 Unable to authenticate at present (set_id=david.myers@myHostname.com): cannot connect to saslauthd daemon at /var/run/saslauthd/mux: Permission denied
2014-08-27 12:38:12 plain_saslauthd_server authenticator failed for 85-170-90-200.rev.numericable.fr ([192.168.0.14]) [85.170.90.200]: 435 Unable to authenticate at present (set_id=david.myers@myHostname.com): cannot connect to saslauthd daemon at /var/run/saslauthd/mux: Permission denied
2014-08-27 12:38:12 login_saslauthd_server authenticator failed for 85-170-90-200.rev.numericable.fr ([192.168.0.14]) [85.170.90.200]: 435 Unable to authenticate at present (set_id=david.myers@myHostname.com): cannot connect to saslauthd daemon at /var/run/saslauthd/mux: Permission denied

```

I though that exim could use the dovecot password login system ?

What I would like to finish with.

Multiple web sites on this single server (which works fine with apache).
virtual users having mail on these sites (ie they don't have an actual username/pwd for this machine, just for email)

Exim seems to be reading all the config options as I would have them do it

```

$ sudo exim -bP
no_accept_8bitmime
acl_not_smtp = 
acl_not_smtp_mime = 
acl_not_smtp_start = 
acl_smtp_auth = 
acl_smtp_connect = 
acl_smtp_data = acl_check_data
acl_smtp_dkim = 
acl_smtp_etrn = 
acl_smtp_expn = 
acl_smtp_helo = 
acl_smtp_mail = acl_check_mail
acl_smtp_mailauth = 
acl_smtp_mime = 
acl_smtp_notquit = 
acl_smtp_predata = 
acl_smtp_quit = 
acl_smtp_rcpt = acl_check_rcpt
acl_smtp_starttls = 
acl_smtp_vrfy = 
admin_groups =
no_allow_domain_literals
no_allow_mx_to_ip
no_allow_utf8_domains
auth_advertise_hosts = *
auto_thaw = 0s
av_scanner = sophie:/var/run/sophie
bi_command = 
bounce_message_file = 
bounce_message_text = 
bounce_return_body
bounce_return_message
bounce_return_size_limit = 100K
bounce_sender_authentication = 
callout_domain_negative_expire = 3h
callout_domain_positive_expire = 1w
callout_negative_expire = 2h
callout_positive_expire = 1d
callout_random_local_part = $primary_hostname-$tod_epoch-testing
check_log_inodes = 0
check_log_space = 0
check_rfc2047_length
check_spool_inodes = 0
check_spool_space = 0
daemon_smtp_ports = smtp
daemon_startup_retries = 9
daemon_startup_sleep = 30s
delay_warning = 1d
delay_warning_condition = ${if or {{ !eq{$h_list-id:$h_list-post:$h_list-subscribe:}{} }{ match{$h_precedence:}{(?i)bulk|list|junk} }{ match{$h_auto-submitted:}{(?i)auto-generated|auto-replied} }} {no}{yes}}
no_deliver_drop_privilege
deliver_queue_load_max =
delivery_date_remove
no_disable_ipv6
dkim_verify_signers = $dkim_signers
dns_again_means_nonexist = 
dns_check_names_pattern = (?i)^(?>(?(1)\.|())[^\W](?>[a-z0-9/_-]*[^\W])?)+(\.?)$
dns_csa_search_limit = 5
dns_csa_use_reverse
dns_ipv4_lookup = 
dns_retrans = 0s
dns_retry = 0
no_drop_cr
dsn_from = Mail Delivery System <Mailer-Daemon@$qualify_domain>
envelope_to_remove
errors_copy = 
errors_reply_to = 
exim_group = Debian-exim
exim_path = /usr/sbin/exim4
exim_user = Debian-exim
extra_local_interfaces = 
extract_addresses_remove_arguments
finduser_retries = 0
freeze_tell = postmaster
gecos_name = $1
gecos_pattern = ^([^,:]*)
no_gnutls_compat_mode
gnutls_require_kx = 
gnutls_require_mac = 
gnutls_require_protocols = 
header_line_maxsize = 0
header_maxsize = 1048576
headers_charset = UTF-8
helo_accept_junk_hosts = 
helo_allow_chars = 
helo_lookup_domains = @ : @[]
helo_try_verify_hosts = 
helo_verify_hosts = 
hold_domains = 
host_lookup = *
host_lookup_order = bydns:byaddr
host_reject_connection = 
hosts_connection_nolog = 
hosts_treat_as_local = 
ignore_bounce_errors_after = 2d
ignore_fromline_hosts = 
no_ignore_fromline_local
keep_malformed = 4d
ldap_default_servers = 
ldap_version = -1
no_local_from_check
local_from_prefix = 
local_from_suffix = 
local_interfaces = 92.39.247.92
local_scan_path = 
local_scan_timeout = 5m
local_sender_retain
localhost_number = 
log_file_path = /var/log/exim4/%slog
log_selector = +tls_peerdn
no_log_timezone
lookup_open_max = 25
max_username_length = 0
no_message_body_newlines
message_body_visible = 500
message_id_header_domain = 
message_id_header_text = 
message_logs
message_size_limit = 50M
no_move_frozen_messages
no_mua_wrapper
mysql_servers = 
never_users =
percent_hack_domains = 
no_perl_at_start
perl_startup = 
pgsql_servers = 
pid_file_path = /var/run/exim4/exim.pid
pipelining_advertise_hosts = *
no_preserve_message_logs
primary_hostname = vps4576-cloud.dns26.com
no_print_topbitchars
process_log_path = 
prod_requires_admin
qualify_domain = myHostname.com
qualify_recipient = myHostname.com
queue_domains = 
queue_list_requires_admin
no_queue_only
queue_only_file = 
queue_only_load =
queue_only_load_latch
queue_only_override
no_queue_run_in_order
queue_run_max = 5
queue_smtp_domains = 
receive_timeout = 0s
received_header_text = Received: ${if def:sender_rcvhost {from $sender_rcvhost\n\t}{${if def:sender_ident {from ${quote_local_part:$sender_ident} }}${if def:sender_helo_name {(helo=$sender_helo_name)\n\t}}}}by $primary_hostname ${if def:received_protocol {with $received_protocol}} ${if def:tls_cipher {($tls_cipher)\n\t}}(Exim $version_number)\n\t${if def:sender_address {(envelope-from <$sender_address>)\n\t}}id $message_exim_id${if def:received_for {\n\tfor $received_for}}
received_headers_max = 30
recipient_unqualified_hosts = 
recipients_max = 0
no_recipients_max_reject
remote_max_parallel = 2
remote_sort_domains = 
retry_data_expire = 1w
retry_interval_max = 1d
return_path_remove
rfc1413_hosts = *
rfc1413_query_timeout = 5s
sender_unqualified_hosts = 
smtp_accept_keepalive
smtp_accept_max = 20
smtp_accept_max_nonmail = 10
smtp_accept_max_nonmail_hosts = *
smtp_accept_max_per_connection = 1000
smtp_accept_max_per_host = 
smtp_accept_queue = 0
smtp_accept_queue_per_connection = 10
smtp_accept_reserve = 0
smtp_active_hostname = 
smtp_banner = $smtp_active_hostname ESMTP Exim $version_number $tod_full
smtp_check_spool_space
smtp_connect_backlog = 20
smtp_enforce_sync
smtp_etrn_command = 
smtp_etrn_serialize
smtp_load_reserve =
smtp_max_synprot_errors = 3
smtp_max_unknown_commands = 3
smtp_ratelimit_hosts = 
smtp_ratelimit_mail = 
smtp_ratelimit_rcpt = 
smtp_receive_timeout = 5m
smtp_reserve_hosts = 
no_smtp_return_error_details
spamd_address = 127.0.0.1 783
no_split_spool_directory
spool_directory = /var/spool/exim4
sqlite_lock_timeout = 5
no_strict_acl_vars
no_strip_excess_angle_brackets
no_strip_trailing_dot
syslog_duplication
syslog_facility = 
syslog_processname = exim
syslog_timestamp
system_filter = 
system_filter_directory_transport = 
system_filter_file_transport = 
system_filter_group =
system_filter_pipe_transport = 
system_filter_reply_transport = 
system_filter_user =
tcp_nodelay
timeout_frozen_after = 1w
timezone = 
tls_advertise_hosts = *
tls_certificate = /etc/exim4/exim.crt
tls_crl = 
tls_dhparam = 
tls_on_connect_ports = 
tls_privatekey = /etc/exim4/exim.key
no_tls_remember_esmtp
tls_require_ciphers = 
tls_try_verify_hosts = 
tls_verify_certificates = ${if exists{/etc/ssl/certs/ca-certificates.crt}{/etc/ssl/certs/ca-certificates.crt}{/dev/null}}
tls_verify_hosts = 
trusted_groups =
trusted_users = uucp
unknown_login = 
unknown_username = 
untrusted_set_sender = *
uucp_from_pattern = ^From\s+(\S+)\s+(?:[a-zA-Z]{3},?\s+)?(?:[a-zA-Z]{3}\s+\d?\d|\d?\d\s+[a-zA-Z]{3}\s+\d\d(?:\d\d)?)\s+\d\d?:\d\d?
uucp_from_sender = $1
warn_message_file = 
write_rejectlog

```


Is there anyone out there that has any idea how to solve my problem?

If you need any other files, just ask..

thanks in advance.

David

---

