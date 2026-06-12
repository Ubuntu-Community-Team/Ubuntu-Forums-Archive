---
title: "Setting up a Mailserver"
date: 2007-08-19
forum: General Help
---

### Post by kenmiles on 2007-08-19
Can anyone please help me with this problem.
I am setting up a mail server on Ubuntu 6.10 and have followed the guide but when I issue the command - 
telnet kmiles.co.uk 25
it just hangs there trying to connect.
My postfix main.cf is as followes -

 smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no
append_dot_mydomain = no
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache
myhostname = kenneth-desktop
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = kmiles.co.uk, kenneth-desktop, localhost.localdomain, localhost
relayhost = 
mynetworks = 127.0.0.0/8
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all

My DNS records are as followes -
kmiles.co.uk		A	217.42.233.244
[www.kmiles.co.uk](www.kmiles.co.uk)	A	217.42.233.244
kmiles.co.uk		MX	kmiles.co.uk		10

Any help on this is very welcome as I can't seem to find where I am going wrong.

Thanks in advance, Kenneth.

---

### Post by kenmiles on 2007-08-19
Have now solved it. It was the settings in the BT hub that I had to change.
Regards, Kenneth.

---

