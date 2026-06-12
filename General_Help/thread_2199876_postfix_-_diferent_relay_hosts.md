---
title: "postfix - diferent relay hosts"
date: 2014-01-16
forum: General Help
---

### Post by sebastiaopburnay on 2014-01-16
Hi!

I'm a noob in terms of postfix configurations, and I'm having a problem that might be simple to solve to you.

Architecture: 64 Bits Ubuntu Server 12.04 LTS, hosting a Postfix 2.9.6.

I would like my Ubuntu server to chose different relay host depending on the destination address of SMTP messages sent.

I'll explain, we have a stupid SMTP relay machine which only sends **_ALL_** SMTP messages to the cloud office365 mail server, that SMTP relay will not relay messages to our SMS gateway based on @sms.MyDomain in the destination of those messages. He will ALLWAYS send received SMTP to the cloud server.

In my /etc/postfix/main.cf, I only have that SMS relay host's IP address, so, all SMTP messages that should go to our SMS gateay never get delivered.

I show bellow the drawing of what I want 
[ATTACH=CONFIG]249531[/ATTACH]

I also put the content of main.cf (with IP addresses and domain names replaced with <propper descriptions>.
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
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = <MyMailDomain (string after the '@') in 'MAIL FROM:'>
alias_maps = hash:/etc/aliases
smtp_generic_maps = hash:/etc/postfix/generic
sender_canonical_maps = hash:/etc/postfix/generic 
alias_database = hash:/etc/aliases
#myorigin = /etc/mailname
mydestination = MyServer.MyDomain, localhost.MyDomain, localhost
relayhost = <SMTP Relay's IP address>
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 0
recipient_delimiter = +
#inet_interfaces = loopback-only
inet_interfaces = all
default_transport = smtp
relay_transport = smtp
#default_transport = error
#relay_transport = error
#imet_protocols = all
mailbox_command = procmail -a "$EXTENSION"

```

I hope this is a simple fix for you.

Thank you in advance,
Sebastião

---

### Post by SeijiSensei on 2014-01-16
You need to use [transport maps]("https://www.google.com/search?q=postfix+transport+maps") keyed by the destination host or domain.  An entry looks like this:

```
example.com     smtp:relay.example.com
```

would send all mail for example.com to relay.example.com rather than the default delivery method.

---

### Post by sebastiaopburnay on 2014-01-16
I'm really sorry,

I was feeling strange about this issue, so I took a better look of the script which sends SMSs.

I found out that those SMTP to be SMS messages were being sent not by postfix, but instead by nail.

nail gets its configs from '/etc/nail.rc' which has an entry of 'set smtp=' where I had the stupid SMTP relay.

Again, thank you for your help.

---

