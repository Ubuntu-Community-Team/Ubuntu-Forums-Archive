---
title: "Problem with VPN and postfix mail"
date: 2021-10-19
forum: General Help
---

### Post by Dan Z on 2021-10-19
Problem with VPN and postfix mail
Ubuntu 18.04, Mulvad vpn. gmail server

I have postfix working fine sending mails though gmail while VPN not connected. When connected , sending mail fails.

In looking at mail logs, it appears it is not connecting to gmail.

I contacted Mulvad and there response was:

"We block outgoing port 25. You need to use a server with support for
SSL/TLS (which uses port 587/465) and use that instead."

I am using port 587, as far as I can see. 

Hers is my  /etc/postfix/main.cf:

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
delay_warning_time = 1h

readme_directory = no

# TLS parameters
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

smtpd_relay_restrictions = permit_mynetworks permit_sasl_authenticated defer_unauth_destination
myhostname =dandell-OptiPlex-990
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
mydestination = dandell-OptiPlex-990, localhost.localdomain, , localhost
relayhost = [smtp.gmail.com]:587
smtp_sasl_auth_enable = yes
smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd
smtp_sasl_security_options = 
smtp_tls_CAfile = /etc/ssl/certs/ca-certificates.crt
#smtp_tls_CAfile = /etc/postfix/cacert.pem
smtp_use_tls = yes

mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all
=======================================================
It does say "relayhost = [smtp.gmail.com]:587" , so I assume I am using port 587 for SSL., or is that TLS?

Then I searched for more information on port 25 and found this:

[https://kb.iweb.com/hc/en-us/articles/230241988-Changing-SMTP-ports-Linux-](https://kb.iweb.com/hc/en-us/articles/230241988-Changing-SMTP-ports-Linux-)

"Due to a very large volume of junk email being produced today, most ISPs now block port 25. By default, your server may use port 25 to send mail; as a result, you could find that your email is being blocked.

<snip>

Postfix

You will need to edit the following file:


/etc/postfix/master.cf

Add a line to the file in the following format:


<port> inet n - - - - smtpd

Replace <port> with the appropriate port number, for example:


26 inet n - - - - smtpd"
==========================================
So I added 495 ,  also tried 587, and 26.



465 inet n - - - - smtpd


But still blocked all three cases
Unable to find any other info on my problem
In summary, postfix mail works fine if VPN if off, does not work if VPN is on, any advice would be appeciated, thanks DAN

---

### Post by TheFu on 2021-10-19
25/tcp is used for server-to-server SMTP and SMPTS traffic.
465/tcp and 587/tcp is used for client-to-server (authenticated!) SMTP and SMPTS traffic.

I've never used gmail as a relay.  I only send traffic from my postfix server to other domains on port 25/tcp, but I have an account that doesn't block port 25.

For most SMTP stuff, SSL vs TLS isn't THAT important. any encryption is better than none, but nobody should be using SSL for about the last 5+ yrs as all the SSL protocols have been cracked a long time.  TLS earlier than v1.3 really shouldn't be used either today.  v1.2 was cracked last year and the NSA warned against using it ... though it seems the US military still allows TLS v1.2 since some of their systems cannot support TLS v1.3.  I recall reading the TLS v1.4 should be released in a few months.  Encryption protocols keep moving forward as weaknesses in older versions come to light.
[https://threatpost.com/nsa-urges-sysadmins-to-replace-obsolete-tls-protocols/162814/](https://threatpost.com/nsa-urges-sysadmins-to-replace-obsolete-tls-protocols/162814/) 
When I switched my websites to only allow TLS v1.3, the attacks drastically dropped .... like over 95% less attacks from the "usual suspect" countries.

---

