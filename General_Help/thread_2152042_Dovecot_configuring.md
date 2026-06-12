---
title: "Dovecot configuring"
date: 2013-06-06
forum: General Help
---

### Post by JKyleOKC on 2013-06-06
I'm getting lots of errors in /var/log/syslog, all similar to this example:```
Jun  6 11:44:44 mehitabel postfix/qmgr[1761]: 0A50C100034: from=<root@jimkyle.dns2go.com>, size=594, nrcpt=1 (queue active)
Jun  6 11:44:44 mehitabel dovecot: lda(root): Error: chdir(/root/) failed: Permission denied (euid=65534(nobody) egid=65534(nogroup) missing +x perm: /root, dir owned by 0:0 mode=0700)
Jun  6 11:44:44 mehitabel dovecot: lda(root): Error: chdir(/root) failed: Permission denied
Jun  6 11:44:44 mehitabel dovecot: lda(root): Error: user root: Initialization failed: Initializing mail storage from mail_location setting failed: stat(/root/Maildir) failed: Permission denied (euid=65534(nobody) egid=65534(nogroup) missing +x perm: /root, dir owned by 0:0 mode=0700)
Jun  6 11:44:44 mehitabel dovecot: lda(root): Fatal: Invalid user settings. Refer to server log for more information.
Jun  6 11:44:44 mehitabel postfix/local[4158]: 0A50C100034: to=<root@jimkyle.dns2go.com>, orig_to=<root>, relay=local, delay=99537, delays=99537/0.01/0/0.08, dsn=4.3.0, status=deferred (temporary failure)

```It seems obvious that something is wrong in my configuration file, which so far is strictly the default that came with installation of the dovecot-postfix package:```
# 2.0.19: /etc/dovecot/dovecot.conf
# OS: Linux 3.2.0-45-generic i686 Ubuntu 12.04.2 LTS 
mail_location = maildir:~/Maildir
managesieve_notify_capability = mailto
managesieve_sieve_capability = fileinto reject envelope encoded-character vacation subaddress comparator-i;ascii-numeric relational regex imap4flags copy include variables body enotify environment mailbox date ihave
passdb {
  driver = pam
}
plugin {
  sieve = ~/.dovecot.sieve
  sieve_dir = ~/sieve
}
protocols = imap pop3 sieve
service auth {
  unix_listener /var/spool/postfix/private/dovecot-auth {
    group = postfix
    mode = 0660
    user = postfix
  }
}
ssl_cert = </etc/ssl/certs/dovecot.pem
ssl_cipher_list = ALL:!LOW:!SSLv2:ALL:!aNULL:!ADH:!eNULL:!EXP:RC4+RSA:+HIGH:+MEDIUM
ssl_key = </etc/ssl/private/dovecot.pem
userdb {
  driver = passwd
}
protocol imap {
  imap_client_workarounds = delay-newmail
  mail_max_userip_connections = 10
}
protocol pop3 {
  mail_max_userip_connections = 10
  pop3_client_workarounds = outlook-no-nuls oe-ns-eoh
}
protocol lda {
  deliver_log_format = msgid=%m: %$
  mail_plugins = sieve
  postmaster_address = postmaster
  quota_full_tempfail = yes
  rejection_reason = Your message to <%t> was automatically rejected:%n%r
}

