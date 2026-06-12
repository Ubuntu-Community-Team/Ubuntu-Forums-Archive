---
title: "PHP mail() still sending on 25 port, when should on 587 (configured in Postfix)"
date: 2015-07-30
forum: General Help
---

### Post by Jarucy on 2015-07-30
Hello,
 
I have serious problem which I can’t solve with google help. Some time ago I’ve got not very old server on Linux 2.6.24 with PHP Version 5.2.4
I’m working on some scripts in PHP there and noticed that I can’t send emails via mail() function in PHP. I don’t see any errors in PHP, but server don’t sending any emails (I’m using it only for sending few emails like actvation code for forum etc.). I’m newbie in Linux, so my knowledge is low in this topic. But google our friend ;)
 
I’ve checked mail logs and there is a lot such entries:
 
> Jul 30 13:59:49 itsmydomain postfix/pickup[1336]: 1C7233000864: uid=33 from=<www-data>
Jul 30 13:59:49 itsmydomain postfix/cleanup[1378]: 1C7233000864: message-id=<20150730125949.1C7233000864@itsmydomain >
Jul 30 13:59:49 itsmydomain postfix/qmgr[1337]: 1C7233000864: from=<www-data@itsmydomain.com>, size=898, nrcpt=1 (queue active)
Jul 30 14:00:19 itsmydomain postfix/smtp[1380]: connect to gmail-smtp-in.l.google.com[173.194.78.26]:25: Connection timed out
Jul 30 14:00:49 itsmydomain postfix/smtp[1380]: connect to alt1.gmail-smtp-in.l.google.com[74.125.143.26]:25: Connection timed out
Jul 30 14:01:19 itsmydomain postfix/smtp[1380]: connect to alt2.gmail-smtp-in.l.google.com[74.125.130.26]:25: Connection timed out
Jul 30 14:01:49 itsmydomain postfix/smtp[1380]: connect to alt3.gmail-smtp-in.l.google.com[64.233.188.27]:25: Connection timed out
Jul 30 14:02:19 itsmydomain postfix/smtp[1380]: connect to alt4.gmail-smtp-in.l.google.com[173.194.72.26]:25: Connection timed out
Jul 30 14:02:19 itsmydomain postfix/smtp[1380]: 1C7233000864: to=<just_tester45@gmail.com>, relay=none, delay=150, delays=0.05/0/150/0, dsn=4.4.1, status=deferred (connect to alt4.gmail-smtp-in.l.google.com[173.194.72.26]:25: Connection timed out)
 
On server is Postfix. And probably with smtp port 25 works perfect. 
But after some googling I’ve discovered that my ISP blocking (probably) port 25. I think here is proof:
 
> # telnet smtp.gmail.com 25
Trying 64.233.184.109...
Trying 64.233.184.108...
telnet: Unable to connect to remote host: Connection timed out
 
And when I’m checking 587
 
> # telnet smtp.gmail.com 587
Trying 64.233.167.109...
Connected to gmail-smtp-msa.l.google.com.
Escape character is '^]'.
220 smtp.gmail.com ESMTP mc4sm2794148wic.6 – gsmtp
 
 
I suppose I should change smtp port from 25 to 587. So I’ve changed **master.cf** to open 587 port (and 465 just in case):
 
>  
==========================================================================
# service type  private unpriv  chroot  wakeup  maxproc command + args
#               (yes)   (yes)   (yes)   (never) (100)
# ==========================================================================
smtp      inet  n       -       -       -       -       smtpd
submission inet n       -       -       -       -       smtpd
  -o smtpd_tls_security_level=encrypt
  -o smtpd_sasl_auth_enable=yes
  -o smtpd_client_restrictions=permit_sasl_authenticated,reject
#  -o milter_macro_daemon_name=ORIGINATING
smtps     inet  n       -       -       -       -       smtpd
  -o smtpd_tls_wrappermode=yes
  -o smtpd_sasl_auth_enable=yes
  -o smtpd_client_restrictions=permit_sasl_authenticated,reject
