---
title: "SASL LOGIN authentication failed: no mechanism available"
date: 2013-08-19
forum: General Help
---

### Post by brian12 on 2013-08-19
Marked as SOLVED. See reply.

Hello folks,

I'm trying to set up an email server for my organization and I am having some issues. I used the guide here: [https://library.linode.com/email/postfix/dovecot-mysql-debian-6-squeeze](https://library.linode.com/email/postfix/dovecot-mysql-debian-6-squeeze) which I realize is a little dated. I'm not real new to linux, but not exactly seasoned either. This is a little more invovled than what I do on my machine at home.

I can log into squirrelmail and send/receive email with no issues.

When I setup Thunderbird it autoconfigures to use STARTTLS. It will configure the account and retreive the email through imap correctly with no issues. However, when I try to send an email it says that it cannot connect to the SMTP server and fails to send mail out.

my mail.log file shows:

> 
servername dovecot: imap-login: Login: user=<someuser@website.com>, method=PLAIN, rip=xxx.xxx.xxx.xxx, lip=xxx.xxx.xxx.xxx, mpid=13569, TLS, session=<psSBfU7kLgC4srLV>
servername dovecot: imap(demo@website.com): Disconnected: Logged out in=8 out=340
servername dovecot: imap-login: Login: user=<someuser@websitel.com>, method=PLAIN, rip=xxx.xxx.xxx.xxx, lip=xxx.xxx.xxx.xxx, mpid=13571, TLS, session=<UdsRfk7kLwC4srLV>
servername postfix/smtpd[13553]: connect from wsip-xxx.xxx.xxx.xxx.ok.ok.cox.net[xxx.xxx.xxx.xxx]
servername postfix/smtpd[13553]: warning: wsip-xxx.xxx.xxx.xxx.ok.ok.cox.net[xxx.xxx.xxx.xxx]: SASL PLAIN authentication failed: no mechanism available
servername postfix/smtpd[13553]: warning: wsip-xxx.xxx.xxx.xxx.ok.ok.cox.net[xxx.xxx.xxx.xxx]: SASL LOGIN authentication failed: no mechanism available


/etc/postfix/main.cf
> 
smtpd_banner = $myhostname ESMTP $mail_name (Debian/GNU)
biff = no
append_dot_mydomain = no
readme_directory = /usr/share/doc/postfix
smtpd_tls_cert_file = /etc/postfix/smtpd.cert
smtpd_tls_key_file = /etc/postfix/smtpd.key
smtp_tls_security_level = may
smtpd_tls_security_level = may
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom
myhostname = website.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = website.com
mydestination = localhost, localhost.localdomain
mynetworks = 172.17.2.0/24 192.168.1.0/24 127.0.0.0/8 xxx.xxx.xxx.xxx
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
relay_domains = $mydestination
html_directory = /usr/share/doc/postfix/html
message_size_limit = 30720000
virtual_alias_domains = 
virtual_alias_maps = proxy:mysql:/etc/postfix/mysql-virtual_forwardings.cf, mysql:/etc/postfix/mysql-virtual_email2email.cf
virtual_mailbox_domains = proxy:mysql:/etc/postfix/mysql-virtual_domains.cf
virtual_mailbox_maps = proxy:mysql:/etc/postfix/mysql-virtual_mailboxes.cf
virtual_mailbox_base = /home/vmail
virtual_uid_maps = static:5000
virtual_gid_maps = static:5000
smtpd_sasl_auth_enable = yes
broken_sasl_auth_clients = yes
smtpd_sasl_authenticated_header = yes
smtpd_recipient_restrictions = permit_mynetworks, permit_sasl_authenticated, reject_unauth_destination
proxy_read_maps = $local_recipient_maps $mydestination $virtual_alias_maps $virtual_alias_domains $virtual_mailbox_maps $virtual_mailbox_domains $relay_recipient_maps $relay_domains $canonical_maps $sender_canonical_maps $recipient_canonical_maps $relocated_maps $transport_maps $mynetworks $virtual_mailbox_limit_maps
virtual_transport = dovecot
dovecot_destination_recipient_limit = 1


