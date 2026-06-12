---
title: "PostFix and DoveCot: No SASL Authentication Mechanisms"
date: 2013-01-06
forum: General Help
---

### Post by Clucky on 2013-01-06
After following the guide provided by debuntu.org ([http://www.debuntu.org/how-to-virtual-emails-accounts-with-postfix-and-dovecot/](http://www.debuntu.org/how-to-virtual-emails-accounts-with-postfix-and-dovecot/)) which was very helpful, I immediately began having issues with SASL autentication. What provoked me to look in the mail.log to see the following message was an error message on thunderbird that stated "Thunderbird failed to find the settings for your email account." The error that repeats in **mail.log** is as follows:
 ```
Jan  6 14:16:45 Jesse-Server postfix/smtpd[22109]: connect from unknown[192.168.2.1]
Jan  6 14:16:45 Jesse-Server postfix/smtpd[22109]: warning: SASL: Connect to private/auth failed: No such file or directory
Jan  6 14:16:45 Jesse-Server postfix/smtpd[22109]: fatal: no SASL authentication mechanisms
Jan  6 14:16:46 Jesse-Server postfix/master[8209]: warning: process /usr/lib/postfix/smtpd pid 22109 exit status 1
Jan  6 14:16:46 Jesse-Server postfix/master[8209]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling
Jan  6 14:17:46 Jesse-Server postfix/smtpd[22134]: connect from localhost[127.0.0.1]
Jan  6 14:17:46 Jesse-Server postfix/smtpd[22134]: warning: SASL: Connect to private/auth failed: No such file or directory
Jan  6 14:17:46 Jesse-Server postfix/smtpd[22134]: fatal: no SASL authentication mechanisms
Jan  6 14:17:47 Jesse-Server postfix/master[8209]: warning: process /usr/lib/postfix/smtpd pid 22134 exit status 1
Jan  6 14:17:47 Jesse-Server postfix/master[8209]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling
Jan  6 14:18:26 Jesse-Server postfix/anvil[22112]: statistics: max connection rate 1/60s for (smtp:192.168.2.1) at Jan  6 14:16:45
Jan  6 14:18:26 Jesse-Server postfix/anvil[22112]: statistics: max connection count 1 for (smtp:192.168.2.1) at Jan  6 14:16:45
Jan  6 14:18:26 Jesse-Server postfix/anvil[22112]: statistics: max cache size 1 at Jan  6 14:16:45

```This provoked me to look for private/auth, but as you can see below, no such file exists...
```
root@Jesse-Server:/home/clucky# ls -l /var/spool/postfix/private/auth
ls: cannot access /var/spool/postfix/private/auth: No such file or directory

```What I would like to know is where is my private/auth folder? Am I using the wrong version of dovecot perhaps? In an unrelated note, when I type service dovecot restart it says the following: 
```

stop: Unknown instance: 
dovecot start/running, process 9394

```Here is the configuration for postfix labled **main.cf**:
```

smtpd_banner = $myhostname ESMTP $mail_name (Debian/GNU)
biff = no
# appending .domain is the MUA's job.
append_dot_mydomain = no
# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h
# TLS parameters
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache
#vhost with mysql params
#virtual_alias_domains needs to be unset
virtual_alias_domains =
virtual_mailbox_domains = mysql:/etc/postfix/virtual/mysql-virtual-mailbox-domains.cf
virtual_mailbox_maps = mysql:/etc/postfix/virtual/mysql-virtual-mailbox-maps.cf
virtual_alias_maps = mysql:/etc/postfix/virtual/mysql-virtual-alias-maps.cf, mysql:/etc/postfix/virtual/mysql-virtual-email2email.cf
virtual_uid_maps = static:5000
virtual_gid_maps = static:5000
virtual_transport = dovecot
dovecot_destination_recipient_limit = 1
myhostname = worldofclucky.net
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = worldofclucky.net, localhost
relayhost =
mynetworks = 127.0.0.0/8
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
smtpd_sasl_type = dovecot
smtpd_sasl_path = private/auth
smtpd_sasl_auth_enable = yes
smtpd_recipient_restrictions = permit_mynetworks,permit_sasl_authenticated,reject_unauth_destination

```and here is **dovecot.conf**:
```

protocols = imaps
mail_location = maildir:/var/vmail/%d/%n/Maildir
## uncomment this if you already have email from
## courier for instance.
#namespace private {
#  separator = .
#  prefix = INBOX.
#  inbox = yes
#}
## change section "protocol lda" to:
protocol lda {
  # Address to use when sending rejection mails.
  postmaster_address = postmaster@worldofclucky.net
  log_path = /var/vmail/dovecot-deliver.log
  # Hostname to use in various parts of sent mails, eg. in Message-Id.
  # Default is the system's real hostname.
  #hostname =
  # Support for dynamically loadable plugins. mail_plugins is a space separated
  # list of plugins to load.
  #mail_plugins =
  #mail_plugin_dir = /usr/lib/dovecot/modules/lda
  # Binary to use for sending mails.
  #sendmail_path = /usr/lib/sendmail
  # UNIX socket path to master authentication server to find users.
  auth_socket_path = /var/run/dovecot/auth-master
  # Enabling Sieve plugin for server-side mail filtering
  # handy for storing spam in their folders
  mail_plugins = cmusieve
  global_script_path = /var/vmail/globalsieverc
}
## in section auth default
## change :
mechanisms = plain login
## comment out "passdb pam"
## and make sure the following is in
## to look for users in the DB
  passdb sql {
    # Path for SQL configuration file, see /etc/dovecot/dovecot-sql.conf for example
    args = /etc/dovecot/dovecot-sql.conf
  }
## and add this so dovecot does not deal with uid/gid
## we use uid and gid 5000 for everybody
  userdb static {
    args = uid=5000 gid=5000 home=/home/vmail/%d/%n allow_all_users=yes
  }
## next make sure the section "socket listen" looks like this
## so dovecot and postfix work happily together
  socket listen {
     master {
       path = /var/run/dovecot/auth-master
       mode = 0600
       user = vmail # User running Dovecot LDA
       #group = mail # Or alternatively mode 0660 + LDA user in this group
     }
     client {
      # The client socket is generally safe to export to everyone. Typical use
      # is to export it to your SMTP server so it can do SMTP AUTH lookups
      # using it.
      path = /var/spool/postfix/private/auth
      #path = /var/run/dovecot/auth-client
      mode = 0660
      user = postfix
      group = postfix
     }
   }

```Any help would be greatly appreciated, and if you need any more errors/configs, do not hesitate to ask. Thank you in advanced!

---

### Post by Clucky on 2013-01-08
Nobody has any thoughts?

---

