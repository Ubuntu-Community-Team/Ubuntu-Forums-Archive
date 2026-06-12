---
title: "Confgure imap Dovecot"
date: 2013-01-25
forum: General Help
---

### Post by teriyaki-89 on 2013-01-25
Hi everybody. I am stuck with configuring imap server with dovecot. I can login with plain text locally on server
**mutt -f  imap://domain1.com**  and read mail sent by postfix mta, but when i try to connect to imap server from mail client on my computer like thunderbird or outlook it can't. Can anyone help me what i've done wrong
i used [**this**]("https://help.ubuntu.com/community/PostfixVirtualMailBoxClamSmtpHowto")  for configuring dovecot
Below are my configs:

```

 /etc/dovecot/dovecot.conf
auth_mechanisms = plain cram-md5 login
auth_default_realm = domain1.com
auth_realms = domain1.com
auth_verbose = yes
auth default {
mechanisms = plain cram-md5
passdb passwd-file {
args = /etc/dovecot/passwd
}
userdb passwd-file {
args = /etc/dovecot/users
}
user = root
socket listen {
client {
# The client socket is generally safe to export to everyone. Typical use
# is to export it to your SMTP server so it can do SMTP AUTH lookups
# using it.
path = /var/spool/postfix/private/auth-client
mode = 0660
user = postfix
group = postfix
}
}
}
base_dir = /var/run/dovecot/
info_log_path = /var/log/dovecot.info
log_path = /var/log/dovecot
log_timestamp = "%Y-%m-%d %H:%M:%S "
mail_location = maildir:/home/vmail/%d/%n
passdb {
args = /etc/dovecot/passwd
driver = passwd-file
}
protocols = imap pop3
service auth {
executable = /usr/lib/dovecot/auth
user = root
}
service imap-login {
chroot = login
executable = /usr/lib/dovecot/imap-login
user = dovecot
}
service imap {
executable = /usr/lib/dovecot/imap
}
service pop3-login {
chroot = login
executable = /usr/lib/dovecot/pop3-login
user = dovecot
}
service pop3 {
executable = /usr/lib/dovecot/pop3
}
ssl = no
userdb {
args = /etc/dovecot/users
driver = passwd-file
}
valid_chroot_dirs = /var/spool/vmail
protocol pop3 {
pop3_uidl_format = %08Xu%08Xv
}

```
/etc/dovecot/users
```
nur@domain1.com::5000:5000::/home/vmail/domain1.com/nur/:/bin/false::
```

/etc/dovecot/passwd
```
nur@domain1.com:{CRAM-MD5}dd59f669267e9bb13d42a1ba57c972c5b13a4b2ae457c9ada8035dc7d8bae41b
```

---

