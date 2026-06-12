---
title: "Mail-problem (with internal mails)"
date: 2014-03-07
forum: General Help
---

### Post by alis5 on 2014-03-07
Hello,
 
I’m having some problem getting my (internal) mail to work.
 
I use Zarafa, postfix, mysql, (yaffas as a framework to look at the config from the web).
The server is has Ubuntu 12.04lts installed, the IP for it is 192.168.0.100.
I’m getting the mail to my server (which is behind my router, 192.168.0.1), but they get stuck at postfix (in the mailqueue). 
My mail is [EMAIL="glenn@glenso.so"]glenn@glenso.so[/EMAIL] and glenn is my login at mysql as well (same password), zarafa uses the thing. But Yaffas couldn’t use the same username, so it’s “nick” instead.
 
I can open office and web-access to see my (old) mail, (backup from an earlier installation). And I can send emails to the rest of the world (like Hotmail). But NOT to my own server. Which results in that the incoming mails get stuck in postfix and I can’t send internal emails to my self.
 
I better also mention that I’m not that used to Linux, but I’m starting to pick it up.
 
The error in mail.log is this:
Mar  7 18:57:16 greenavserver postfix/pickup[10820]: 5883D2F802C6: uid=108 from=<glenn@glenso.se> orig_id=04AC42F80582
Mar  7 18:57:16 glensoserver postfix/cleanup[10982]: 5883D2F802C6: message-id=<zarafa.5318d718.0d98.7450d26e75423a80@glensoserver.greenav.se>
Mar  7 18:57:16 glensoserver postfix/qmgr[10821]: 5883D2F802C6: from=<glenn@glenso.se>, size=14649, nrcpt=1 (queue active)
Mar  7 18:57:16 glensoserver postfix/lmtp[10984]: 5883D2F802C6: to=<glenn@glenso.se>, relay=127.0.0.1[127.0.0.1]:2003, delay=78180, delays=78180/0.02/0.03/0, dsn=4.4.2, status=deferred (lost connection with 127.0.0.1[127.0.0.1] while receiving the initial server greeting)
 
My mail.cf is:
smtpd_banner = $myhostname ESMTP $mail_name
biff = no
append_dot_mydomain = no
readme_directory = no
smtpd_tls_cert_file=/opt/yaffas/etc/ssl/certs/postfix.crt
smtpd_tls_key_file=/opt/yaffas/etc/ssl/certs/postfix.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtp_tls_security_level = may
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
# inet_interfaces = 192.168.0.100, 127.0.0.1
mydestination = localhost
#mydestination = $myhostname, localhost.$myhostname
#mydestination = greenavserver.greenav.se, grennav.se, localhost, localhost.localdomain
mynetworks = [::1]/128, [::ffff:127.0.0.0]/104, 127.0.0.0/8
#mynetworks = [::1]/128, [::ffff:127.0.0.0]/104, 127.0.0.0/8, 192.168.0.0/24, 192.168.0.100
#mynetworks = 127.0.0.0/8 [::1]/128
#mydestination = $myhostname, /etc/postfix/virtual_users_global
# mynetworks = 0.0.0.0/0 [::/0]
mailbox_transport = zarafa
#virtual_mailbox_domains = localhost
virtual_mailbox_domains = greenav.se, localhost
virtual_mailbox_maps = ldap:/etc/postfix/ldap-users.cf
virtual_alias_maps = regexp:/etc/postfix/virtual_users_global, ldap:/etc/postfix/ldap-aliases.cf, hash:/etc/postfix/ldap-group.cf
virtual_transport = lmtp:127.0.0.1:2003
#content_filter =
content_filter = smtp-amavis:[127.0.0.1]:10024
smtpd_helo_required = yes
smtpd_delay_reject = yes
smtpd_recipient_restrictions = permit_mynetworks, permit_sasl_authenticated, reject_unauth_destination, reject_unknown_recipient_domain
reject_unauth_destination, reject_unknown_recipient_domain
# myhostname = greenavserver
myhostname = greenav.se
message_size_limit = 524288000
hash:/etc/postfix/ldap-group.cf
mailbox_command = /usr/bin/zarafa-dagent "$USER"
$daemon_directory/$process_name $process_id & sleep 5
relayhost = [smtp.bredband.net]
smtp_sasl_auth_enable = no
smtp_sasl_password_maps = hash:/etc/postfix/smtp_auth.cf
smtp_sasl_security_options = noanonymous
local_header_rewrite_clients =
remote_header_rewrite_domain =
disable_dns_lookups = yes
zarafa_admin =
 
The things that are out-comment are things that I tried but didn’t help.
 
This is my master.cf:
587      inet  n       -       -       -       -       smtpd
smtp      inet  n       -       -       -       -       smtpd
submission inet n       -       -       -       -       smtpd
  -o smtpd_tls_security_level=encrypt
  -o smtpd_sasl_auth_enable=yes
  -o smtpd_client_restrictions=permit_sasl_authenticated,reject
  -o milter_macro_daemon_name=ORIGINATING
