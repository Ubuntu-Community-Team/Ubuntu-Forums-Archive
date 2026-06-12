---
title: "Ubuntu 13.04 Server - Mail Server - External Mail Issues"
date: 2013-06-02
forum: General Help
---

### Post by xExekut3x on 2013-06-02
I'm able to send/receive mail internally on my LAN fine. I'm unable to send mail or receive mail externally. I contacted my ISP and discovered they block port 25. So I changed my default port to 587, or at least according to this guide [https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix) > Using Port 587 for Secure Submission
If you want to use port 587 as the submission port for SMTP mail rather than 25 (many ISPs block port 25), you will need to edit /etc/postfix/master.cf and uncomment the line  submission inet n      -       n       -       -       smtpd The guides I followed for setting up my Mail Server all came from here [https://help.ubuntu.com/community/MailServer](https://help.ubuntu.com/community/MailServer). I'm using Postfix, Dovecot, and SquirrelMail.     [https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix) [https://help.ubuntu.com/community/PostfixBasicSetupHowto](https://help.ubuntu.com/community/PostfixBasicSetupHowto) [https://help.ubuntu.com/community/Dovecot](https://help.ubuntu.com/community/Dovecot) [https://help.ubuntu.com/community/Squirrelmail](https://help.ubuntu.com/community/Squirrelmail)  Here are my configuration files for Dovecot and Postfix. mainc.cf > #myorigin = /etc/mailname
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no
append_dot_mydomain = no
#delay_warning_time = 4h
readme_directory = no
smtpd_tls_cert_file = /etc/ssl/certs/smtpd.crt
smtpd_tls_key_file = /etc/ssl/private/smtpd.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtpd_relay_restrictions = permit_mynetworks permit_sasl_authenticated defer_unauth_destination
myhostname = srv1.example.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = srv1.example.com, mail.example.com, example.com, localhost.example.com, , localhost
relayhost = 
mynetworks = 127.0.0.0/8, 10.0.0.0/27
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = ipv4
home_mailbox = Maildir/
mailbox_command = 
smtpd_sasl_local_domain = 
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtp_tls_security_level = may
smtpd_tls_security_level = may
smtpd_tls_auth_only = no
smtp_tls_note_starttls_offer = yes
smtpd_tls_CAfile = /etc/ssl/certs/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom
content_filter = smtp-amavis:[127.0.0.1]:10024
 master.cf > smtp      inet  n       -       -       -       -       smtpd
#587   inet  n - n - - smtpd
#smtp      inet  n       -       -       -       1       postscreen
#smtpd     pass  -       -       -       -       -       smtpd
#dnsblog   unix  -       -       -       -       0       dnsblog
#tlsproxy  unix  -       -       -       -       0       tlsproxy
submission inet n       -       -       -       -       smtpd
#  -o syslog_name=postfix/submission
#  -o smtpd_tls_security_level=encrypt
#  -o smtpd_sasl_auth_enable=yes
#  -o smtpd_reject_unlisted_recipient=no
#  -o smtpd_client_restrictions=$mua_client_restrictions
#  -o smtpd_helo_restrictions=$mua_helo_restrictions
#  -o smtpd_sender_restrictions=$mua_sender_restrictions
#  -o smtpd_recipient_restrictions=permit_sasl_authenticated,reject
#  -o milter_macro_daemon_name=ORIGINATING
#smtps     inet  n       -       -       -       -       smtpd
#  -o syslog_name=postfix/smtps
#  -o smtpd_tls_wrappermode=yes
#  -o smtpd_sasl_auth_enable=yes
#  -o smtpd_reject_unlisted_recipient=no
#  -o smtpd_client_restrictions=$mua_client_restrictions
#  -o smtpd_helo_restrictions=$mua_helo_restrictions
#  -o smtpd_sender_restrictions=$mua_sender_restrictions
#  -o smtpd_recipient_restrictions=permit_sasl_authenticated,reject
#  -o milter_macro_daemon_name=ORIGINATING
#628       inet  n       -       -       -       -       qmqpd
pickup    unix  n       -       -       60      1       pickup
  -o content_filter=
         -o receive_override_options=no_header_body_checks
cleanup   unix  n       -       -       -       0       cleanup
qmgr      unix  n       -       n       300     1       qmgr
#qmgr     unix  n       -       n       300     1       oqmgr
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
relay     unix  -       -       -       -       -       smtp
#       -o smtp_helo_timeout=5 -o smtp_connect_timeout=5
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
scalemail-backend unix - n n - 2 pipe
  flags=R user=scalemail argv=/usr/lib/scalemail/bin/scalemail-store ${nexthop} ${user} ${extension}
mailman   unix  -       n       n       -       -       pipe
  flags=FR user=list argv=/usr/lib/mailman/bin/postfix-to-mailman.py
  ${nexthop} ${user}
smtp-amavis     unix    -       -       -       -       2       smtp
        -o smtp_data_done_timeout=1200
        -o smtp_send_xforward_command=yes
        -o disable_dns_lookups=yes
        -o max_use=20
127.0.0.1:10025 inet    n       -       -       -       -       smtpd
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
 dovecot.conf > disable_plaintext_auth = no
listen = *
mail_location = maildir:/home/%u/Maildir
namespace inbox {
  inbox = yes
  location = 
  mailbox Drafts {
    special_use = \Drafts
  }
  mailbox Junk {
    special_use = \Junk
  }
  mailbox Sent {
    special_use = \Sent
  }
  mailbox "Sent Messages" {
    special_use = \Sent
  }
  mailbox Trash {
    special_use = \Trash
  }
  prefix = 
}
auth_mechanisms = plain
passdb {
  driver = pam
}
protocols = imap
ssl_cert = </etc/ssl/certs/server.crt
ssl_key = </etc/ssl/private/server.key
userdb {
  driver = passwd
}
 Here is my DNS Zone File from GoDaddy > ; Domain: example.com
; Exported (y-m-d hh:mm:ss): 2013-06-01 22:42:03
;
; This file is intended for use for informational and archival
; purposes ONLY and MUST be edited before use on a production
; DNS server.
;
; In particular, you must update the SOA record with the correct
; authoritative name server and contact e-mail address information,
; and add the correct NS records for the name servers which will
; be authoritative for this domain.
;
; For further information, please consult the BIND documentation
; located on the following website:
;
; [http://www.isc.org/](http://www.isc.org/)
;
; And RFC 1035:
;
; [http://www.ietf.org/rfc/rfc1035.txt](http://www.ietf.org/rfc/rfc1035.txt)
;
; Please note that we do NOT offer technical support for any use
; of this zone data, the BIND name server, or any other third-
; party DNS software.
;
; Use at your own risk.
; SOA Record
EXAMPLE.COM. 3600 IN SOA ns03.domaincontrol.com. dns.jomax.net (
    2013060107
    28800
    7200
    604800
    600
    )
; A Records
@ 604800 IN A ***.***.***.***
; CNAME Records
www 3600 IN CNAME @
ftp 3600 IN CNAME @
svn 3600 IN CNAME @
; MX Records
mail 3600 IN MX 0 srv1.EXAMPLE.COM
; NS Records
@ 3600 IN NS ns03.domaincontrol.com
@ 3600 IN NS ns04.domaincontrol.com

 I've edited out my web address and IP with example.com and ***.***.***.***. Any help on this issues would be much appreciated.

---

### Post by xExekut3x on 2013-06-02
Maybe some error logs might help. mail.err > Jun  1 22:26:25 srv1 dovecot: ssl-params: Fatal: Timeout while waiting for /var/lib/dovecot/ssl-parameters.dat generation to complete
Jun  1 23:36:48 srv1 dovecot: imap-login: Fatal: Can't load ssl_cert: There is no valid PEM certificate. (You probably forgot '<' from ssl_cert=</etc/ssl/certs/server.crt)
Jun  1 23:36:48 srv1 dovecot: master: Error: service(imap-login): command startup failed, throttling for 2 secs
 mail.log > 
Jun  2 01:16:07 srv1 postfix/qmgr[28056]: C8FDE240B69: removed
Jun  2 01:16:07 srv1 postfix/smtp[28077]: connect to gmail-smtp-in.l.google.com[2607:f8b0:400d:c00::1a]:25: Network is unreachable
Jun  2 01:16:37 srv1 postfix/smtp[28077]: connect to gmail-smtp-in.l.google.com[173.194.68.27]:25: Connection timed out
Jun  2 01:17:07 srv1 postfix/smtp[28077]: connect to alt1.gmail-smtp-in.l.google.com[173.194.78.27]:25: Connection timed out
Jun  2 01:17:07 srv1 postfix/smtp[28077]: connect to alt1.gmail-smtp-in.l.google.com[2a00:1450:400c:c03::1b]:25: Network is unreachable
Jun  2 01:17:37 srv1 postfix/smtp[28077]: connect to alt2.gmail-smtp-in.l.google.com[173.194.65.27]:25: Connection timed out
Jun  2 01:17:37 srv1 postfix/smtp[28077]: 25027240B6A: to=<[EMAIL="example@gmail.com"]example@gmail.com[/EMAIL]>, relay=none, delay=91, delays=0.01/0.03/91/0, dsn=4.4.1, status=deferred (connect to alt2.gmail-smtp-in.l.google.com[173.194.65.27]:25: Connection timed out)
Jun  2 01:18:02 srv1 postfix/master[28052]: terminating on signal 15
Jun  2 01:18:02 srv1 postfix/master[28238]: daemon started -- version 2.10.0, configuration /etc/postfix
Jun  2 01:18:41 srv1 postfix/smtpd[28251]: connect from localhost.localdomain[127.0.0.1]
Jun  2 01:18:41 srv1 postfix/smtpd[28251]: 893A5240B6B: client=localhost.localdomain[127.0.0.1]
Jun  2 01:18:41 srv1 postfix/cleanup[28255]: 893A5240B6B: message-id=<[EMAIL="0e37fdb5db862a3798e8702c952be599.squirrel@example.com"]0e37fdb5db862a3798e8702c952be599.squirrel@example.com[/EMAIL]>
Jun  2 01:18:41 srv1 postfix/qmgr[28242]: 893A5240B6B: from=<[EMAIL="administrator@srv1.rannday.com"]administrator@srv1._[COLOR=#0066cc]example.com[/COLOR]_[/EMAIL]>, size=723, nrcpt=1 (queue active)
Jun  2 01:18:41 srv1 postfix/smtpd[28251]: disconnect from localhost.localdomain[127.0.0.1]
Jun  2 01:18:41 srv1 dovecot: imap-login: Login: user=<administrator>, method=PLAIN, rip=127.0.0.1, lip=127.0.0.1, mpid=28262, secured, session=<R+Q1+yTeWAB/AAAB>
Jun  2 01:18:41 srv1 amavis[26753]: (26753-03) (!)run_av (ClamAV-clamd) FAILED - unexpected , output="/var/lib/amavis/tmp/amavis-20130602T001836-26753-OP6zLyQj/parts: lstat() failed: Permission denied. ERROR\n"
Jun  2 01:18:41 srv1 amavis[26753]: (26753-03) (!)ClamAV-clamd av-scanner FAILED: CODE(0x140f620) unexpected , output="/var/lib/amavis/tmp/amavis-20130602T001836-26753-OP6zLyQj/parts: lstat() failed: Permission denied. ERROR\n" at (eval 112) line 899.
Jun  2 01:18:41 srv1 amavis[26753]: (26753-03) (!)WARN: all primary virus scanners failed, considering backups
Jun  2 01:18:41 srv1 dovecot: imap(administrator): Disconnected: Logged out in=613 out=471
Jun  2 01:18:41 srv1 dovecot: imap-login: Login: user=<administrator>, method=PLAIN, rip=127.0.0.1, lip=127.0.0.1, mpid=28266, secured, session=<P7w5+yTeWgB/AAAB>
Jun  2 01:18:41 srv1 dovecot: imap(administrator): Disconnected: Logged out in=292 out=1811
Jun  2 01:18:59 srv1 postfix/smtpd[28280]: connect from localhost.localdomain[127.0.0.1]
Jun  2 01:18:59 srv1 postfix/smtpd[28280]: D051A240B6C: client=localhost.localdomain[127.0.0.1]
Jun  2 01:18:59 srv1 postfix/cleanup[28255]: D051A240B6C: message-id=<[EMAIL="0e37fdb5db862a3798e8702c952be599.squirrel@rannday.com"]0e37fdb5db862a3798e8702c952be599.squirrel@_[COLOR=#0066cc]example.com[/COLOR]_[/EMAIL]>
Jun  2 01:18:59 srv1 postfix/qmgr[28242]: D051A240B6C: from=<[EMAIL="administrator@srv1.rannday.com"]administrator@srv1._[COLOR=#0066cc]example.com[/COLOR]_[/EMAIL]>, size=1180, nrcpt=1 (queue active)
Jun  2 01:18:59 srv1 postfix/smtpd[28280]: disconnect from localhost.localdomain[127.0.0.1]
Jun  2 01:18:59 srv1 amavis[26753]: (26753-03) Passed CLEAN {RelayedOutbound}, LOCAL [127.0.0.1]:59285 [***.***.***.***] <[EMAIL="administrator@srv1.rannday.com"]administrator@srv1._[COLOR=#0066cc]example.com[/COLOR]_[/EMAIL]> -> <[EMAIL="example@gmail.com"]example[/EMAIL][EMAIL="rannday5@gmail.com"]@gmail.com[/EMAIL]>, Queue-ID: 893A5240B6B, Message-ID: <[EMAIL="0e37fdb5db862a3798e8702c952be599.squirrel@rannday.com"]0e37fdb5db862a3798e8702c952be599.squirrel@_[COLOR=#0066cc]example.com[/COLOR]_[/EMAIL]>, mail_id: Woy-Bzht4-5B, Hits: 0.179, size: 723, queued_as: D051A240B6C, 18250 ms
Jun  2 01:18:59 srv1 postfix/smtp[28256]: 893A5240B6B: to=<[EMAIL="example@gmail.com"]example[/EMAIL][EMAIL="rannday5@gmail.com"]@gmail.com[/EMAIL]>, relay=127.0.0.1[127.0.0.1]:10024, delay=18, delays=0.05/0.02/0.01/18, dsn=2.0.0, status=sent (250 2.0.0 from MTA(smtp:[127.0.0.1]:10025): 250 2.0.0 Ok: queued as D051A240B6C)
Jun  2 01:18:59 srv1 postfix/qmgr[28242]: 893A5240B6B: removed
Jun  2 01:19:30 srv1 postfix/smtp[28281]: connect to gmail-smtp-in.l.google.com[173.194.68.27]:25: Connection timed out
Jun  2 01:19:45 srv1 dovecot: imap-login: Login: user=<administrator>, method=PLAIN, rip=127.0.0.1, lip=127.0.0.1, mpid=28290, secured, session=<E+8G/yTeYgB/AAAB>
Jun  2 01:19:45 srv1 dovecot: imap(administrator): Disconnected: Logged out in=292 out=1811
Jun  2 01:19:55 srv1 dovecot: imap-login: Login: user=<administrator>, method=PLAIN, rip=127.0.0.1, lip=127.0.0.1, mpid=28292, secured, session=<GDyX/yTeYwB/AAAB>
Jun  2 01:19:55 srv1 dovecot: imap(administrator): Disconnected: Logged out in=85 out=704
Jun  2 01:20:00 srv1 postfix/smtp[28281]: connect to alt1.gmail-smtp-in.l.google.com[173.194.78.27]:25: Connection timed out
Jun  2 01:20:30 srv1 postfix/smtp[28281]: connect to alt2.gmail-smtp-in.l.google.com[173.194.65.27]:25: Connection timed out
Jun  2 01:20:41 srv1 dovecot: imap-login: Login: user=<rann>, method=PLAIN, rip=127.0.0.1, lip=127.0.0.1, mpid=28294, secured, session=<1cNYAiXeZgB/AAAB>
Jun  2 01:20:41 srv1 dovecot: imap(rann): Disconnected: Logged out in=44 out=721
Jun  2 01:20:41 srv1 dovecot: imap-login: Login: user=<rann>, method=PLAIN, rip=127.0.0.1, lip=127.0.0.1, mpid=28296, secured, session=<dyRdAiXeZwB/AAAB>
Jun  2 01:20:41 srv1 dovecot: imap(rann): Disconnected: Logged out in=350 out=2345
Jun  2 01:20:41 srv1 dovecot: imap-login: Login: user=<rann>, method=PLAIN, rip=127.0.0.1, lip=127.0.0.1, mpid=28298, secured, session=<rnpfAiXeaAB/AAAB>
Jun  2 01:20:41 srv1 dovecot: imap(rann): Disconnected: Logged out in=227 out=1442
Jun  2 01:20:46 srv1 dovecot: imap-login: Login: user=<administrator>, method=PLAIN, rip=127.0.0.1, lip=127.0.0.1, mpid=28300, secured, session=<5l6rAiXeaQB/AAAB>
Jun  2 01:20:46 srv1 dovecot: imap(administrator): Disconnected: Logged out in=44 out=721
Jun  2 01:20:47 srv1 dovecot: imap-login: Login: user=<administrator>, method=PLAIN, rip=127.0.0.1, lip=127.0.0.1, mpid=28302, secured, session=<ePmvAiXeagB/AAAB>
Jun  2 01:20:47 srv1 dovecot: imap(administrator): Disconnected: Logged out in=350 out=2345
Jun  2 01:20:47 srv1 dovecot: imap-login: Login: user=<administrator>, method=PLAIN, rip=127.0.0.1, lip=127.0.0.1, mpid=28304, secured, session=<F1WyAiXeawB/AAAB>
Jun  2 01:20:47 srv1 dovecot: imap(administrator): Disconnected: Logged out in=227 out=1442
Jun  2 01:21:00 srv1 postfix/smtp[28281]: connect to alt3.gmail-smtp-in.l.google.com[173.194.70.27]:25: Connection timed out
Jun  2 01:21:30 srv1 postfix/smtp[28281]: connect to alt4.gmail-smtp-in.l.google.com[173.194.69.27]:25: Connection timed out
Jun  2 01:21:30 srv1 postfix/smtp[28281]: D051A240B6C: to=<[EMAIL="example@gmail.com"]example[/EMAIL][EMAIL="rannday5@gmail.com"]@gmail.com[/EMAIL]>, relay=none, delay=150, delays=0.01/0.02/150/0, dsn=4.4.1, status=deferred (connect to alt4.gmail-smtp-in.l.google.com[173.194.69.27]:25: Connection timed out)
Jun  2 01:23:02 srv1 postfix/qmgr[28242]: 25027240B6A: from=<[EMAIL="administrator@srv1.rannday.com"]administrator@srv1._[COLOR=#0066cc]example.com[/COLOR]_[/EMAIL]>, size=1184, nrcpt=1 (queue active)
Jun  2 01:23:32 srv1 postfix/smtp[28281]: connect to gmail-smtp-in.l.google.com[173.194.68.26]:25: Connection timed out
Jun  2 01:23:38 srv1 dovecot: imap-login: Login: user=<administrator>, method=PLAIN, rip=127.0.0.1, lip=127.0.0.1, mpid=28318, secured, session=<ED3iDCXebwB/AAAB>
Jun  2 01:23:38 srv1 dovecot: imap(administrator): Disconnected: Logged out in=292 out=1811
Jun  2 01:23:44 srv1 dovecot: imap-login: Login: user=<rann>, method=PLAIN, rip=127.0.0.1, lip=127.0.0.1, mpid=28320, secured, session=<CWFBDSXecAB/AAAB>
Jun  2 01:23:44 srv1 dovecot: imap(rann): Disconnected: Logged out in=44 out=721
Jun  2 01:23:44 srv1 dovecot: imap-login: Login: user=<rann>, method=PLAIN, rip=127.0.0.1, lip=127.0.0.1, mpid=28322, secured, session=<n8xFDSXecQB/AAAB>
Jun  2 01:23:44 srv1 dovecot: imap(rann): Disconnected: Logged out in=350 out=2345
Jun  2 01:23:44 srv1 dovecot: imap-login: Login: user=<rann>, method=PLAIN, rip=127.0.0.1, lip=127.0.0.1, mpid=28324, secured, session=<DC1IDSXecgB/AAAB>
Jun  2 01:23:44 srv1 dovecot: imap(rann): Disconnected: Logged out in=227 out=1442
Jun  2 01:24:02 srv1 postfix/smtp[28281]: connect to alt1.gmail-smtp-in.l.google.com[173.194.66.26]:25: Connection timed out
Jun  2 01:24:32 srv1 postfix/smtp[28281]: connect to alt2.gmail-smtp-in.l.google.com[173.194.65.26]:25: Connection timed out
Jun  2 01:25:02 srv1 postfix/smtp[28281]: connect to alt3.gmail-smtp-in.l.google.com[173.194.70.26]:25: Connection timed out
Jun  2 01:25:32 srv1 postfix/smtp[28281]: connect to alt4.gmail-smtp-in.l.google.com[173.194.69.26]:25: Connection timed out
Jun  2 01:25:32 srv1 postfix/smtp[28281]: 25027240B6A: to=<[EMAIL="example@gmail.com"]example[/EMAIL][EMAIL="rannday5@gmail.com"]@gmail.com[/EMAIL]>, relay=none, delay=566, delays=415/0.01/150/0, dsn=4.4.1, status=deferred (connect to alt4.gmail-smtp-in.l.google.com[173.194.69.26]:25: Connection timed out)
Jun  2 01:28:02 srv1 postfix/qmgr[28242]: D051A240B6C: from=<[EMAIL="administrator@srv1.rannday.com"]administrator@srv1._[COLOR=#0066cc]example.com[/COLOR]_[/EMAIL]>, size=1180, nrcpt=1 (queue active)
Jun  2 01:28:33 srv1 postfix/smtp[28356]: connect to gmail-smtp-in.l.google.com[173.194.68.26]:25: Connection timed out
Jun  2 01:29:03 srv1 postfix/smtp[28356]: connect to alt1.gmail-smtp-in.l.google.com[173.194.78.26]:25: Connection timed out
Jun  2 01:29:33 srv1 postfix/smtp[28356]: connect to alt2.gmail-smtp-in.l.google.com[173.194.65.27]:25: Connection timed out
Jun  2 01:30:03 srv1 postfix/smtp[28356]: connect to alt3.gmail-smtp-in.l.google.com[173.194.70.27]:25: Connection timed out
Jun  2 01:30:33 srv1 postfix/smtp[28356]: connect to alt4.gmail-smtp-in.l.google.com[173.194.69.27]:25: Connection timed out
Jun  2 01:30:33 srv1 postfix/smtp[28356]: D051A240B6C: to=<[EMAIL="example@gmail.com"]example[/EMAIL][EMAIL="rannday5@gmail.com"]@gmail.com[/EMAIL]>, relay=none, delay=693, delays=543/0.02/150/0, dsn=4.4.1, status=deferred (connect to alt4.gmail-smtp-in.l.google.com[173.194.69.27]:25: Connection timed out)
Jun  2 01:38:02 srv1 postfix/qmgr[28242]: 25027240B6A: from=<[EMAIL="administrator@srv1.rannday.com"]administrator@srv1._[COLOR=#0066cc]example.com[/COLOR]_[/EMAIL]>, size=1184, nrcpt=1 (queue active)
Jun  2 01:38:02 srv1 postfix/qmgr[28242]: 70D8F240B65: from=<[EMAIL="rann@srv1.rannday.com"]rann@srv1._[COLOR=#0066cc]example.com[/COLOR]_[/EMAIL]>, size=1164, nrcpt=1 (queue active)
Jun  2 01:38:32 srv1 postfix/smtp[28601]: connect to gmail-smtp-in.l.google.com[173.194.68.26]:25: Connection timed out
Jun  2 01:38:32 srv1 postfix/smtp[28602]: connect to gmail-smtp-in.l.google.com[173.194.68.26]:25: Connection timed out
Jun  2 01:39:02 srv1 postfix/smtp[28601]: connect to alt1.gmail-smtp-in.l.google.com[173.194.66.26]:25: Connection timed out
Jun  2 01:39:02 srv1 postfix/smtp[28602]: connect to alt1.gmail-smtp-in.l.google.com[173.194.67.26]:25: Connection timed out
Jun  2 01:39:32 srv1 postfix/smtp[28602]: connect to alt2.gmail-smtp-in.l.google.com[173.194.65.26]:25: Connection timed out
Jun  2 01:39:32 srv1 postfix/smtp[28601]: connect to alt2.gmail-smtp-in.l.google.com[173.194.65.26]:25: Connection timed out
Jun  2 01:40:02 srv1 postfix/smtp[28602]: connect to alt3.gmail-smtp-in.l.google.com[173.194.70.26]:25: Connection timed out
Jun  2 01:40:02 srv1 postfix/smtp[28601]: connect to alt3.gmail-smtp-in.l.google.com[173.194.70.26]:25: Connection timed out
Jun  2 01:40:32 srv1 postfix/smtp[28602]: connect to alt4.gmail-smtp-in.l.google.com[173.194.69.26]:25: Connection timed out
Jun  2 01:40:32 srv1 postfix/smtp[28601]: connect to alt4.gmail-smtp-in.l.google.com[173.194.69.26]:25: Connection timed out
Jun  2 01:40:33 srv1 postfix/smtp[28601]: 25027240B6A: to=<[EMAIL="rannday5@gmail.com"]rannday5@gmail.com[/EMAIL]>, relay=none, delay=1466, delays=1315/0.03/150/0, dsn=4.4.1, status=deferred (connect to alt4.gmail-smtp-in.l.google.com[173.194.69.26]:25: Connection timed out)
Jun  2 01:40:33 srv1 postfix/smtp[28602]: 70D8F240B65: to=<[EMAIL="rannday5@gmail.com"]rannday5@gmail.com[/EMAIL]>, relay=none, delay=4882, delays=4731/0.04/150/0, dsn=4.4.1, status=deferred (connect to alt4.gmail-smtp-in.l.google.com[173.194.69.26]:25: Connection timed out)
Jun  2 01:43:02 srv1 postfix/qmgr[28242]: D051A240B6C: from=<[EMAIL="administrator@srv1.rannday.com"]administrator@srv1._[COLOR=#0066cc]example.com[/COLOR]_[/EMAIL]>, size=1180, nrcpt=1 (queue active)
Jun  2 01:43:32 srv1 postfix/smtp[28621]: connect to gmail-smtp-in.l.google.com[173.194.68.26]:25: Connection timed out
Jun  2 01:44:02 srv1 postfix/smtp[28621]: connect to alt1.gmail-smtp-in.l.google.com[173.194.67.26]:25: Connection timed out
Jun  2 01:44:32 srv1 postfix/smtp[28621]: connect to alt2.gmail-smtp-in.l.google.com[173.194.65.26]:25: Connection timed out
Jun  2 01:45:02 srv1 postfix/smtp[28621]: connect to alt3.gmail-smtp-in.l.google.com[173.194.70.26]:25: Connection timed out
Jun  2 01:45:32 srv1 postfix/smtp[28621]: connect to alt4.gmail-smtp-in.l.google.com[173.194.69.26]:25: Connection timed out
Jun  2 01:45:32 srv1 postfix/smtp[28621]: D051A240B6C: to=<[EMAIL="rannday5@gmail.com"]rannday5@gmail.com[/EMAIL]>, relay=none, delay=1593, delays=1442/0.02/150/0, dsn=4.4.1, status=deferred (connect to alt4.gmail-smtp-in.l.google.com[173.194.69.26]:25: Connection timed out)
Jun  2 01:58:02 srv1 postfix/qmgr[28242]: 29A0324074F: from=<[EMAIL="administrator@srv1.rannday.com"]administrator@srv1._[COLOR=#0066cc]example.com[/COLOR]_[/EMAIL]>, size=725, nrcpt=1 (queue active)
Jun  2 01:58:32 srv1 postfix/smtp[28626]: connect to gmail-smtp-in.l.google.com[173.194.68.26]:25: Connection timed out
Jun  2 01:59:02 srv1 postfix/smtp[28626]: connect to alt1.gmail-smtp-in.l.google.com[173.194.78.26]:25: Connection timed out
Jun  2 01:59:32 srv1 postfix/smtp[28626]: connect to alt2.gmail-smtp-in.l.google.com[74.125.136.26]:25: Connection timed out
Jun  2 02:00:02 srv1 postfix/smtp[28626]: connect to alt3.gmail-smtp-in.l.google.com[173.194.70.26]:25: Connection timed out
Jun  2 02:00:32 srv1 postfix/smtp[28626]: connect to alt4.gmail-smtp-in.l.google.com[173.194.69.26]:25: Connection timed out
Jun  2 02:00:32 srv1 postfix/smtp[28626]: 29A0324074F: to=<[EMAIL="rannday5@gmail.com"]rannday5@gmail.com[/EMAIL]>, relay=none, delay=11429, delays=11279/0.02/150/0, dsn=4.4.1, status=deferred (connect to alt4.gmail-smtp-in.l.google.com[173.194.69.26]:25: Connection timed out)
 This was just the tail end of a very long log file. Please, I'll wash your feet and maybe even kiss them if you can help me.

---

### Post by weather15 on 2013-07-08
Looking at the logs that you posted, there are a number of occurrences where you see "Jun 2 01:24:02 srv1 postfix/smtp[28281]: connect to alt1.gmail-smtp-in.l.google.com[173.194.66.26]:25: Connection timed out". This means that your server is unable to connect the Google mail servers. This means that your server is still trying to connect to the Google Mail servers using port 25. According to your [other post]("http://ubuntuforums.org/showthread.php?t=2159096"), you said that your ISP blocks ports "25, 465, 587". These are the standard ports that mail exchange occurs on. I see you setup Gmail as an SMTP relay and saw that all your mail appeared to come from your Gmail account. This is something that happens when using Gmail accounts as SMTP relays. Since you were able to utilize Gmail as an SMTP relay, you are able to send mail out using port 587.

I understand that you would like to tell Postfix to use port 587 to send mail out instead of port 25. Unfortunately, it is not that simple. Port 587 is used for transferring mail over a TLS connection. Not all mail servers on the Internet will accept mail on port 587, but they all accept mail on port 25. In this case the best thing you can do, is to use a SMTP relay service. There are a number of different options you can use. I myself have worked with Dyn's Email Delivery Lite Plan, for $3 per month, you can send 10,000 emails. 

Now looking at the two threads it also seems that your ISP may block incoming traffic on ports "25, 465, 587". In this case, then you will not be able to receive mail from the outside, unless you use a service that delivers inbound mail to your server on alternative ports, that your ISP allows traffic on. Since your ISP is blocking these ports, they most likely do not want you to setup a mail server on their network anyway. You might want to look for a new ISP or consider having your mail hosted with Google Apps, or purchase a virtual private or dedicated server.

---

