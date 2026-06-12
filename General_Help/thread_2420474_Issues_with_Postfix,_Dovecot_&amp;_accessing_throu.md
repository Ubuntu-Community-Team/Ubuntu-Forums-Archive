---
title: "Issues with Postfix, Dovecot &amp; accessing through client"
date: 2019-06-06
forum: General Help
---

### Post by waddellgaz on 2019-06-06
Hello All,

New to these forums (and new ish to linux), apologies if I'm posting in the wrong place.

So I'm trying to set up a mail server on my VPS, which I can then hook up with thunderbird/ ms outlook.

Step1. Postfix
I believe I have this set up correctly, I am able to send and receive mail with user/domain [EMAIL="gary@waddellfamily.co.uk"]gary@x[/EMAIL]xx.co.uk

For reference here is my Postfix config settings

```
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


# TLS parameters
#smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
#smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache


# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.


smtpd_relay_restrictions = permit_mynetworks permit_sasl_authenticated defer_unauth_destination
myhostname = HostVpsServer
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = $mydomain
mydestination = $myhostname, HostVpsServer, localhost.localdomain, localhost
relayhost = 
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all
home_mailbox = Maildir/
virtual_alias_maps = hash:/etc/postfix/virtual
mydomain = *mydomain*
mailbox_command = 


#added after mail would send 04June2019
smtpd_sasl_auth_enable = yes
#smtpd_sasl_security_options = noanonymous
smtpd_sasl_type = dovecot
smtpd_sasl_path = private/auth
smtpd_sasl_local_domain = 
broken_sasl_auth_clients = yes


smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtpd_tls_auth_only = no
smtpd_use_tls = yes
smtp_use_tls = yes
smtp_tls_note_starttls_offer = yes
smtpd_tls_key_file = /etc/ssl/private/xxx.key
smtpd_tls_cert_file = /etc/ssl/certs/xxx.crt
smtpd_tls_CAfile = /etc/ssl/certs/cacert.pem


smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s

```
Step2. Dovecot

I think somewhere in here, this is where it's going wrong. I followed a guide somewhere online and generated some SSL keys using openssl.

```
10-ssl.conf
##
## SSL settings
##


# SSL/TLS support: yes, no, required. <doc/wiki/SSL.txt>
ssl = required


# PEM encoded X.509 SSL/TLS certificate and private key. They're opened before
# dropping root privileges, so keep the key file unreadable by anyone but
# root. Included doc/mkcert.sh can be used to easily generate self-signed
# certificate, just make sure to update the domains in dovecot-openssl.cnf
#original which allowed partial email function with test email in only
ssl_cert = </etc/ssl/certs/xxx.crt
ssl_key = </etc/ssl/private/xxx.key






# If key file is password protected, give the password here. Alternatively
# give it when starting dovecot with -p parameter. Since this file is often
# world-readable, you may want to place this setting instead to a different
# root owned 0600 file by using ssl_key_password = <path.
ssl_key_password = *mypassword*


# PEM encoded trusted certificate authority. Set this only if you intend to use
# ssl_verify_client_cert=yes. The file should contain the CA certificate(s)
# followed by the matching CRL(s). (e.g. ssl_ca = </etc/ssl/certs/ca.pem)
#ssl_ca = 


# Require that CRL check succeeds for client certificates.
#ssl_require_crl = yes


# Directory and/or file for trusted SSL CA certificates. These are used only
# when Dovecot needs to act as an SSL client (e.g. imapc backend). The
# directory is usually /etc/ssl/certs in Debian-based systems and the file is
# /etc/pki/tls/cert.pem in RedHat-based systems.
#ssl_client_ca_dir =
#ssl_client_ca_file =


# Request client to send a certificate. If you also want to require it, set
# auth_ssl_require_client_cert=yes in auth section.
#ssl_verify_client_cert = no


# Which field from certificate to use for username. commonName and
# x500UniqueIdentifier are the usual choices. You'll also need to set
# auth_ssl_username_from_cert=yes.
#ssl_cert_username_field = commonName


# DH parameters length to use.
#ssl_dh_parameters_length = 1024


# SSL protocols to use
#ssl_protocols = !SSLv2


# SSL ciphers to use
#ssl_cipher_list = ALL:!LOW:!SSLv2:!EXP:!aNULL


# Prefer the server's order of ciphers over client's.
#ssl_prefer_server_ciphers = no


# SSL crypto device to use, for valid values run "openssl engine"
#ssl_crypto_device =


# SSL extra options. Currently supported options are:
#   no_compression - Disable compression.
#ssl_options =

```


When I try to connect the account with outlook, it seems to do 50% of the job and send the test email, the bit it fails at is "log into incoming mail server". See attached 2x images with log output of this.

Any ideas?

---

### Post by waddellgaz on 2019-06-06
Never mind all - even though I'd spent around 5 hours troubleshooting before posting - 1 hour after adding to this forum I got it working :p.

Turns out it was the client MS outlook settings issue, nothing to do with Postfix or Dovecot.

For anyone else with the same issue check these settings;
From account settings click more settings
Outgoing server tab > Ensure "my outgoing server SMTP required authentication is selected"
Advanced tab > IMAP port 143 and encrypted connection set to TLS
Advanced tab > SMTP port 25 and encrypted connection set to TLS

Woohoo!

---

### Post by kpatz on 2019-06-06
I would edit your email address out of your post so spammers don't pick it up.

I would also configure Postfix to accept authenticated SMTP connections on port 587, since many ISPs block port 25 and you may find yourself unable to send mail from your client on that port.

To do this, edit master.cf and uncomment the line that reads:```
#submission inet n       -       y       -       -       smtpd
```and then restart Postfix.  Then set Outlook to send SMTP on 587 instead of 25, and you should be golden.

---

### Post by waddellgaz on 2019-06-06
Thanks kpatz - done that. 

You're a legend for the advice :)

---

