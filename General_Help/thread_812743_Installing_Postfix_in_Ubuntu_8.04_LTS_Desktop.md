---
title: "Installing Postfix in Ubuntu 8.04 LTS Desktop"
date: 2008-05-30
forum: General Help
---

### Post by sasm on 2008-05-30
Hello, i'm having difficulties in installing postfix in Ubuntu 8.04LTS Desktop, i follow the steps in the tutorial and when im going to check if everything is ok... i run the command telnet localhost 25... and this is what i get:
Trying 127.0.0.1...
Connected to localhost
Escape character is '^]'.
220 xlconta.com ESMTP Postfix (Ubuntu)
ehlo localhost
250-xlconta.com
250-PIPELINING
250-SIZE 10240000
250-VRFY
250-ETRN
250-STARTTLS
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN

the following: 
250-AUTH LOGIN PLAIN
250-AUTH=LOGIN PLAIN

is missing...why?

Can someone help me???

thank you.

---

### Post by Monicker on 2008-05-30
Are you referring to this tutorial?

[https://help.ubuntu.com/7.10/server/C/postfix.html]("https://help.ubuntu.com/7.10/server/C/postfix.html")

I would double check everything in the SMTP Authentication section.  You could also attach a copy of /etc/postfix/main.cf for review.

---

### Post by sasm on 2008-05-30
Yes i refer to that tutorial, here goes a whats inside my main.cf:

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
# delay_warning_time = 4h

# TLS parameters
smtpd_tls_cert_file = /etc/postfix/ssl/smtpd.crt
smtpd_tls_key_file = /etc/postfix/ssl/smtpd.key
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = xlconta.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
# myorigin = /etc/mailname
myorigin = /etc/mailname
mydestination = xlconta.com, localhost.xlconta, 208.69.34.132
relayhost = 
mynetworks = 127.0.0.0/8 208.69.34.132
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtpd-sasl_local_domain = 
smtpd-sasl_auth_enable = yes
smtpd-sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_tls_auth_only = no
smtp_use_tls = yes
smtpd_tls_note_starttls_offer = yes
smtpd_tls_CAfile = /etc/postfix/ssl/cacert.pem
smtpd_tls_loglevel = 4
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
smtp_tls_note_starttls_offer = yes
tls_random_source = dev:/dev/urandom
home_mailbox = Maildir/
debug_peer_list = problem.xlconta

is there any problem with the config?

Thank u for helping.

---

### Post by Monicker on 2008-05-30
Looks good as far as I can tell.  Do you also have the following lines in /etc/postfix/sasl/smtpd.conf?
```

pwcheck_method: saslauthd
mech_list: plain login
```

You should also look at the postfix logs, /var/log/mail.log, for any reference to "AUTH LOGIN PLAIN".

---

### Post by sasm on 2008-05-30
Ok i've check my /etc/postfix/sasl/samtp.conf an had only this 2 lines there:

pwcheck_method: saslauthd
mech_list: plain login

And if checked in my /var/log/mail.log for references to AUTH LOGIN PLAIN and didn't found any here goes what i have at my mail.log:

May 30 10:10:36 xlconta-desktop postfix/smtpd[22675]: connect from localhost[127.0.0.1]
May 30 10:15:41 xlconta-desktop postfix/smtpd[22675]: timeout after EHLO from localhost[127.0.0.1]
May 30 10:15:41 xlconta-desktop postfix/smtpd[22675]: disconnect from localhost[127.0.0.1]
May 30 10:22:58 xlconta-desktop postgrey: 2008/05/30-10:22:58 Server closing! 
May 30 10:23:01 xlconta-desktop authdaemond: stopping authdaemond children
May 30 10:23:01 xlconta-desktop postfix/master[6494]: terminating on signal 15
May 30 10:24:28 xlconta-desktop amavis[5428]: starting.  /usr/sbin/amavisd-new at xlconta-desktop amavisd-new-2.5.3 (20071212), Unicode aware
May 30 10:24:28 xlconta-desktop amavis[5428]: Perl version               5.008008
May 30 10:24:30 xlconta-desktop postgrey: Process Backgrounded 
May 30 10:24:30 xlconta-desktop postgrey: 2008/05/30-10:24:30 postgrey (type Net::Server::Multiplex) starting! pid(5575) 
May 30 10:24:30 xlconta-desktop postgrey: Binding to TCP port 60000 on host 127.0.0.1  
May 30 10:24:30 xlconta-desktop postgrey: Setting gid to "129 129" 
May 30 10:24:30 xlconta-desktop postgrey: Setting uid to "119" 
May 30 10:24:32 xlconta-desktop authdaemond: modules="authpam", daemons=5
May 30 10:24:32 xlconta-desktop authdaemond: Installing libauthpam
May 30 10:24:32 xlconta-desktop authdaemond: Installation complete: authpam
May 30 10:24:34 xlconta-desktop postfix/master[6148]: daemon started -- version 2.5.1, configuration /etc/postfix
May 30 10:24:42 xlconta-desktop postfix/master[6148]: reload configuration /etc/postfix
May 30 10:26:06 xlconta-desktop postfix/smtpd[7024]: connect from localhost[127.0.0.1]
May 30 10:26:17 xlconta-desktop postfix/smtpd[7024]: disconnect from localhost[127.0.0.1]
May 30 10:39:48 xlconta-desktop postfix/master[6148]: terminating on signal 15
May 30 10:39:49 xlconta-desktop postfix/master[8861]: daemon started -- version 2.5.1, configuration /etc/postfix
May 30 10:40:13 xlconta-desktop postfix/smtpd[8927]: connect from localhost[127.0.0.1]
May 30 10:45:17 xlconta-desktop postfix/smtpd[8927]: timeout after EHLO from localhost[127.0.0.1]
May 30 10:45:17 xlconta-desktop postfix/smtpd[8927]: disconnect from localhost[127.0.0.1]
May 30 11:43:14 xlconta-desktop postfix/smtpd[9752]: connect from localhost[127.0.0.1]
May 30 11:47:28 xlconta-desktop postfix/smtpd[9752]: disconnect from localhost[127.0.0.1]
May 30 11:48:13 xlconta-desktop dovecot: Dovecot v1.0.10 starting up
May 30 11:48:13 xlconta-desktop dovecot: Generating Diffie-Hellman parameters for the first time. This may take a while..
May 30 11:49:45 xlconta-desktop dovecot: ssl-build-param: SSL parameters regeneration completed
May 30 11:52:13 xlconta-desktop dovecot: Killed with signal 15
May 30 11:52:13 xlconta-desktop dovecot: Dovecot v1.0.10 starting up
May 30 11:52:34 xlconta-desktop postfix/smtpd[10171]: connect from ipcop.localdomain[192.168.1.1]
May 30 11:53:27 xlconta-desktop postfix/smtpd[10171]: disconnect from ipcop.localdomain[192.168.1.1]
May 30 11:53:37 xlconta-desktop postfix/master[8861]: terminating on signal 15
May 30 11:53:38 xlconta-desktop postfix/master[10280]: daemon started -- version 2.5.1, configuration /etc/postfix
May 30 11:54:00 xlconta-desktop postfix/smtpd[10348]: connect from ipcop.localdomain[192.168.1.1]
May 30 11:54:28 xlconta-desktop postfix/smtpd[10348]: disconnect from ipcop.localdomain[192.168.1.1]
May 30 11:56:53 xlconta-desktop postfix/master[10280]: reload configuration /etc/postfix
May 30 11:56:53 xlconta-desktop postfix/anvil[10351]: statistics: max connection rate 1/60s for (smtp:192.168.1.1) at May 30 11:54:00
May 30 11:56:53 xlconta-desktop postfix/anvil[10351]: statistics: max connection count 1 for (smtp:192.168.1.1) at May 30 11:54:00
May 30 11:56:53 xlconta-desktop postfix/anvil[10351]: statistics: max cache size 1 at May 30 11:54:00
May 30 11:57:00 xlconta-desktop postfix/smtpd[10413]: initializing the server-side TLS engine
May 30 11:57:00 xlconta-desktop postfix/tlsmgr[10415]: open smtpd TLS cache btree:/var/lib/postfix/smtpd_scache
May 30 11:57:00 xlconta-desktop postfix/tlsmgr[10415]: tlsmgr_cache_run_event: start TLS smtpd session cache cleanup
May 30 11:57:00 xlconta-desktop postfix/smtpd[10413]: connect from localhost[127.0.0.1]
May 30 11:57:10 xlconta-desktop postfix/smtpd[10413]: disconnect from localhost[127.0.0.1]
May 30 11:57:43 xlconta-desktop postfix/smtpd[10413]: connect from localhost[127.0.0.1]
May 30 11:57:51 xlconta-desktop postfix/smtpd[10413]: disconnect from localhost[127.0.0.1]
May 30 12:02:25 xlconta-desktop postfix/smtpd[10542]: initializing the server-side TLS engine
May 30 12:02:25 xlconta-desktop postfix/smtpd[10542]: connect from localhost[127.0.0.1]
May 30 12:07:29 xlconta-desktop postfix/smtpd[10542]: timeout after EHLO from localhost[127.0.0.1]
May 30 12:07:29 xlconta-desktop postfix/smtpd[10542]: disconnect from localhost[127.0.0.1]
May 30 12:13:08 xlconta-desktop postfix/master[10280]: terminating on signal 15
May 30 12:14:05 xlconta-desktop postfix/master[10976]: daemon started -- version 2.5.1, configuration /etc/postfix
May 30 12:14:15 xlconta-desktop postfix/master[10976]: terminating on signal 15
May 30 12:14:16 xlconta-desktop postfix/master[11078]: daemon started -- version 2.5.1, configuration /etc/postfix
May 30 12:14:20 xlconta-desktop postfix/smtpd[11086]: initializing the server-side TLS engine
May 30 12:14:20 xlconta-desktop postfix/tlsmgr[11088]: open smtpd TLS cache btree:/var/lib/postfix/smtpd_scache
May 30 12:14:21 xlconta-desktop postfix/tlsmgr[11088]: tlsmgr_cache_run_event: start TLS smtpd session cache cleanup
May 30 12:14:21 xlconta-desktop postfix/smtpd[11086]: connect from localhost[127.0.0.1]
May 30 12:14:27 xlconta-desktop postfix/smtpd[11086]: disconnect from localhost[127.0.0.1]
May 30 12:18:00 xlconta-desktop postfix/smtpd[11137]: initializing the server-side TLS engine
May 30 12:18:00 xlconta-desktop postfix/smtpd[11137]: connect from ipcop.localdomain[192.168.1.1]
May 30 12:21:59 xlconta-desktop postfix/smtpd[11137]: disconnect from ipcop.localdomain[192.168.1.1]
May 30 12:25:19 xlconta-desktop postfix/anvil[11139]: statistics: max connection rate 1/60s for (smtp:192.168.1.1) at May 30 12:18:00
May 30 12:25:19 xlconta-desktop postfix/anvil[11139]: statistics: max connection count 1 for (smtp:192.168.1.1) at May 30 12:18:00
May 30 12:25:19 xlconta-desktop postfix/anvil[11139]: statistics: max cache size 1 at May 30 12:18:00
May 30 13:14:21 xlconta-desktop postfix/tlsmgr[11088]: tlsmgr_cache_run_event: start TLS smtpd session cache cleanup
May 30 14:14:21 xlconta-desktop postfix/tlsmgr[11088]: tlsmgr_cache_run_event: start TLS smtpd session cache cleanup
May 30 15:14:21 xlconta-desktop postfix/tlsmgr[11088]: tlsmgr_cache_run_event: start TLS smtpd session cache cleanup
May 30 15:48:10 xlconta-desktop postfix/smtpd[13999]: initializing the server-side TLS engine
May 30 15:48:10 xlconta-desktop postfix/smtpd[13999]: connect from ipcop.localdomain[192.168.1.1]
May 30 15:48:54 xlconta-desktop postfix/smtpd[13999]: disconnect from ipcop.localdomain[192.168.1.1]

can u see any problem????

Thank for helping.

---

