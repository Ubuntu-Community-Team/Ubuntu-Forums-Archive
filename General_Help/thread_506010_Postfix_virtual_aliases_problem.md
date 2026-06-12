---
title: "Postfix virtual aliases problem"
date: 2007-07-21
forum: General Help
---

### Post by orotrev on 2007-07-21
I get the following error when sending mail to a user.

```

postfix/error[3220]: 208261BDBE: to=<*****@goiv.com>, relay=none, delay=0.22, delays=0.21/0.01/0/0.01, dsn=5.0.0, status=bounced (User unknown in virtual alias table)

```

here is my main.cf file

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

# TLS parameters
smtpd_tls_cert_file = /etc/postfix/ssl/smtpd.crt
smtpd_tls_key_file = /etc/postfix/ssl/smtpd.key
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = mail.goiv.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = localhost, localhost.localdomain, localhost
relayhost = 
mynetworks = 127.0.0.0/8
mailbox_command = 
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all
smtpd_sasl_local_domain = 
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_sasl_authenticated, permit_mynetworks, reject_unauth_destination
smtpd_tls_auth_only = no
smtp_use_tls = yes
smtp_tls_note_starttls_offer = yes
smtpd_tls_CAfile = /etc/postfix/ssl/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom
home_mailbox = Maildir/
virtual_alias_domains = goiv.com, gointernetvideo.com
virtual_alias_maps = hash:/etc/postfix/virtual
#virtual_mailbox_domain = goiv.com, gointernetvideo.com
#virtual_mailbox_maps = hash:/etc/postix/virtual

```

I have created a virtual file and used postmap on it here it is:
```

test@goiv.com   **username omitted**
******@goiv.com      **username omitted**

```

what am I missing? I want to use a simple setup that maps virtual aliases to users that have system accounts. Nothing fancy no MySQL DBs or anything. I am very new to postfix and courier. I followed the tutorial found here: [https://help.ubuntu.com/community/Postfix]("https://help.ubuntu.com/community/Postfix")
and
[https://help.ubuntu.com/community/PostfixBasicSetupHowto]("https://help.ubuntu.com/community/PostfixBasicSetupHowto")

---

### Post by orotrev on 2007-07-21
I think I fixed that error, I commented out the myorigin = /etc/mailname. Now I get the "mail for **** loops back to myself" error. Doing a bit of reading has led me to believe that it is a hostname, dns problem, but I can't find the problem.

---

### Post by orotrev on 2007-07-21
Nope, thats not it. Still having the same problem.

---

### Post by orotrev on 2007-07-22
Bump

---

### Post by Mr. C. on 2007-07-23
Show postconf -n output, not your main.cf.

What is in your /etc/mailname file ?

What do you get with:

```
dig goiv.com
dig mail.goiv.com
```
MrC

---

### Post by LK7R on 2007-07-23
It has to do something with DNS. If you change the mailname to localhost it will work.

Had the same problem just now and localhost in mailname solved it. Still going to investigate the correct solution - correct name in mailname smtp answer.

Hope it helps.

---

### Post by LK7R on 2007-07-23
ok so what i found next:

if you have in your mail name   example.com and this is adress you want to have virtual, then you have to have different name in mailname which is localy deliveryable. That means:

[I]/etc/postfix/main.cf
 mydestination = localhost, localhost.localdomain, mx.testing.org

{ other configurations }

virtual_alias_domains = example.com, example1.com, exampleN.com
virtual_alias_maps = hash:/etc/postfix/virtual
 [/I]

and in your mailname:

[I]
/etc/mailname
 mx.testing.org
[/I]

then it should work as it should.

Dan

---

### Post by Mr. C. on 2007-07-23
This wasn't a DNS issue; it was a problem with placing your domain in both virtual alias domains and using non-fully qualified email addresses in your virtual alias maps.  Postfix adds on the domain name (mydomain), so that creates a mail look when your mailname parameter is the same as mydomain.

You could change your virtual aliases to send to **name@localhost** instead of just **name**.

You cannot have a domain listed in more than one address class at a time (eg. local, virtual alias, virtual mailbox).

MrC

---

### Post by LK7R on 2007-07-23
Thanks for the correction - that make sense!

---

