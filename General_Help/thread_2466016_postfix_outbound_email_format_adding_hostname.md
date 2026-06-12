---
title: "postfix outbound email format adding hostname"
date: 2021-08-17
forum: General Help
---

### Post by melloa on 2021-08-17
Guys,

I'm moving from iRed, so DNS/MX/dmarc/ports open/etc are cared for.

I have a fresh ubuntu 20.04 install with postfix 3.4.13.

Old problem, as per posts I&#8217;ve seen, but unable to pin-point a solution: When sending e-mail using mailutils or webmin the email format is adding the hostname to the domain, i.e.: [EMAIL="user@mailserver.mellodomain.com"]user@mailserver.mellodomain.com[/EMAIL], instead of [EMAIL="user@mellodomain.com"]user@mellodomain.com[/EMAIL].

Could be rewriting functions, but not sure where to look. Read the manual but couldn&#8217;t find how/where to change, nor to check if that&#8217;s the problem.

Below postconf -n output:

```
mello@mailserver:~$ sudo postconf -n
[sudo] password for mello: 
alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
command_directory = /usr/sbin
compatibility_level = 2
daemon_directory = /usr/lib/postfix/sbin
data_directory = /var/lib/postfix
debugger_command = PATH=/bin:/usr/bin:/usr/local/bin:/usr/X11R6/bin ddd $daemon_directory/$process_name $process_id & sleep 5
home_mailbox = Maildir/
inet_protocols = all
local_recipient_maps = unix:passwd.byname $alias_maps
mailq_path = /usr/bin/mailq
mydestination = $myhostname, localhost.$mydomain, localhost, $mydomain
mydomain = mellodomain.com
myhostname = mailserver
mynetworks = 127.0.0.0/8, 10.10.10.0/24
mynetworks_style = subnet
myorigin = $mydomain
newaliases_path = /usr/bin/newaliases
sendmail_path = /usr/sbin/postfix
setgid_group = postdrop
smtpd_banner = $myhostname ESMTP
smtpd_recipient_restrictions = permit_mynetworks, permit_auth_destination, permit_sasl_authenticated, reject append_dot_mydomain = no
smtpd_sasl_auth_enable = yes
smtpd_sasl_local_domain = $myhostname
smtpd_sasl_path = private/auth
smtpd_sasl_security_options = noanonymous
smtpd_sasl_type = dovecot
unknown_local_recipient_reject_code = 550

```

I have set myhostname and mydomain to the mailserver and mellodomain.com respectively and used my destination as $mydomain.

Any assistance in resolve this problem will be appreciated.


Best regards,
Al

---