smtps     inet  n       -       -       -       -       smtpd
  -o smtpd_tls_wrappermode=yes
  -o smtpd_sasl_auth_enable=yes
  -o smtpd_client_restrictions=permit_sasl_authenticated,reject
  -o milter_macro_daemon_name=ORIGINATING
#628      inet  n       -       -       -       -       qmqpd
pickup    fifo  n       -       -       60      1       pickup
        -o content_filter=
        -o receive_override_options=no_header_body_checks
cleanup   unix  n       -       -       -       0       cleanup
qmgr      fifo  n       -       n       300     1       qmgr
#qmgr     fifo  n       -       -       300     1       oqmgr
tlsmgr    unix  -       -       -       1000?   1       tlsmgr
rewrite   unix  -       -       -       -       -       trivial-rewrite
bounce    unix  -       -       -       -       0       bounce
defer     unix  -       -       -       -       0       bounce
trace     unix  -       -       -       -       0       bounce
verify    unix  -       -       -       -       1       verify
flush     unix  n       -       -       1000?   0       flush
proxymap  unix  -       -       n       -       -       proxymap
proxywrite unix -       -       n       -       1       proxymap
smtp      unix  -       -       -       -       -       smtp
# When relaying mail as backup MX, disable fallback_relay to avoid MX loops
relay     unix  -       -       -       -       -       smtp
        -o smtp_fallback_relay=
showq     unix  n       -       -       -       -       showq
error     unix  -       -       -       -       -       error
retry     unix  -       -       -       -       -       error
discard   unix  -       -       -       -       -       discard
local     unix  -       n       n       -       -       local
virtual   unix  -       n       n       -       -       virtual
lmtp      unix  -       -       -       -       -       lmtp
anvil     unix  -       -       -       -       1       anvil
scache    unix  -       -       -       -       1       scache
maildrop  unix  -       n       n       -       -       pipe
  flags=DRhu user=vmail argv=/usr/bin/maildrop -d ${recipient}
uucp      unix  -       n       n       -       -       pipe
  flags=Fqhu user=uucp argv=uux -r -n -z -a$sender - $nexthop!rmail ($recipient)
ifmail    unix  -       n       n       -       -       pipe
  flags=F user=ftn argv=/usr/lib/ifmail/ifmail -r $nexthop ($recipient)
bsmtp     unix  -       n       n       -       -       pipe
  flags=Fq. user=bsmtp argv=/usr/lib/bsmtp/bsmtp -t$nexthop -f$sender $recipient
scalemail-backend unix  -       n       n       -       2       pipe
  flags=R user=scalemail argv=/usr/lib/scalemail/bin/scalemail-store ${nexthop} ${user} ${extension}
mailman   unix  -       n       n       -       -       pipe
  flags=FR user=list argv=/usr/lib/mailman/bin/postfix-to-mailman.py
  ${nexthop} ${user}
zarafa    unix -        n       n       -       10      pipe
  flags=DRhu user=vmail argv=/usr/bin/zarafa-dagent   -R  ${recipient}
amavis unix - - - - 2 smtp
        -o smtp_data_done_timeout=1200
        -o smtp_send_xforward_command=yes
        -o disable_dns_lookups=yes
        -o max_use=20
127.0.0.1:10025 inet n - - - - smtpd
        -o content_filter=
        -o local_recipient_maps=
        -o relay_recipient_maps=
        -o smtpd_restriction_classes=
        -o smtpd_delay_reject=no
        -o smtpd_client_restrictions=permit_mynetworks,reject
        -o smtpd_helo_restrictions=
        -o smtpd_sender_restrictions=
        -o smtpd_recipient_restrictions=permit_mynetworks,reject
        -o smtpd_data_restrictions=reject_unauth_pipelining
        -o smtpd_end_of_data_restrictions=
        -o mynetworks=127.0.0.0/8
        -o smtpd_error_sleep_time=0
        -o smtpd_soft_error_limit=1001
        -o smtpd_hard_error_limit=1000
        -o smtpd_client_connection_count_limit=0
        -o smtpd_client_connection_rate_limit=0
        -o receive_override_options=no_header_body_checks,no_unknown_recipient_checks
 
Mysql-aliases.cf (which I thought might could cause some errors here) are:
user = glenn
#user = nick
password = ****** (I have comment away this)
hosts = 127.0.0.1
dbname = glenso
#dbname = zarafa
 
 
Do anyone has some suggestions on where to start to look for faults?
I have struggled with this for quite some time now, and start to run out of ideas.
 
Thanks for help!

---

### Post by alis5 on 2014-03-08
No one that has any suggestions/ideas?

---

### Post by alis5 on 2014-03-09
bump

---

