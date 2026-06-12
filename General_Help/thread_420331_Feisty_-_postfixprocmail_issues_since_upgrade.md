---
title: "Feisty - postfix/procmail issues since upgrade"
date: 2007-04-23
forum: General Help
---

### Post by qaelith_2112 on 2007-04-23
I just upgraded a home server from Edgy to Feisty via apt-get.  I've had trouble with my e-mail since then.  I'm using fetchmail, postfix, procmail, and dovecot, with ssl for remote secure login.  I've configured it with a maildir ($HOME/Maildir/).

Since the upgrade, I suddenly was getting no mail.  I discovered that somehow my existing .procmailrc that was working in edgy was now delivering to / (filesystem root) instead of /username/Maildir.  I fooled with this for a while and managed to get it to deliver correctly, though it seems to be wanting to use /etc/procmailrc instead of /home/username/.procmailrc for direction.  Fine, but not what I really want.

The bigger problem is that since I've gotten mail delivering to the correct folder, it wants to set the owner to root and the group to mail, and with permissions of 700, I can't see the mail under my normal user ID.  No permission to view it.  I can chown it and get it fine, but then why should I have to chown everything as it comes in?  I believe the problem may be that it's running procmail as root rather than as me.  Before, the mail was delivering with my user ID as owner and group.  I've double-checked my config (of everything...) against the current recommendations in the Perfect Setup guide for Feisty, and I seem to have it configured as recommended.  I'm hoping someone has an idea what went wrong in the upgrade, and how I can fix it.  Here are my relevant config files:


procmailrc:
> SHELL=/bin/bash
LINEBUF=4096
LOGFILE=$HOME/.maillog
VERBOSE=Yes
FORMAIL=/usr/bin/formail

PATH=$HOME/bin:/usr/local/bin:/usr/bin:/bin
MAILDIR=$HOME/Maildir/
DEFAULT=$HOME/Maildir/
:0:
$HOME/Maildir/


postfix main.cf:
> # See /usr/share/postfix/main.cf.dist for a commented, more complete version


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

# TLS parameters
smtpd_tls_cert_file = /etc/postfix/ssl/smtpd.crt
smtpd_tls_key_file = /etc/postfix/ssl/smtpd.key
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = zeus.olympus
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = zeus.olympus, localhost.olympus, , localhost, comcast.net
relayhost = 
mynetworks = 127.0.0.0/8
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all
smtpd_sasl_local_domain = 
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtpd_tls_auth_only = no
smtp_use_tls = yes
smtp_tls_note_starttls_offer = yes
smtpd_tls_CAfile = /etc/postfix/ssl/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom


---

### Post by cnb2412 on 2007-06-10
Hi,

I've the same problem. Did you get a solution in the meantime?

---

### Post by qaelith_2112 on 2007-06-10
Unfortunately, no.  I've been doing a wholly unsatisfactory workaround until I have a chance to totally wipe the server and reinstall from CD in the hope that it'll work properly on clean install.  

My workaround has been to sudo chown -R myuserid /home/myuserid/Maildir/*  every time I want to deal with my mail.  Oddly, if there is even a single new mail that has arrived that ended up in my mailbox with "root" as the owner, I can't seem to get to anything through an IMAP client until everything is owned by me.

I tried setting a CRON job to do the chown every hour, but for whatever reason it doesn't fully work unless I manually login and do it.

I'll post back if a clean install ends up working, or if I figure out a solution without needing to do that.

---

### Post by qaelith_2112 on 2007-06-12
ADDENDUM:  Just found a solution in an unlikely place -- a FreeBSD forum.

If you're using Procmail as I would anticipate you are, add this to your /etc/procmailrc and/or your ~/.procmailrc:

DROPPRIVS=yes

That's all it took.  Now my mail is owned by the correct user and group instead of root:mail.

---

### Post by cnb2412 on 2007-06-14
Thank you for the tip! 

It works

---

