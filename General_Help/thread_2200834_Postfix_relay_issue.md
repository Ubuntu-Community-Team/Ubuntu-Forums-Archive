---
title: "Postfix relay issue"
date: 2014-01-21
forum: General Help
---

### Post by michael96 on 2014-01-21
Hello!

First time poster, wasn't sure if this was a proper spot to place this thread, please move if needed.

I seem to have an issue with postfix on ubuntu, i have configured postifx's main.cf "relayhost=172.16.16.9" which should relay email to my external mail server however in the /var/log/mail.log file i see email is still being relayed to "local".

main.cf
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

myhostname = Nagios
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = domain.ca, Nagios, localhost.localdomain, localhost
relayhost = 172.16.16.9
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all



/var/log/mail.log
Jan 21 16:20:00 Nagios postfix/local[2848]: 1E4F81206A9: to=<alerts@domain.ca>, orig_to=<nagios@domain.ca>, relay=local, delay=0.01, delays=0/0/0/0.01, dsn=5.1.1, status=bounced (unknown user: "alerts")
Jan 21 16:20:00 Nagios postfix/qmgr[2808]: 1E4F81206A9: removed


my mail server will relay email from any internal IP with no authentication so that should be no issue, i have also restarted postfix and the entire server several times..

any help would be greatly appreciated!

Thanks in advance!

---

### Post by SeijiSensei on 2014-01-21
Try removing "domain.ca" from the list in the mydestination directive. I'm pretty sure that tells Postfix to deliver mail for domain.ca locally.

---

### Post by michael96 on 2014-01-21
Thank you SeijiSensei !! 

marked resolved.
Thanks again! 
Michael.

---