#  -o milter_macro_daemon_name=ORIGINATING
#628      inet  n       -       -       -       -       qmqpd
pickup    fifo  n       -       -       60      1       pickup
cleanup   unix  n       -       -       -       0       cleanup
qmgr      fifo  n       -       n       300     1       qmgr
#qmgr     fifo  n       -       -       300     1       oqmgr
tlsmgr    unix  -       -       -       1000?   1       tlsmgr
rewrite   unix  -       -       -       -       -       trivial-rewrite
bounce    unix  -       -       -       -       0       bounce
defer     unix  -       -       -       -       0       bounce
trace     unix  -       -       -       -       0       bounce
verify    unix  -       -       -       -       1       verify
flush     unix  n       -       -       1000?   0       flush
proxymap  unix  -       -       n       -       -       proxymap
proxywrite unix -       -       n       -       1       proxymap
smtp      unix  -       -       -       -       -       smtp
# When relaying mail as backup MX, disable fallback_relay to avoid MX loops
relay     unix  -       -       -       -       -       smtp
                -o smtp_fallback_relay=
#       -o smtp_helo_timeout=5 -o smtp_connect_timeout=5
showq     unix  n       -       -       -       -       showq
error     unix  -       -       -       -       -       error
retry     unix  -       -       -       -       -       error
local     unix  -       n       n       -       -       local
virtual   unix  -       n       n       -       -       virtual
lmtp      unix  -       -       -       -       -       lmtp
anvil     unix  -       -       -       -       1       anvil
scache    unix  -       -       -       -       1       scache
#
# ====================================================================
# Interfaces to non-Postfix software. Be sure to examine the manual
# pages of the non-Postfix software to find out what options it wants.
#
# Many of the following services use the Postfix pipe(8) delivery
# agent.  See the pipe(8) man page for information about ${recipient}
# and other message envelope options.
# ====================================================================
#
# maildrop. See the Postfix MAILDROP_README file for details.
# Also specify in main.cf: maildrop_destination_recipient_limit=1
#
maildrop  unix  -       n       n       -       -       pipe
  flags=DRhu user=vmail argv=/usr/bin/maildrop -d ${recipient}
#
# See the Postfix UUCP_README file for configuration details.
#
uucp      unix  -       n       n       -       -       pipe
  flags=Fqhu user=uucp argv=uux -r -n -z -a$sender - $nexthop!rmail ($recipient)
#
# Other external delivery methods.
#
ifmail    unix  -       n       n       -       -       pipe
  flags=F user=ftn argv=/usr/lib/ifmail/ifmail -r $nexthop ($recipient)
bsmtp     unix  -       n       n       -       -       pipe
  flags=Fq. user=bsmtp argv=/usr/lib/bsmtp/bsmtp -t$nexthop -f$sender $recipient
scalemail-backend unix                -              n             n             -              2             pipe
  flags=R user=scalemail argv=/usr/lib/scalemail/bin/scalemail-store ${nexthop} ${user} ${extension}
mailman   unix  -       n       n       -       -       pipe
  flags=FR user=list argv=/usr/lib/mailman/bin/postfix-to-mailman.py
  ${nexthop} ${user}
 
 
Imho **main.cf** is ok, so I didn’t changed anything, here it is:  
 
> smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no
 
# appending .domain is the MUA's job.
append_dot_mydomain = no
 
# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h
maximal_queue_lifetine = 1d
minimal_backoff_time = 1000s
maximal_backoff_time = 8000s
smtpd_recipeint_limit = 16
smtpd_soft_errors_limit = 3
smtpd_hard_error_limit = 12
 
readme_directory = no
 
myhostname = itsmydomain
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = itsmydomain.com, itsmydomain, localhost.localdomain, localhost
relayhost =
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
mynetworks_style = host
 
# TLS parameters
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache 
 
 
 
To check if ports are proper open, I’ve done this:
 
> :~# nmap -sT -O localhost
21/tcp   open  ftp
22/tcp   open  ssh
25/tcp   open  smtp
80/tcp   open  http
110/tcp  open  pop3
143/tcp  open  imap
465/tcp  open  smtps
587/tcp  open  submission
3306/tcp open  mysql
8000/tcp open  http-alt
9102/tcp open  jetdirect
 
 
And this:
 
> :~# telnet localhost 587
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
220 itsmydomain ESMTP Postfix (Ubuntu)
ehlo localhost
250-itsmydomain
250-PIPELINING
250-SIZE 10240000
250-VRFY
250-ETRN
250-STARTTLS
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN
 
Then I’ve said PHP to use port 587 for sending emails, I’ve done it in /etc/php5/apache2/php.ini.
Using phpinfo() in php script gave me information that it should be ok:

