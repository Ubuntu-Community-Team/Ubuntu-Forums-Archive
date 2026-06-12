---
title: "Postfix Problem"
date: 2008-06-23
forum: General Help
---

### Post by Peque on 2008-06-23
Hey There forum. 

I've changed the mailserver at work from a redhat with sendmail to an Ubuntu with Postfix.
Our internal salessystem aree still running Redhat - but I cannot get this server to relay through our mailserver. 
A postconf -n from the mailserver: 
# postconf -n
alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
broken_sasl_auth_clients = yes
config_directory = /etc/postfix
content_filter = smtp-amavis:[127.0.0.1]:10024
inet_interfaces = all
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
mydestination = 
myhostname = insatech.com
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128 172.16.50.0/23
myorigin = /etc/mailname
readme_directory = no
recipient_delimiter = +
relayhost = 
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache
smtp_use_tls = yes
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_delay_reject = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,	reject_unauth_destination,	permit_mynetworks,	check_relay_domains
smtpd_sasl_auth_enable = yes
smtpd_sasl_local_domain = 
smtpd_sasl_path = private/auth-client
smtpd_sasl_security_options = noanonymous
smtpd_sasl_type = dovecot
smtpd_tls_CAfile = /etc/postfix/certs/cacert.pem
smtpd_tls_cert_file = /etc/postfix/certs/mailcert.pem
smtpd_tls_key_file = /etc/postfix/certs/mailkey.pem
smtpd_tls_loglevel = 1
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtpd_tls_session_cache_timeout = 3600s
smtpd_use_tls = yes
tls_random_exchange_name = /var/run/prng_exch
tls_random_source = dev:/dev/random
transport_maps = hash:/etc/postfix/transport
virtual_alias_maps = mysql:/etc/postfix/mysql_virtual_alias_maps.cf
virtual_gid_maps = static:5000
virtual_mailbox_base = /storage
virtual_mailbox_domains = mysql:/etc/postfix/mysql_virtual_domains_maps.cf
virtual_mailbox_limit = 5120000000
virtual_mailbox_maps = mysql:/etc/postfix/mysql_virtual_mailbox_maps.cf
virtual_minimum_uid = 5000
virtual_transport = virtual
virtual_uid_maps = static:5000

But getting this error when trying to sending mail from salessystemserver through the mailserver: 
Jun 23 13:09:25 insa02 sendmail[23902]: m5NB9PFP023902: Authentication-Warning: hugin.insatech.com: mera set sender to [M0645134]<jah@insatech.com> using -f
Jun 23 13:09:25 insa02 sendmail[23902]: m5NB9PFP023902: from=[M0645134]<jah@insatech.com>, size=70285, class=0, nrcpts=1, msgid=<200806231109.m5NB9PFP023902@hugin.insatech.com>, bodytype=8BITMIME, relay=mera@localhost
Jun 23 13:09:25 insa02 sendmail[23902]: STARTTLS=client, relay=mail.insatech.com, version=TLSv1/SSLv3, verify=FAIL, cipher=DHE-RSA-AES256-SHA, bits=256/256
Jun 23 13:09:25 insa02 sendmail[23902]: m5NB9PFP023902: to=hjo@welltec.dk, ctladdr=[M0645134]<jah@insatech.com> (500/500), delay=00:00:00, xdelay=00:00:00, mailer=relay, pri=100285, relay=mail.insatech.com [172.16.50.6], dsn=5.7.1, stat=Service unavailable
Jun 23 13:09:25 insa02 sendmail[23902]: m5NB9PFP023902: m5NB9PFQ023902: DSN: Service unavailable
Jun 23 13:09:25 insa02 sendmail[23902]: m5NB9PFQ023902: to=[M0645134]<jah@insatech.com>, delay=00:00:00, xdelay=00:00:00, mailer=relay, pri=101309, relay=mail.insatech.com [172.16.50.6], dsn=2.0.0, stat=Sent (Ok: queued as 0EDFD15025B)

 

Our mailserver IP: 172.16.50.6
Our Salessytem server: 172.16.50.3
So I was wondering that is it possible to allow on host to be able top relay through our mailserver - Or am I doing something totally wrong here

---