/etc/postfix/master.cf
> 
# ==========================================================================
# service type  private unpriv  chroot  wakeup  maxproc command + args
#               (yes)   (yes)   (yes)   (never) (100)
# ==========================================================================
smtp      inet  n       -       -       -       -       smtpd
#smtp      inet  n       -       -       -       1       postscreen
#smtpd     pass  -       -       -       -       -       smtpd
#dnsblog   unix  -       -       -       -       0       dnsblog
#tlsproxy  unix  -       -       -       -       0       tlsproxy
#submission inet n       -       -       -       -       smtpd
#  -o syslog_name=postfix/submission
  -o smtpd_tls_security_level=may
#  -o smtpd_sasl_auth_enable=yes
#  -o smtpd_client_restrictions=permit_sasl_authenticated,reject
#  -o milter_macro_daemon_name=ORIGINATING
#smtps     inet  n       -       -       -       -       smtpd
#  -o syslog_name=postfix/smtps
#  -o smtpd_tls_wrappermode=yes
#  -o smtpd_sasl_auth_enable=yes
#  -o smtpd_client_restrictions=permit_sasl_authenticated,reject
#  -o milter_macro_daemon_name=ORIGINATING
#628       inet  n       -       -       -       -       qmqpd
pickup    fifo  n       -       -       60      1       pickup
cleanup   unix  n       -       -       -       0       cleanup
qmgr      fifo  n       -       n       300     1       qmgr
#qmgr     fifo  n       -       n       300     1       oqmgr
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
scalemail-backend unix    -    n    n    -    2    pipe
  flags=R user=scalemail argv=/usr/lib/scalemail/bin/scalemail-store ${nexthop} ${user} ${extension}
mailman   unix  -       n       n       -       -       pipe
  flags=FR user=list argv=/usr/lib/mailman/bin/postfix-to-mailman.py
  ${nexthop} ${user}
dovecot   unix  -       n       n       -       -       pipe
    flags=DRhu user=vmail:vmail argv=/usr/lib/dovecot/deliver -d ${recipient}


/etc/postfix/sasl/smtpd.conf
> 
pwcheck_method: saslauthd
mech_list: plain login
allow_plaintext: true
auxprop_plugin: mysql
sql_hostnames: 127.0.0.1
sql_user: username
sql_passwd: password
sql_database: mail
sql_select: select password from users where email = '%u'


/etc/dovecot/dovecot.conf
> 
log_timestamp = "%Y-%m-%d %H:%M:%S "
mail_location = maildir:/home/vmail/%d/%n/Maildir
namespace {
  inbox = yes
  location =
  prefix = INBOX.
  separator = .
  type = private
}
passdb {
  args = /etc/dovecot/dovecot-sql.conf
  driver = sql
}
plugin {
  sieve_global_path = /home/vmail/globalsieverc
  mail_plugins = $mail_plugins virtual
}
protocols = imap pop3
service auth {
  unix_listener /var/spool/postfix/private/auth {
    group = postfix
    mode = 0660
    user = postfix
  }
  unix_listener auth-master {
    mode = 0600
    user = vmail
  }
  user = username
}
ssl_cert = </etc/ssl/certs/dovecot.pem
ssl_key = </etc/ssl/private/dovecot.pem
userdb {
  args = uid=5000 gid=5000 home=/home/vmail/%d/%n allow_all_users=yes
  driver = static
}
protocol lda {
  auth_socket_path = /var/run/dovecot/auth-master
  log_path = /home/vmail/dovecot-deliver.log
  mail_plugins = sieve
  postmaster_address = [EMAIL="postmaster@website.com"]postmaster@website.com[/EMAIL]
}
protocol pop3 {
  pop3_uidl_format = %08Xu%08Xv
}


/etc/default/saslauthd
> 
START=yes
DESC="SASL Authentication Daemon"
NAME="saslauthd"
MECHANISMS="pam"
MECH_OPTIONS=""
THREADS=5
OPTIONS="-c -m /var/spool/postfix/var/run/saslauthd -r"


Any help would be appreciated. Thanks.

---

### Post by brian12 on 2013-08-19
SOLVED.

Adding these lines to main.cf fixed the issue:
smtpd_sasl_type = dovecot
smtpd_sasl_path = private/auth

---