> 
[TABLE="width: 600"]
[TR]
[TD]sendmail_from[/TD]
[TD]*no value*[/TD]
[TD]*no value*[/TD]
[/TR]
[TR]
[TD]sendmail_path[/TD]
[TD]/usr/sbin/sendmail -t -i[/TD]
[TD]/usr/sbin/sendmail -t -i[/TD]
[/TR]
[TR]
[TD]serialize_precision[/TD]
[TD]100[/TD]
[TD]100[/TD]
[/TR]
[TR]
[TD]short_open_tag[/TD]
[TD]On[/TD]
[TD]On[/TD]
[/TR]
[TR]
[TD]SMTP[/TD]
[TD]localhost[/TD]
[TD]localhost[/TD]
[/TR]
[TR]
[TD]smtp_port[/TD]
[TD]587[/TD]
[TD]587[/TD]
[/TR]
[/TABLE]
 
 

After all of this using mail() in PHP still using port 25 and postfix don’t sending emails via port 587:
 
> Jul 30 18:43:50 itsmydomain postfix/pickup[7404]: D7D033000865: uid=33 from=<www-data>
Jul 30 18:43:50 itsmydomain postfix/cleanup[7414]: D7D033000865: message-id=<20150730174350.D7D033000865@itsmydomain>
Jul 30 18:43:50 itsmydomain postfix/qmgr[7403]: D7D033000865: from=<www-data@itsmydomain.com>, size=895, nrcpt=1 (queue active)
Jul 30 18:44:21 itsmydomain postfix/smtp[7416]: connect to mx13.o2.pl[193.17.41.15]:25: Connection timed out
Jul 30 18:44:51 itsmydomain postfix/smtp[7416]: connect to mx4.o2.pl[193.17.41.44]:25: Connection timed out
Jul 30 18:45:21 itsmydomain postfix/smtp[7416]: connect to mx9.o2.pl[193.17.41.123]:25: Connection timed out
Jul 30 18:45:51 itsmydomain postfix/smtp[7416]: connect to mx7.o2.pl[193.17.41.47]:25: Connection timed out
Jul 30 18:46:21 itsmydomain postfix/smtp[7416]: connect to mx8.o2.pl[193.17.41.48]:25: Connection timed out
Jul 30 18:46:21 itsmydomain postfix/smtp[7416]: D7D033000865: to=<another_tester@o2.pl>, relay=none, delay=150, delays=0.04/0/150/0, dsn=4.4.1, status=deferred (connect to mx8.o2.pl[193.17.41.48]:25: Connection timed out)  
 
 
What I’m doing wrong? Please help me, I've lost 3 days to solve that and I've achieved nothing :(

---

### Post by SeijiSensei on 2015-08-03
You need to ask your ISP what server you can use to relay outbound mail.  Then set the server and port number following the advice here: [http://stackoverflow.com/questions/5913149/change-smtp-port-from-25-to-587](http://stackoverflow.com/questions/5913149/change-smtp-port-from-25-to-587)

PHP is using port 587 to communicate with the local copy of Postfix running on your server.  Postfix then tries to relay that message to its recipient by sending it to the remote server's port 25.  There isn't anything you can do to change that behavior.  You need to find out if your ISP has a relay server you can use.

---

### Post by TopCoder01 on 2015-08-22
OP, 

 I'm not sure if "Itsmydomain.com" is really your domain or you just red-acted it in your post, but if it is,  it doesn't show your mail ports as open for incoming mail as seen here: [T]("https://www.unlocktheinbox.com/portscan/tcp/itsmydomain.com/")[CP Port Scan]("http://www.unlocktheinbox.com/portscan/tcp/itsmydomain.com/")

I know certain ISP block port 25 (Comcast, U-verse) 
[COLOR=#696969][FONT=Helvetica]
You can see the ports comcast blocks here

[/FONT][/COLOR]http://customer.xfinity.com/help-and-support/internet/list-of-blocked-ports/

[COLOR=#696969][FONT=Helvetica]So if you're running the server off your home pc internet connection, theirs a good chance its blocked.

If you're able to send email by any means - you can send one to [EMAIL="mailtest@unlocktheinbox.com"]mailtest@unlocktheinbox.com[/EMAIL] and it does a complete analysis of all your mail ports and auto-responds - I believe the first analysis is free, after that you'll need to sign up to see the full results.

[/FONT][/COLOR]Other Email Tools: [Mailtester]("https://www.unlocktheinbox.com/mail-tester/") | [SPF Wizard]("https://www.unlocktheinbox.com/spfwizard/") | [DMARC Wizard]("https://www.unlocktheinbox.com/dmarcwizard/") | [DKIM Wizard]("https://www.unlocktheinbox.com/dkimwizard/") | [Email Identifier]("https://www.unlocktheinbox.com/emailidentifieralignments/")[COLOR=#696969][FONT=Helvetica]

[/FONT][/COLOR]

---

