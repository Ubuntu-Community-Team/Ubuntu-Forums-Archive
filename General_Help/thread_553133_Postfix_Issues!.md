---
title: "Postfix Issues!"
date: 2007-09-17
forum: General Help
---

### Post by samuelodofin on 2007-09-17
hello guys ive just setted up ubuntu LAMP server package and i was really impressed, everything worked perfectly. I then install webmin and setted up postfix and dovecot (for IMAP and POP3)......

But am now having a problem...no emails are coming through, they all bounce back (even when i tested sending to [email]root@XXX.XXX.XXX.XXX[/email] (thats my ip) .... it didnt come, but i was able to send mails through webmin and i received it without any problem i am also able to send mail to [email]user@mydomail.com[/email] (from webmin) and it went through.....so i am unsure of where the problem lies.....am also not able to access the mails using outlook...eventhough dovecot is working well.........The website opens perfectly. 

I dont know what step ive missed.......heres my postfix config file:

> # See /usr/share/postfix/main.cf.dist for a commented, more complete version


# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
#myorigin = /etc/mailname


myhostname = $mydomain

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

# TLS parameters
smtpd_tls_cert_file = /etc/postfix/ssl/smtpd.crt
smtpd_tls_key_file = /etc/postfix/ssl/smtpd.key
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache

smtpd_sasl_auth_enable = yes
smtpd_sasl_local_domain = 
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtpd_sasl_security_options = noanonymous

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
mydestination = $myhostname, localhost.$mydomain, $mydomain
mynetworks = 127.0.0.0/8, 192.168.1.0/24
mailbox_command = 
mailbox_size_limit = 0
recipient_delimiter = +
inet_protocols = all
myorigin = /etc/mailname
broken_sasl_auth_clients = yes
smtpd_tls_auth_only = no
smtp_use_tls = yes
smtp_tls_note_starttls_offer = yes
smtpd_tls_CAfile = /etc/postfix/ssl/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom
home_mailbox = Maildir/
inet_interfaces = all



Umm....any help will be very welcomed......also also...

telnet localhost 25 from terminal give this:

> Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
220 mydomain.com ESMTP Postfix (Ubuntu)



NOTE: ive changed instances of my domain name to mydomain.....so all mydomains are valid TLD domain names..

---

