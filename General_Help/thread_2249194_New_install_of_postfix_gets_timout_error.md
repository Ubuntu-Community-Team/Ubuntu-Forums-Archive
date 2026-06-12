---
title: "New install of postfix gets timout error"
date: 2014-10-20
forum: General Help
---

### Post by bulrush2 on 2014-10-20
[LIST]
[*]New install of Ubuntu 14.04 
[*]Postfix (There is no switch to get the version but it was installed today.) 
[*]Assume I'm a newbie and not all things have been setup. The server is for internal development and outgoing email only. It is not a web server, an FTP server, or anything else. 
[*]Looked at instructions here: [https://rtcamp.com/tutorials/linux/ubuntu-postfix-gmail-smtp/](https://rtcamp.com/tutorials/linux/ubuntu-postfix-gmail-smtp/) 
[*]I don't need SSL or a CA certificate. I just use username and password authentication. 
[*]I will have outgoing email only. 
[*]Also note that this is an internal server so DNS is not set up, as I'm only sending outgoing emails. 
[*]Installed postfix via 'sudo apt-get install postfix mailutils' 
[*]Here is /etc/postfix/main.cf file: 
[/LIST]

```
#### begin file ####
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
#smtpd_use_tls=yes
#smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
#smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

smtpd_relay_restrictions = permit_mynetworks permit_sasl_authenticated defer_unauth_destination
#myhostname = ubuntucomp
myhostname = ubuntucomp.net
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
mydestination =myemail.com, localhost.localdomain, , localhost
relayhost = [smtpout.server.net]:587
smtp_sasl_auth_enable = yes
smtp_sasl_password_maps = hash:/etc/postfix/smtp_auth
smtp_sasl_security_options = noanonymous

mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 1000000000
recipient_delimiter = +
inet_interfaces = all
myorigin = /etc/mailname
inet_protocols = all
#### end file ####

```

My /etc/hosts file has an entry for the SMTP server like this: 1.2.3.4<tab>smtpout.server.net

Do I have to make an entry in my iptables? Which entry do I make for the SMTP server? 

I have no idea what to put in "mynetworks" in main.cf. If my ubuntu server IP is 122.123.169.5 would I put: "122.123.0.0/8 [::ffff:122.123.0.0.0]/104 [::1]/128"?

I make an email like this: mail -s "test subject" [EMAIL="toaddr@somewhere.com"]toaddr@somewhere.com[/EMAIL]
Then I enter body text and hit ^D on an empty line. 

When I do 'mailq' I get this error on all my emails" "delivery temporarily suspended: connect to smtpout.server.net[1.2.3.4]:587: Connection timed out". My /var/log/mail.log says the same thing.

"Before you start a mail server, you must verify your server&#8217;s FQDN, reverse PTR, MX records." I don't think I have any of this. I wouldn't know where to start, this is not a registered server, it does not have an official domain.

---

### Post by Doug S on 2014-10-20
> **bulrush2 said:**
> Do I have to make an entry in my iptables? Which entry do I make for the SMTP server?You shouldn't need to, because you are opening an outgoing connection (assuming your iptables rule set allows you do do that).> **bulrush2 said:**
> I have no idea what to put in "mynetworks" in main.cf. If my ubuntu server IP is 122.123.169.5 would I put: "122.123.0.0/8 [::ffff:122.123.0.0.0]/104 [::1]/128"?No. The "mynetworks" directive is to identify your LAN. Here is an example of mine, where my LAN is 192.168.111.0/24:```
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128 192.168.111.0/24
```> **bulrush2 said:**
> When I do 'mailq' I get this error on all my emails" "delivery temporarily suspended: connect to smtpout.server.net[1.2.3.4]:587: Connection timed out". My /var/log/mail.log says the same thing.
"Before you start a mail server, you must verify your server’s FQDN, reverse PTR, MX records." I don't think I have any of this. I wouldn't know where to start, this is not a registered server, it does not have an official domain.Yes, I don't think you can do what you are trying to do (but am not certain (I have never tried without a FQDN and MX records properly setup on some external DNS)).

---

