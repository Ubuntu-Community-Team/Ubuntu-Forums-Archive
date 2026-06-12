---
title: "Postfix undelivered mail (self signed certificate in chain) with smartCom certs"
date: 2007-10-26
forum: General Help
---

### Post by jpkeller on 2007-10-26
I am getting errors in my postfix logs, and mails are not being delivered to some addresses: 

"postfix/smtp[10538]: certificate verification failed for *****.com: num=19:self signed certificate in certificate chain"


I've just set up postfix to reference all the the SSL certificates I've gotten from startCom -

relevant main.cf lines: 
smtpd_sasl_local_domain =
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtp_tls_note_starttls_offer = yes
# smtpd_tls_key_file = /etc/postfix/ssl/smtpd.key
# smtpd_tls_cert_file = /etc/postfix/ssl/smtpd.crt
# smtpd_tls_CAfile = /etc/postfix/ssl/cacert.pem
smtpd_tls_key_file = /etc/postfix/ssl/startCom/ssl.key
smtpd_tls_cert_file = /etc/postfix/ssl/startCom/ssl.crt
smtpd_tls_CAfile = /etc/postfix/ssl/startCom/ca.crt

smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom
smtpd_tls_auth_only = no
smtp_use_tls = yes
smtpd_use_tls = yes






When I run: 
openssl s_client -starttls smtp -showcerts -connect 127.0.0.1:25

it returns: 
CONNECTED(00000003)
10543:error:140770FC:SSL routines:SSL23_GET_SERVER_HELLO:unknown protocol:s23_clnt.c:567:


same result if I use the external IP - 


any suggestions for next steps? I am pretty stuck on this - I have also set up a virtualhost with the ssl certs for apache as outlined in the installation guidelines, but this apparently hasn't affected the mailer.

---

