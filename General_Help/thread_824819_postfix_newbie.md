---
title: "postfix newbie"
date: 2008-06-10
forum: General Help
---

### Post by stefanoBelletti on 2008-06-10
HI all,
i've installed postfix following the how-to found on the net.
(i.e.: [https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix) )
i've installed it in the simpliest way onto kubuntu 8.04
I send an email email, /var/log/email looks good:
-----------------------------------------
Jun 10 17:53:00 ubuntu postfix/smtpd[8086]: connect from localhost[127.0.0.1]
Jun 10 17:53:31 ubuntu postfix/smtpd[8086]: 9285EF2106: client=localhost[127.0.0.1]
Jun 10 17:53:37 ubuntu postfix/cleanup[8089]: 9285EF2106: message-id=<20080610155331.9285EF2106@ubuntu.workgroup>
Jun 10 17:53:37 ubuntu postfix/qmgr[8082]: 9285EF2106: from=<root@localhost>, size=354, nrcpt=1 (queue active)
Jun 10 17:53:37 ubuntu postfix/local[8091]: 9285EF2106: to=<fmaster@localhost>, relay=local, delay=13, delays=13/0.01/0/0.01, dsn=2.0.0, status=sent (delivered to maildir)
Jun 10 17:53:37 ubuntu postfix/qmgr[8082]: 9285EF2106: removed

-----------------------------------------
but the "mail" command simply returns:
"no mail for fmaster"
:-(
looking in /home/fmaster/Maildir/new
there is my bloo## email :-((
what am i doing wrong ?
Thank you !
main.cf:--------------------------------
myorigin = /etc/mailname
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no
append_dot_mydomain = no
readme_directory = no
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/
smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
myhostname = ubuntu.workgroup
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydomain = topolino.mooo.com
mydestination = topolino.mooo.com,ubuntu.workgroup,localhost
relayhost =
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
mynetworks_style = host
local_recipient_maps =
mydestination = topolino.mooo.com,ubuntu.workgroup,localhost
home_mailbox = Maildir/
mailbox_command =
inet_protocols = all
---------------------------------------------------

---