```It's possible that I need to modify permissions on /root/Maildir, or make some similar change, but I definitely don't want to punch holes in my system security. The messages are all sent from "logwatch" via "cron" entries; perhaps I should simply change their recipient user from "root" to "jk" but that may be a bit flaky also. Since only local traffic is involved here, what would be the effect of removing "sieve" from the protocols; the only thing I need is pop3?

The dovecot documentation is so incredibly detailed that it's almost useless for a newcomer to the program; can someone point me in the correct direction to eliminate these errors, please!

---

### Post by JKyleOKC on 2013-06-08
bump

---

### Post by SeijiSensei on 2013-06-08
How many mailboxes are you intending to have on this machine?  Is it critical that you use Maildir, or can you use mbox for the mail folders instead?  On a machine with mbox folders, root's mail is usually delivered to /var/mail/root rather than a file or folder in root's home directory.  

Are you sure that both /root and /root/Maildir have 700 permissions?

---

### Post by JKyleOKC on 2013-06-08
They do now, but /root/Maildir did not exist until I just now created it and set its permissions.

I actually need only one mailbox, for "jk" which is the only user other than the various system users. I'm not at all sure why Dovecot is trying to deliver a message to "root" in the first place. The only messages handled are those from various cron jobs, so perhaps I simply need to be certain that all of them get addressed to "jk" or perhaps set postfix aliases for "root" and "postmaster" to translate to "jk" instead of to root...

Thanks for the response; it has definitely triggered more thoughts!

---

### Post by JKyleOKC on 2013-06-09
Thanks again! This morning I changed dovecot.conf, setting the mail location to mbox instead of maildir, and the errors all went away.

For the benefit of anyone who comes across this thread in future, I used "doveconf -n >newconf" to create a copy of the current configuration in my home directory, went to dovecot's "wiki2" pages and followed the "configuration" link, copied the mail_location (for mbox) and mail_privileged_group lines from there, pasted them into "newconf" to replace the existing line, renamed the existing "/etc/dovecot/dovecot.conf" file to be "/etc/dovecot/dovecot.conf.original", copied "newconf" to "/etc/dovecot/dovecot.conf", then used "sudo dovecot reload" to update the actual configuration.

To test it, I triggered an access from my remote mail client and checked /var/log/syslog -- no errors this time!

---

### Post by JKyleOKC on 2013-06-10
I spoke too soon about a solution!

This morning, no mail at all came through -- and syslog still had the "lda(root)" errors from dovecot.

Restored the original /etc/dovecot/dovecot.conf file from the backup, and the messages came through as always. Obviously some part of my changes caused a fatal problem.

I'm still stumped.

---

### Post by dan-j on 2013-08-13
I'm having the same or similar problem.

Clean install of Dovecot, Postfix, dovecot-postfix.

Postfix is queueing the mail, but won't deliver with the following error:
```
Aug 12 20:49:53 server dovecot: lda(dan): Fatal: Invalid user settings. Refer to server log for more information.
Aug 12 20:49:53 server dovecot: lda(dan): Error: user dank: Initialization failed: mail_location not set and autodetection failed: Mail storage autodetection failed with home=/home/dan
```

What's weird is, mail_location is indeed set:
```
# dovecot -a | grep mail_location
mail_location = maildir:~/Maildir

```
Also, ~/Maildir doesn't exist in any of my local users' homedirs.

My main.cf is:
```

# See /usr/share/postfix/main.cf.dist for a commented, more complete version




# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
#myorigin = /etc/mailname


smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no


# appending .domain is the MUA's job.
append_dot_mydomain = no


# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h


readme_directory = no


# TLS parameters
smtpd_tls_cert_file = /etc/ssl/certs/ssl-mail.pem
smtpd_tls_key_file = /etc/ssl/private/ssl-mail.key
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache


# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.


myhostname = mail.foobar.net
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = foobar.net
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 0
recipient_delimiter = +
home_mailbox = Maildir/
smtpd_sasl_auth_enable = yes
smtpd_sasl_type = dovecot
smtpd_sasl_path = private/dovecot-auth
smtpd_sasl_authenticated_header = yes
smtpd_sasl_security_options = noanonymous
smtpd_sasl_local_domain = $myhostname
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = reject_unknown_sender_domain, reject_unknown_recipient_domain, reject_unauth_pipelining, permit_mynetworks, permit_sasl_authenticated, reject_unauth_destination
smtpd_sender_restrictions = reject_unknown_sender_domain
mailbox_command = /usr/lib/dovecot/deliver -c /etc/dovecot/conf.d/01-mail-stack-delivery.conf -m "${EXTENSION}"
smtp_use_tls = yes
smtpd_tls_received_header = yes
smtpd_tls_mandatory_protocols = SSLv3, TLSv1
smtpd_tls_mandatory_ciphers = medium
smtpd_tls_auth_only = yes
tls_random_source = dev:/dev/urandom
inet_protocols = all

```

---

### Post by JKyleOKC on 2013-08-13
I believe that you need to manually create the Maildir directories for each user, just as you have to create mountpoints before using them.

---

### Post by dan-j on 2013-08-13
> **JKyleOKC said:**
> I believe that you need to manually create the Maildir directories for each user, just as you have to create mountpoints before using them.


So, I created the dirs **~/Maildir/[new,cur,tmp]** and mail spooled... So, for me it's working, but I don't know why.

Why didn't Maildir get created?  Why is the Dovecot error misleading?

Oh well, just one for the Google Searches. :-)

---

