---
title: "Postfix cannot allocate memory"
date: 2006-10-07
forum: General Help
---

### Post by Orestes on 2006-10-07
I'm having trouble installing postfix. The install goes fine, I enter the information into the install script, but when the postfix command is run, The daemon fails to initialize.

I get this in /var/log/mail.err:
```
Oct  7 22:22:14 silver postfix/master[26245]: fatal: pipe: Cannot allocate memory
```

I'm on a 64bit VPS running Breezy Badger Server.

My main.cf is:

[CODE][root@silver:/etc/postfix# cat main.cf
# See /usr/share/postfix/main.cf.dist for a commented, more complete version

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

myhostname = silver.woodwaysolutions.co.uk
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = silver.woodwaysolutions.co.uk, localhost, localhost.localdomain, localhost, woodwaysolutions.co.uk
relayhost =
mynetworks = 127.0.0.0/8
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
mailbox_command = procmail -a "$EXTENSION"
/CODE]


Anybody got any ideas? Should I file a bug report?
:-k

---

### Post by lidingtian on 2006-10-07
> **Orestes said:**
> I'm having trouble installing postfix. The install goes fine, I enter the information into the install script, but when the postfix command is run, The daemon fails to initialize.

I get this in /var/log/mail.err:
```
Oct  7 22:22:14 silver postfix/master[26245]: fatal: pipe: Cannot allocate memory
```

I'm on a 64bit VPS running Breezy Badger Server.

My main.cf is:

[CODE][root@silver:/etc/postfix# cat main.cf
# See /usr/share/postfix/main.cf.dist for a commented, more complete version

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

myhostname = silver.woodwaysolutions.co.uk
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = silver.woodwaysolutions.co.uk, localhost, localhost.localdomain, localhost, woodwaysolutions.co.uk
relayhost =
mynetworks = 127.0.0.0/8
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
mailbox_command = procmail -a "$EXTENSION"
/CODE]


Anybody got any ideas? Should I file a bug report?
:-k

[&#21147;&#39030;&#22825;]("http://www.lidingtian.com")
[lidingtian]("http://www.lidingtian.com")
[&#26426;&#26800;]("http://www.lidingtian.com")
[&#20379;&#27714;&#20449;&#24687;]("http://www.lidingtian.com")

---

### Post by Orestes on 2006-10-08
Thanks, lidingtian. Awesome.

Whut? :)

---

### Post by Traffic on 2008-03-19
Hello...

Any idea what the answer was for this...?

I have the same exact problem - and, cannot find any solutions...


...

---

