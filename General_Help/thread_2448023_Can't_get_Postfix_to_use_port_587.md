---
title: "Can't get Postfix to use port 587"
date: 2020-07-30
forum: General Help
---

### Post by lazloman on 2020-07-30
I'm trying to enable Postfix to Use TLS on port 587. I have these lines in master.cf:

smtpd_use_tls=yes
smtpd_tls_security_level = may
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtpd_sasl_auth_enable = yes
smtp_tls_security_level = may
smtpd_tls_security_level = may

and these lines in main.cf:

submission inet n       -       n       -       -       smtpd -v
  -o smtpd_tls_security_level=encrypt
  -o smtpd_sasl_auth_enable=yes
  -o smtpd_client_restrictions=permit_sasl_authenticated,reject
  -o milter_macro_daemon_name=ORIGINATING

My firewall opens port 587, but on the local network, if I run nmap on the mail server, port 587 is not open:
21/tcp    open  ftp
22/tcp    open  ssh
25/tcp    open  smtp
53/tcp    open  domain
110/tcp   open  pop3
111/tcp   open  rpcbind
139/tcp   open  netbios-ssn
143/tcp   open  imap
445/tcp   open  microsoft-ds
548/tcp   open  afp
631/tcp   open  ipp
783/tcp   open  spamassassin
993/tcp   open  imaps
3306/tcp  open  mysql
5432/tcp  open  postgresql
7999/tcp  open  irdmi2
8080/tcp  open  http-proxy
8181/tcp  open  intermapper
8443/tcp  open  https-alt
10024/tcp open  unknown
10025/tcp open  unknown

telnetting into port 587 yields:
Trying 127.0.0.1...
telnet: Unable to connect to remote host: Connection refused

What am I missing?
Thanks

---

