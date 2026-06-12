---
title: "smtp, postfix setup problem"
date: 2005-04-23
forum: General Help
---

### Post by bahbo on 2005-04-23
I installed Ubuntu onto a partition on my otherwise Debian machine (which uses exim).  I am connected to the internet via dsl, and have been trying to set up postfix so that my mail (from mutt) will be sent to the dsl smtp server.  Since the dsl smtp server requires a username and password, I have this listed in /etc/postfix/passwd_auth (the only line is 
 smtp.sbcglobal.yahoo.com        [email]my.user.name@sbcglobal.net:my.pass[/email]word
For some strange reason that I don't understand, when I look at mailq, it says they are trying to connect to smtp at a different location (smtp.ucsc.edu).  My main.cf file reads as follows:
 smtpd_banner = $myhostname ESMTP $mail_name (Debian/GNU)
biff = no
append_dot_mydomain = no
myhostname = perelandra.felton.org
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = 
relayhost = 
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
smtp_sasl_auth_enable = yes
smtp_sasl_password_maps = hash:/etc/postfix/smtp_auth
smtp_sasl_security_options =

I tried postmap hash:smtp_auth and postfix reload.  
I've tried everything that I can think of, but am obviously doing something wrong.  I've thought about installing exim (which I know how to work with), but would prefer to stay with the Ubuntu defaults if possible.  Any help would be appreciated.
Thanks,
Ric

---

### Post by greengeek on 2005-09-25
I had a similar problem a while back. Basically, you've told postfix how to log into your ISPs mail server, but you haven't actually told it to relay mail through that server, so it's trying to directly send the mail to its final destination.

Quick and simple fix:
Change the relayhost = line to:
```
relayhost = [smtp.sbcglobal.yahoo.com]
```

and reload the postfix configuration. Note, the brackets are important, they will make sure that postfix properly negotiates any sort of redirection or clustering that your ISP performs on their smtp servers. That should get everything set.

Hope that helps.

---

### Post by SpectralDesign on 2005-11-12
I'm having trouble with SMTP relay via postfix and my web hosting provider....  I got this message when I tried to send a message:

<user@example.net>: host smtp.example.com[4.10.x.x] said:
    553 Sorry, that domain isn't in my list of allowed rcpthosts. (in reply to
    RCPT TO command)

As if it didn't even try to do the auth... here's my main.cf:

# See /usr/share/postfix/main.cf.dist for a commented, more complete version

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h


myhostname = localhost.localdomain
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
mydestination = localhost, localhost.localdomain, localhost.localdomain, localhost
relayhost = [smtpout.example.net]:3535
mynetworks = 127.0.0.0/8
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
smtp_sasl_auth_enable = yes
smtp_sasl_password_maps = hash:/etc/postfix/smtp_auth
smtp_sasl_security_options = noanonymous

PS - my /etc/postfix/smtp_auth looks like:
smtpout.example.net        [email]user@mydomain.net[/email]:passwd

---

