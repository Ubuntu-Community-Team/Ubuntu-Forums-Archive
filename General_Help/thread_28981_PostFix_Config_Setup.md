---
title: "PostFix Config Setup"
date: 2005-04-22
forum: General Help
---

### Post by capi on 2005-04-22
I've been messing with mail servers all day. Since Ubuntu came with Postfix I thought I'd try that one. It's a fresh server install and the Sendmail config looks like...

/etc/postfix/main.cf:
```

# See /usr/share/postfix/main.cf.dist for a commented, more complete version

smtpd_banner = $myhostname ESMTP $mail_name (Debian/GNU)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

myhostname = localhost.localdomain
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = localhost.localdomain, localhost.localdomain, localhost
relayhost =
mynetworks = 127.0.0.0/8
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = loopback-only

``` 

I don't have a domain name for this computer, unless you count the ones from no-ip.com, so can I just use IP an IP address? Where do I plug the values in, just over localhost.localdomain?

What exactly does PostFix do, from some of the tutorials it sounded like I needed some other programs as well to get a simple mail server. I'm trying to set this up so that I can simply send and recieve mail, as simple as I can make it. I'm also setting up apache/mysql/php after this and I'd like to be able to use phps mail function.

A final note I'm behind a router, I'll need to open a port to send mail most likely, but will I need to opena port to recieve e-mail?

Helps greatly appreciated.

---

### Post by capi on 2005-04-23
[QUOTE=capi]I've been messing with mail servers all day. Since Ubuntu came with Postfix I thought I'd try that one. It's a fresh server install and the Sendmail config looks like...

/etc/postfix/main.cf:
```

# See /usr/share/postfix/main.cf.dist for a commented, more complete version

smtpd_banner = $myhostname ESMTP $mail_name (Debian/GNU)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

myhostname = localhost.localdomain
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = localhost.localdomain, localhost.localdomain, localhost
relayhost =
mynetworks = 127.0.0.0/8
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = loopback-only

``` 

I don't have a domain name for this computer, unless you count the ones from no-ip.com, so can I just use IP an IP address? Where do I plug the values in, just over localhost.localdomain?

What exactly does PostFix do, from some of the tutorials it sounded like I needed some other programs as well to get a simple mail server. I'm trying to set this up so that I can simply send and recieve mail, as simple as I can make it. I'm also setting up apache/mysql/php after this and I'd like to be able to use phps mail function.

A final note I'm behind a router, I'll need to open a port to send mail most likely, but will I need to opena port to recieve e-mail?

Helps greatly appreciated.[/QUOTE]
 No one? I know can get all my config details, but I'm not even sure what I need. I'm simply trying to get mail to be sent beyond localhost, I'm behind a router and I'm not sure what I need to do.

---

### Post by DJ_Max on 2005-04-23
Postfix is a mail transfer agent, using to send mail over the internet, most people won't need it unless they have a FQDN (Domain name). Otherwise, to my knowledge, most mail servers won't accept your mail.

Look at webmin for setting up Postfix.

---

