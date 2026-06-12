---
title: "Text based mail ?????????????????????"
date: 2007-03-14
forum: General Help
---

### Post by raidlost on 2007-03-14
all I need to do is send a mail message from a terminal to a external mail server using mailx..\\

I have tried postfix, exim4 and sendmail.......

nothing fancy :KS 

but obviously it has now taken me 9 days in Ubuntu 


what is the trick with linux :( 

and when i say 9 days I have spent at least 7 hours solid a day on this problem as it is urgent.

the mail must be delivered through a exchange server all i need to do is
:::::
mailx user@domain
:::::

any help at this point will restore what is left of my sleep pattern.....!!!!

---

### Post by scxtt on 2007-03-14
all i've EVER had to do was install both "postfix" and "mailx" ... i do a test mail immediately and it always works ...

what do you mean "through [an] exchange server"?  i use what i've mentioned above to send mail from MY box to my work email (an exchange server) - and it works too ...

---

### Post by raidlost on 2007-03-14
Yes 

I need to send mail through our work server {an} exchange 2003 server.
I have installed postfix according to the Ubuntu server guide
I have installed mailx
technically it should work {according to the manuals}

:confused: 
I type
#mailx user@domain
Subject: bbbbbbbbbbbbbbbbb
bbbbbbbbbbbbbbbbbbbbbb

~.

Ubuntu says (cos I am sure it has a mind of its own)
postdrop: warning: unable to look up public/pickup: No such file or directory

:confused:

---

### Post by scxtt on 2007-03-14
what do you get if you type **mailq**? is everything you've sent "stuck" in the queue?

i'm still not clear on your exchange references - you don't send mail through the exchange server, exchange isn't your mta (mail transfer agent), that's what postfix is for ... but our work exchange server will accept those messages ...

so i can do:

#> mailx -s "test email to work" [email]scxtt@work.com[/email] < message.txt

and get that email (from scxtt@kubuntu) when i check my work email ...

---

### Post by raidlost on 2007-03-14
fine :popcorn: 

-- postfix is the MTA --

Exchange is accepting mail from another linux box (pc) like you have specified


#> mailx -s "test email to work" [email]scxtt@work.com[/email] < message.txt

the pc I have, needs to replace the existing one. and needs to send a message like you have specified...


#> mailx -s "test email to work" [email]scxtt@work.com[/email] < message.txt

the mail is in the queue and goes to the queue when I send a mail. the system time on the pc is 11:59 but the message time is 09:59 ????

nothing seems to leave the queue

---

### Post by scxtt on 2007-03-14
post the contents of **/etc/postfix/main.cf** if you would :)

and maybe the contents of **/etc/hosts** ...

---

### Post by raidlost on 2007-03-14
sorry slow connection for some reason

i have attached the files i hope you get them

hosts

127.0.0.1 localhost
10.1.2.150 squid.domain

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

---

### Post by raidlost on 2007-03-14
main.cf

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

# TLS parameters
smtpd_tls_cert_file = /etc/ssl/certs/smtpd.crt
smtpd_tls_key_file = /etc/ssl/private/smtpd.key
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = squid.ubuntu.domain
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination =
relayhost =
mailbox_size_limit = 0
recipient_delimiter =
inet_interfaces = all
inet_protocols = all
smtpd_sasl_local_domain =
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtpd_tls_auth_only = no
smtp_use_tls = yes
smtp_tls_note_starttls_offer = yes
smtpd_tls_CAfile = /etc/ssl/certs/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom
mynetworks = 1

---

### Post by bapoumba on 2007-03-14
Thread moved to "General Help".

---

### Post by raidlost on 2007-03-14
a

---

### Post by scxtt on 2007-03-15
i'd recommend running "sudo dpkg-reconfigure postfix" and selecting the "internet" config ... seems to me you've got more 'options' in main.cf than are really necessary ...

make sure you restart postfix if the reconfigure doesn't do it for you ...

---

