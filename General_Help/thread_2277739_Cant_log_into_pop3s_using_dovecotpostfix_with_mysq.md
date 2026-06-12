---
title: "Cant log into pop3s using dovecot/postfix with mysql"
date: 2015-05-11
forum: General Help
---

### Post by astarmathsandphysics on 2015-05-11
I am almost there setting up an email server but now I can't log in with an email client to read the email - I get connection refused message.using mutt and wring username or password or configuration not found using k9 on android or thunderbird.
Ports 995/25/465/587 are open - I have checked using extermal tool - and I can telnet into the mailserver
I can send and receive email - just cant login to retreive them.

Any ideas?

Found this in /var/log/syslog

May 11 10:02:23 server dovecot: pop3-login: Disconnected (auth failed, 1 attempts in 16 secs): user=<admin@astarmathsandphysics.com>, method=PLAIN, rip=81.106.96.92, lip=192.168.0.9, TLS: Disconnected, session=<3anhocoVjwBRamBc>

result of dovecot -n

# 2.2.9: /etc/dovecot/dovecot.conf
# OS: Linux 3.13.0-32-generic x86_64 Ubuntu 14.04.2 LTS ext4
auth_mechanisms = plain login
mail_location = maildir:/var/mail/vhosts/%d/%n
mail_privileged_group = mail
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
passdb {
  args = /etc/dovecot/dovecot-sql.conf.ext
  driver = sql
}
plugin {
  sieve = ~/.dovecot.sieve
  sieve_dir = ~/sieve
}
protocols = lmtp imap pop3
service auth-worker {
  user = vmail
}
service auth {
  unix_listener /var/spool/postfix/private/auth {
    group = postfix
    mode = 0660
    user = postfix
  }
  unix_listener auth-userdb {
    mode = 0600
    user = vmail
  }
  user = dovecot
}
service imap-login {
  inet_listener imap {
    port = 0
  }
}
service lmtp {
  unix_listener /var/spool/postfix/private/dovecot-lmtp {
    group = postfix
    mode = 0600
    user = postfix
  }
  unix_listener /var/spool/postfix/private/lmtp {
    group = postfix
    mode = 0600
    user = postfix
  }
}
service pop3-login {
  inet_listener pop3 {
    port = 0
  }
  inet_listener pop3s {
    port = 995
    ssl = yes
  }
}
ssl_cert = </etc/dovecot/dovecot.pem
ssl_cipher_list = ALL:!LOW:!SSLv2:ALL:!aNULL:!ADH:!eNULL:!EXP:RC4+RSA:+HIGH:+MEDIUM
ssl_key = </etc/dovecot/private/dovecot.pem
userdb {
  args = uid=vmail gid=vmail home=/var/mail/vhosts/%d/%n
  driver = static
}
protocol lda {
  deliver_log_format = msgid=%m: %$
  mail_plugins = sieve
  postmaster_address = postmaster
  quota_full_tempfail = yes
  rejection_reason = Your message to <%t> was automatically rejected:%n%r
}
protocol imap {
  imap_client_workarounds = delay-newmail
  mail_max_userip_connections = 10
}
protocol pop3 {
  mail_max_userip_connections = 10
  pop3_client_workarounds = outlook-no-nuls oe-ns-eoh


result of postconf -n

root@server:~# postconf -n
alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
config_directory = /etc/postfix
content_filter = scan:127.0.0.1:10026
html_directory = /usr/share/doc/postfix/html
inet_interfaces = all
inet_protocols = all
mailbox_command =
mailbox_size_limit = 51200000
mydestination = localhost
myhostname = server
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
myorigin = /etc/mailname
readme_directory = /usr/share/doc/postfix
recipient_delimiter = +
relayhost =
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_recipient_restrictions = permit_sasl_authenticated, permit_mynetworks, reject_unauth_destination
smtpd_relay_restrictions = permit_mynetworks permit_sasl_authenticated defer_unauth_destination
smtpd_sasl_auth_enable = yes
smtpd_sasl_path = private/auth
smtpd_sasl_type = dovecot
smtpd_tls_auth_only = yes
smtpd_tls_cert_file = /etc/dovecot/dovecot.pem
smtpd_tls_key_file = /etc/dovecot/private/dovecot.pem
smtpd_use_tls = yes
virtual_alias_maps = mysql:/etc/postfix/mysql-virtual-alias-maps.cf
virtual_mailbox_domains = mysql:/etc/postfix/mysql-virtual-mailbox-domains.cf
virtual_mailbox_maps = mysql:/etc/postfix/mysql-virtual-mailbox-maps.cf
virtual_transport = lmtp:unix:private/dovecot-lmtp
root@server:~#

I DID IT

I can only say that I stayed up late and got up early trying every possible option until it worked

---

