---
title: "Postfix/Dovecot help please"
date: 2023-12-25
forum: General Help
---

### Post by artisanpens on 2023-12-25
Hi all,

I have installed Postfix and Dovecot via Web min on a server
Distributor ID:    UbuntuDescription:    Ubuntu 23.04
Release:    23.04
Codename:    lunar

I have setup a domain which resolves for www etc.

I have added a second domain via virtual hosts.

I can receive email sent to the second domain but get [COLOR=#000000][FONT=monospace]host {domain1.com}[107.191.46.74] said: 550[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]"550 5.1.1 {<[/FONT][/COLOR][EMAIL="sales@artisan-pens.com"]sales@[/EMAIL]domain1.com[COLOR=#000000][FONT=monospace]>}: Recipient address rejected: User unknown in virtual alias table\r\n"

[/FONT][/COLOR]MY Postfix main.cf file contains

smtpd_relay_restrictions = permit_mynetworks permit_sasl_authenticated defer_unauth_destination
myhostname = Artisan-pens
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
mydestination = $myhostname, {domain1}, localhost.localdomain,mail.{domain1.com}, $mydomain , localhost, {domain2}
mynetworks = 127.0.0.0/8 [::ffff:12
 
to clarify I have replaced the real domain names with {domain1} and {domain2} for this post.

Has anyone any idea how to receive email to the {domain1} mailboxes

Thanks in advance and Happy Christmas

---

### Post by TheFu on 2023-12-27
23.04 support ends any day. Definitely before Feb.  You need to move to 23.10 and plan to move to an LTS release - either back to 22.04 or 24.04 (when released).

It isn't worth your or our time to do anything on a non-supported release. For servers, especially, do yourself a favor, only run LTS releases.

You need to be very clear about domains, since there are 50 different specific types.

Quickly looking, the **mynetworks** line is broke.  Mine looks like this - 172.22.22.45 is my real email server that this gateway accepts email from that are allowed to be from our domains.  1 IP. No others. Period.
```
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128 172.22.22.45/32
```

Also, hostnames are case-insensitive, to best to never mix case in those.  Some scripts that get used to manage systems may not handle mixed case.


Did you run **sudo newaliases** after fixing the /etc/aliases file?

BTW, Webmin causes more problems than is solves. Learn to do things manually and only use webmin AFTER you 100% know how to do it manually. Without that, it is likely just another attack vector for bad-guys to abuse.

Use **postconf -n** to check for syntax issues in postscript configs.  On my working email gateway, 
```
$ postconf -n |wc -l
40
```
so 6 lines doesn't seem like anywhere sufficient to have a working config.
I think you need a **myorigin**

Whenever posting config files or terminal stuff, please, please, please use forum code tags.

---

