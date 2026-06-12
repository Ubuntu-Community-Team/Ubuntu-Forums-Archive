---
title: "postfix/smtpd[24862]: fatal: no SASL authentication mechanisms"
date: 2015-04-24
forum: General Help
---

### Post by astarmathsandphysics on 2015-04-24
For the fourth or fifth time I am trying to configure postfix with dovecot and I get the error 

postfix/smtpd[24862]: fatal: no SASL authentication mechanisms

I understand there are issues with dovecot-lmtp actually being lmtp and client-auth being auth in var/spool/postfix/private.
I I think I have fixed those but I still get these errors.

Here is output from postconf -n

alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
config_directory = /etc/postfix
html_directory = /usr/share/doc/postfix/html
inet_interfaces = all
inet_protocols = all
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
mydestination = localhost
myhostname = astarmathsandphysics.com
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
virtual_transport = lmtp:unix:private/lmtp

Here is the output from dovecot -n

# 2.2.9: /etc/dovecot/dovecot.conf
# OS: Linux 3.13.0-32-generic x86_64 Ubuntu 14.04.2 LTS ext4
auth_mechanisms = plain login
auth_verbose = yes
log_path = /var/log/dovecot.log
mail_debug = yes
mail_location = maildir:/var/mail/vhosts/%d/%n
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
protocols = lmtp imap pop3 sieve
service auth-worker {
  user = vmail
}
service auth {
  unix_listener /var/spool/postfix/private/auth {
    group = postfix
    mode = 0666
    user = postfix
  }
  unix_listener /var/spool/postfix/private/dovecot-auth {
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
}
ssl_cert = </etc/dovecot/dovecot.pem
ssl_cipher_list = ALL:!LOW:!SSLv2:ALL:!aNULL:!ADH:!eNULL:!EXP:RC4+RSA:+HIGH:+MEDIUM
ssl_key = </etc/dovecot/private/dovecot.pem
userdb {
  args = uid=vmail gid=vmail home=/var/mail/vhosts/%d/%n
  driver = static
}
doveconf: Error: protocols: Unknown protocol: sieve
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
}
doveconf: Fatal: Error in configuration file /etc/dovecot/dovecot.conf: protocols: Unknown protocol: sieve



PS dovecot-sieve is installed

---

