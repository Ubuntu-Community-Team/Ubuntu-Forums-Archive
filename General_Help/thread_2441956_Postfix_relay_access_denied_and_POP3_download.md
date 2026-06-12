---
title: "Postfix relay access denied and POP3 download"
date: 2020-04-28
forum: General Help
---

### Post by scoutdubna on 2020-04-28
I hope someone can help me as I am quickly going bald!


At present I run a Web and Mail server hanging on the end of my ADSL line here in France but in the last year reliability has gone from adequate to terrible so I have moved the Web side to IONOS and now want to move Mail.


Installed Postfix and Dovecot using Webmin and then Let’s Encrypt:
[https://www.digitalocean.com/community/tutorials/how-to-secure-apache-with-let-s-encrypt-on-ubuntu-18-04](https://www.digitalocean.com/community/tutorials/how-to-secure-apache-with-let-s-encrypt-on-ubuntu-18-04)


For Postfix I used:
[https://www.digitalocean.com/community/tutorials/how-to-secure-apache-with-let-s-encrypt-on-ubuntu-18-04](https://www.digitalocean.com/community/tutorials/how-to-secure-apache-with-let-s-encrypt-on-ubuntu-18-04)


The result is that using webmin I can send Email from one user account to another.
From a user account I can send an email to the outside world
From the outside world I can send an email to a postfix user account on the new server


What I cannot do is send from my local PC to the outside world using the SMTP server hosted with IONOS.


I get the message5.7.1 Relay Access Denied


I see from the Internet that this is a common problem but so far all the attempts to resolve this have failed.


Can anyone point me to the error.


Also I am unable to download emails from the server using POP3


Here is the /etc/postfix/main.cf


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
#delay_warning_time = 4h


readme_directory = no


# See [http://www.postfix.org/COMPATIBILITY_README.html](http://www.postfix.org/COMPATIBILITY_README.html) -- default to 2 on
# fresh installs.
compatibility_level = 2


# TLS parameters
smtpd_tls_cert_file = /etc/letsencrypt/live/dubnafrance.co.uk/fullchain.pem
smtpd_tls_key_file = /etc/letsencrypt/live/dubnafrance.co.uk/privkey.pem
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache


# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.


smtpd_relay_restrictions = permit_mynetworks permit_sasl_authenticated defer_unauth_destination
myhostname = dubnafrance.co.uk
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = dubnafrance.co.uk, localhost.co.uk, , localhost, ugandanetwork.org.uk
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 0
recipient_delimiter = +
inet_protocols = all
virtual_alias_maps = hash:/etc/postfix/virtual
home_mailbox = Maildir/
smtpd_sasl_auth_enable = yes
smtpd_sasl_type = dovecot
smtpd_sasl_path = private/dovecot-auth
smtpd_sasl_authenticated_header = yes
smtpd_sasl_security_options = noanonymous
smtpd_sasl_local_domain = $myhostname
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = check_sender_access hash:/etc/postfix/sender_access permit_sasl_authenticated permit_mynetworks reject_unauth_destination
mailbox_command = /usr/lib/dovecot/deliver -c /etc/dovecot/dovecot.conf -m "${EXTENSION}"
smtp_use_tls = yes
smtpd_tls_received_header = yes
smtpd_tls_auth_only = yes
tls_random_source = dev:/dev/urandom
mynetworks_style = subnet






#Disable Poodle
smtp_tls_security_level = may
smtpd_tls_mandatory_protocols=!SSLv2,!SSLv3
smtp_tls_mandatory_protocols=!SSLv2,!SSLv3
smtpd_tls_protocols=!SSLv2,!SSLv3
smtp_tls_protocols=!SSLv2,!SSLv3
# Changes to SSL Ciphers
tls_preempt_cipherlist = yes
smtpd_tls_mandatory_ciphers = high
tls_high_cipherlist = ECDHE-RSA-AES256-GCM-SHA384:ECDHE-ECDSA-AES256-GCM-SHA384:ECDHE-RSA-AES256-SHA384:ECDHE-ECDSA-AES256-SHA384:DHE-DSS-AES256-GCM-SHA384:DHE-RSA-AES256-GCM-SHA384:DHE-RSA-AES256-SHA256:DHE-DSS-AES256-SHA256:ADH-AES256-GCM-SHA384:ADH-AES256-SHA256:ECDH-RSA-AES256-GCM-SHA384:ECDH-ECDSA-AES256-GCM-SHA384:ECDH-RSA-AES256-SHA384:ECDH-ECDSA-AES256-SHA384:AES256-GCM-SHA384:AES256-SHA256:ECDHE-RSA-AES128-GCM-SHA256:ECDHE-ECDSA-AES128-GCM-SHA256:ECDHE-RSA-AES128-SHA256:ECDHE-ECDSA-AES128-SHA256:DHE-DSS-AES128-GCM-SHA256:DHE-RSA-AES128-GCM-SHA256:DHE-RSA-AES128-SHA256:DHE-DSS-AES128-SHA256:ADH-AES128-GCM-SHA256:ADH-AES128-SHA256:ECDH-RSA-AES128-GCM-SHA256:ECDH-ECDSA-AES128-GCM-SHA256:ECDH-RSA-AES128-SHA256:ECDH-ECDSA-AES128-SHA256:AES128-GCM-SHA256:AES128-SHA256:NULL-SHA256


/etc/dovecot/dovecont.conf file
## Dovecot configuration file


!include_try /usr/share/dovecot/protocols.d/*.protocol
dict {
  #quota = mysql:/etc/dovecot/dovecot-dict-sql.conf.ext
  #expire = sqlite:/etc/dovecot/dovecot-dict-sql.conf.ext
}


!include conf.d/*.conf:
!include_try local.conf
pop3_uidl_format = %08Xu%08Xv






and here is the error in the mail.log file


Apr 28 11:08:58 dubnafrance postfix/smtpd[109243]: connect from 7.16.204.77.rev.sfr.net[77.204.16.7]
Apr 28 11:08:59 dubnafrance postfix/smtpd[109243]: NOQUEUE: reject: RCPT from 7.16.204.77.rev.sfr.net[77.204.16.7]: 554 5.7.1 <dubnachris@gmail.com>: Relay access denied; from=<chris@dubnafrance.co.uk> to=<dubnachris@gmail.com> proto=ESMTP helo=<junglebook>
Apr 28 11:08:59 dubnafrance postfix/smtpd[109243]: disconnect from 7.16.204.77.rev.sfr.net[77.204.16.7] ehlo=1 mail=1 rcpt=0/1 rset=1 quit=1 commands=4/5
Apr 28 11:09:00 dubnafrance postfix/smtpd[74165]: disconnect from unknown[45.142.195.5] ehlo=1 auth=0/1 rset=1 quit=1 commands=3/4


Hope someone will help please.

CHRIS

---

