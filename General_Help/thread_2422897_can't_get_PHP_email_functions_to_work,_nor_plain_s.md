---
title: "can't get PHP email functions to work, nor plain sendmail features, on clean 18.04"
date: 2019-07-14
forum: General Help
---

### Post by ReneVeerman on 2019-07-14
i need to get PHP email functions to work on my server with minimal fuss.

for the record : i'm not interested in learning how to set up email client featues on a server, merely how to use gmail and sendmail on the local machine to send out emails.

here's the log of what i got so far :

root@albatross:/etc/php/7.2/apache2# gedit /etc/hosts
root@albatross:/etc/php/7.2/apache2# sendmailconfig
Configure sendmail with the existing /etc/mail/sendmail.conf? [Y] 
Reading configuration from /etc/mail/sendmail.conf.
Validating configuration.
Writing configuration to /etc/mail/sendmail.conf.
Writing /etc/cron.d/sendmail.
Configure sendmail with the existing /etc/mail/sendmail.mc? [Y] 
Updating sendmail environment ...
Reading configuration from /etc/mail/sendmail.conf.
Validating configuration.
Writing configuration to /etc/mail/sendmail.conf.
Writing /etc/cron.d/sendmail.
Reading configuration from /etc/mail/sendmail.conf.
Validating configuration.
Writing configuration to /etc/mail/sendmail.conf.
Writing /etc/cron.d/sendmail.
Could not open /etc/mail/databases(No such file or directory), creating it.
Reading configuration from /etc/mail/sendmail.conf.
Validating configuration.
Creating /etc/mail/databases...


Checking filesystem, this may take some time - it will not hang!
  ...   Done.
 
Checking for installed MDAs...
sasl2-bin not installed, not configuring sendmail support.


To enable sendmail SASL2 support at a later date, invoke "/usr/share/sendmail/update_auth"


 
Creating/Updating SSL(for TLS) information
Creating /etc/mail/tls/starttls.m4...
You already have sendmail certificates
 


*** *** *** WARNING *** WARNING *** WARNING *** WARNING *** *** ***


Everything you need to support STARTTLS (encrypted mail transmission
and user authentication via certificates) is installed and configured
but is *NOT* being used.


To enable sendmail to use STARTTLS, you need to:
1) Add this line to /etc/mail/sendmail.mc and optionally
   to /etc/mail/submit.mc:
  include(`/etc/mail/tls/starttls.m4')dnl
2) Run sendmailconfig
3) Restart sendmail


Checking {sendmail,submit}.mc and related databases...
Reading configuration from /etc/mail/sendmail.conf.
Validating configuration.
Creating /etc/mail/databases...
Reading configuration from /etc/mail/sendmail.conf.
Validating configuration.
Creating /etc/mail/databases...
Reading configuration from /etc/mail/sendmail.conf.
Validating configuration.
Creating /etc/mail/Makefile...
Reading configuration from /etc/mail/sendmail.conf.
Validating configuration.
Writing configuration to /etc/mail/sendmail.conf.
Writing /etc/cron.d/sendmail.
Disabling HOST statistics file(/var/lib/sendmail/host_status).
Creating /etc/mail/sendmail.cf...
Creating /etc/mail/submit.cf...
Informational: confCR_FILE file empty: /etc/mail/relay-domains
Informational: confCT_FILE file empty: /etc/mail/trusted-users
Updating /etc/mail/access...
Informational: ALIAS_FILE file empty: /etc/mail/aliases
Updating /etc/mail/aliases...
/etc/mail/aliases: 0 aliases, longest 0 bytes, 0 bytes total
Reload the running sendmail now with the new configuration? [Y] 
Reloading sendmail ...
root@albatross:/etc/php/7.2/apache2# echo "test" | sendmail -v [email]seductiveapps@gmail.com[/email]
[email]seductiveapps@gmail.com[/email]... Connecting to [127.0.0.1] via relay...
220 albatross.fritz.box ESMTP Sendmail 8.15.2/8.15.2/Debian-10; Mon, 8 Jul 2019 09:29:36 +0200; (No UCE/UBE) logging access from: localhost(OK)-localhost [127.0.0.1]
>>> EHLO albatross.fritz.box
250-albatross.fritz.box Hello localhost [127.0.0.1], pleased to meet you
250-ENHANCEDSTATUSCODES
250-PIPELINING
250-EXPN
250-VERB
250-8BITMIME
250-SIZE
250-DSN
250-ETRN
250-AUTH DIGEST-MD5 CRAM-MD5
250-DELIVERBY
250 HELP
>>> VERB
250 2.0.0 Verbose mode
>>> MAIL From:<rene@albatross.fritz.box> SIZE=5 AUTH=rene@albatross.fritz.box
250 2.1.0 <rene@albatross.fritz.box>... Sender ok
>>> RCPT To:<seductiveapps@gmail.com>
>>> DATA
250 2.1.5 <seductiveapps@gmail.com>... Recipient ok
354 Enter mail, end with "." on a line by itself
>>> .
050 <seductiveapps@gmail.com>... Connecting to gmail-smtp-in.l.google.com. via esmtp...
050 <seductiveapps@gmail.com>... Connecting to alt1.gmail-smtp-in.l.google.com. via esmtp...
050 <seductiveapps@gmail.com>... Connecting to alt2.gmail-smtp-in.l.google.com. via esmtp...
050 <seductiveapps@gmail.com>... Connecting to alt3.gmail-smtp-in.l.google.com. via esmtp...
050 <seductiveapps@gmail.com>... Connecting to alt4.gmail-smtp-in.l.google.com. via esmtp...
050 <seductiveapps@gmail.com>... Deferred: Connection timed out with alt4.gmail-smtp-in.l.google.com.
250 2.0.0 x687Ta6n012202 Message accepted for delivery
[email]seductiveapps@gmail.com[/email]... Sent (x687Ta6n012202 Message accepted for delivery)
Closing connection to [127.0.0.1]
>>> QUIT
221 2.0.0 albatross.fritz.box closing connection
root@albatross:/etc/php/7.2/apache2# cat /etc/hosts
127.0.0.1	localhost 
127.0.0.1	albatross
127.0.1.1	albatross


# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

---

### Post by HermanAB on 2019-07-15
Hmm, first of all sendmail isn't really sendmail.  It is a link to postfix.

So, go to the postfix web site and start reading: 
[http://www.postfix.org/documentation.html](http://www.postfix.org/documentation.html)

After about 2 weeks of reading, find the information about forwarding mail, install postfix from the Ubuntu repos and enable mail forwarding.

You should be good in about 3 months.

---

### Post by dragonfly41 on 2019-07-15
Another thought .. if you install [webmin ]("http://www.webmin.com/")on your remote server you can send emails via webmin

[https://subscription.packtpub.com/book/networking_and_servers/9781849515849/1/ch01lvl1sec19/enabling-webmin-to-send-an-e-mail](https://subscription.packtpub.com/book/networking_and_servers/9781849515849/1/ch01lvl1sec19/enabling-webmin-to-send-an-e-mail)

but do be aware of the security considerations since webmin is an open door into your server if your admin password is breached.

---

### Post by ReneVeerman on 2019-07-22
ok i read the postfix docs, followed all the error messages i could find, which did lead to solutions, but i'm stuck at

root@albatross:~# service postfix status
&#9679; postfix.service - Postfix Mail Transport Agent
   Loaded: loaded (/lib/systemd/system/postfix.service; enabled; vendor preset: enabled)
   Active: active (exited) since Mon 2019-07-22 14:39:59 CEST; 58min ago
  Process: 23174 ExecReload=/bin/true (code=exited, status=0/SUCCESS)
  Process: 23971 ExecStart=/bin/true (code=exited, status=0/SUCCESS)
 Main PID: 23971 (code=exited, status=0/SUCCESS)


jul 22 14:39:59 albatross systemd[1]: Starting Postfix Mail Transport Agent...
jul 22 14:39:59 albatross systemd[1]: Started Postfix Mail Transport Agent.
root@albatross:~# mailq
-Queue ID-  --Size-- ----Arrival Time---- -Sender/Recipient-------
8F0F2401F5F      265 Mon Jul 22 14:35:09  [email]root@seductiveapps.com[/email]
(connect to alt2.gmail-smtp-in.l.google.com[64.233.188.26]:25: Connection timed out)
                                         [email]seductiveapps@gmail.com[/email]


8D01B401F84      265 Mon Jul 22 14:37:19  [email]root@seductiveapps.com[/email]
(connect to alt2.gmail-smtp-in.l.google.com[64.233.188.26]:25: Connection timed out)
                                         [email]seductiveapps@gmail.com[/email]


9BBD8401F92      265 Mon Jul 22 14:45:40  [email]root@seductiveapps.com[/email]
(connect to alt2.gmail-smtp-in.l.google.com[64.233.188.26]:25: Connection timed out)
                                         [email]seductiveapps@gmail.com[/email]


E8427401F86      265 Mon Jul 22 14:40:03  [email]root@seductiveapps.com[/email]
(connect to alt2.gmail-smtp-in.l.google.com[2404:6800:4008:c06::1b]:25: Connection timed out)
                                         [email]seductiveapps@gmail.com[/email]


-- 1 Kbytes in 4 Requests.


-------------------------
i'm only interested in sending emails (from PHP and from commandline sendmail), not receiving them, so i don't think firewall issues are causing the problem listed above here.

---

### Post by SeijiSensei on 2019-07-22
Open a terminal and type
```
telnet 64.233.188.26 25
```

If it fails to connect, it's probably because your ISP blocks outbound SMTP connections to prevent spambots.

---

### Post by HermanAB on 2019-07-22
You can get around the above by using SMTPS, the secure version of SMTP on the outgoing connection.  It has a different port number 587.

Doing this, is described somewhere in the Postfix manuals.  Otherwise, you may need to upgrade your ISP account to a Small Business Account (they all have something like that), which should not cost much more and which should also give you other features, like more throughput and an IP address or two.

---

### Post by ReneVeerman on 2019-07-26
i've tried telnet to that IP address in my mailq logs (the one with connection timed out at port 25),
on both port 25 and 587,
which both won't connect using ubuntu telnet :(

and my ISP says they don't block anything.
to be sure i added port forwarding in my modem for port 25, that didn't fix it either.

i also tried adding a rule in ufw (sudo ufw allow 25),
but that didn't fix it either :(

i'm stuck, and would love some more helo..

---

### Post by ReneVeerman on 2019-07-26
i've got 2 more sets of output that might help debug this,
and i could not find anything on google using searchterms  'ubuntu smtp timed out'.

root@albatross:~# nmap -p25 64.233.188.26


Starting Nmap 7.60 ( [https://nmap.org](https://nmap.org) ) at 2019-07-26 09:59 CEST
Nmap scan report for tk-in-f26.1e100.net (64.233.188.26)
Host is up (0.26s latency).


PORT   STATE    SERVICE
25/tcp filtered smtp


Nmap done: 1 IP address (1 host up) scanned in 3.13 seconds



root@albatross:~# tcptraceroute 64.233.188.26 
Selected device enp2s0, address 192.168.178.21, port 55315 for outgoing packets
Tracing the path to 64.233.188.26 on TCP port 80 (http), 30 hops max
 1  192.168.178.1  0.625 ms  0.547 ms  0.515 ms
 2  lo0.dr14.d12.xs4all.net (194.109.5.218)  5.286 ms  5.074 ms  5.363 ms
 3  0.ae24.xr3.3d12.xs4all.net (194.109.7.125)  4.869 ms  5.197 ms  5.150 ms
 4  0.et-1-1-0.xr1.tc2.xs4all.net (194.109.5.7)  5.303 ms  6.341 ms  5.443 ms
 5  google.xs4all.net (194.109.11.2)  6.264 ms  6.090 ms  5.675 ms
 6  209.85.142.194  5.624 ms  6.203 ms  5.814 ms
 7  108.170.241.141  5.782 ms  6.247 ms  9.210 ms
 8  209.85.255.197  6.494 ms  6.799 ms  6.394 ms
 9  209.85.245.231  12.579 ms  11.820 ms  12.242 ms
10  172.253.65.166  79.741 ms  79.771 ms  79.882 ms
11  216.239.59.0  95.892 ms  95.864 ms  99.424 ms
12  209.85.247.5  105.626 ms  105.118 ms  105.380 ms
13  72.14.239.197  139.662 ms  139.573 ms  139.892 ms
14  108.170.234.21  262.340 ms  260.677 ms  260.711 ms
15  209.85.247.44  258.066 ms  257.676 ms  259.150 ms
16  209.85.253.11  262.111 ms  261.719 ms  262.153 ms
17  * * *
18  * * *
19  * * *
20  * * *

---

### Post by dragonfly41 on 2019-07-26
> [COLOR=#000000]i could not find anything on google using searchterms 'ubuntu smtp timed out'.[/COLOR]

Try using advanced search in google using their search operators ..

For example using the operator NEAR

```
ubuntu NEAR smtp timeout NEAR sendmail
```

yields various threads/clues [such as here]("https://askubuntu.com/questions/634470/cant-send-mail").

Research google search operators and patterns.

---

### Post by ReneVeerman on 2019-07-26
your link yielded no ultimate results, i wasn't even able to follow the example given, sorry.

---

### Post by SeijiSensei on 2019-07-26
The tcptraceroute scan tried to connect to port 80 on the remote host which likely isn't in use.  If I use ordinary traceroute or ping which use ICMP packets I can see the server from my desktop. Connecting with telnet from my mail server which has no outbound blocks returns
```

# telnet 64.233.188.26  25
Trying 64.233.188.26...
Connected to 64.233.188.26.
Escape character is '^]'.
220 mx.google.com ESMTP b14si19112531pgi.587 - gsmtp

```
as expected.

It's possible that your IP is in a subnet which is blocked by Google for harboring spammers.  The "filtered" result from nmap suggests this might be the reason.

---

### Post by HermanAB on 2019-07-26
Try to send a short mail manually with telnet, to see exactly where it fails.

Note that to send mail generally requires that your server is configured with DNS and Reverse DNS all working properly, otherwise your server will be ignored/greylisted/blacklisted/tarpitted/spamhaused...  There are many techniques that are used to deter spammers.

Check your IP at Spamhaus [https://www.spamhaus.org/lookup/](https://www.spamhaus.org/lookup/)

---

### Post by ReneVeerman on 2019-07-29
thanks for the tip about tcptraceroute..
an ordinary traceroute does get through! :)
but i still can't connect to port 25 on that machine..

and i checked my IP in that spamhaus.org/lookup, it's not in any of it's lists, so that's good..

root@crow:/home/rene/data1/htdocs/localhost# traceroute 64.233.188.26 25
traceroute to 64.233.188.26 (64.233.188.26), 30 hops max, 28 byte packets
 1  fritz.box (192.168.178.1)  0.646 ms  0.873 ms  1.093 ms
 2  lo0.dr14.d12.xs4all.net (194.109.5.218)  119.099 ms  119.250 ms  119.443 ms
 3  0.ae24.xr3.3d12.xs4all.net (194.109.7.125)  119.981 ms  119.536 ms  119.667 ms
 4  0.et-1-1-0.xr1.sara.xs4all.net (194.109.5.1)  120.235 ms 0.et-1-1-0.xr1.tc2.xs4all.net (194.109.5.7)  119.980 ms 0.et-7-1-0.xr1.tc2.xs4all.net (194.109.5.5)  120.333 ms
 5  google.xs4all.net (194.109.11.2)  120.796 ms  120.894 ms google.xs4all.net (194.109.11.222)  120.423 ms
 6  * * *
 7  209.85.252.244 (209.85.252.244)  106.676 ms 108.170.236.134 (108.170.236.134)  6.468 ms  5.539 ms
 8  108.170.241.140 (108.170.241.140)  6.160 ms 108.170.241.141 (108.170.241.141)  6.216 ms 108.170.241.140 (108.170.241.140)  7.034 ms
 9  209.85.255.230 (209.85.255.230)  6.999 ms 216.239.41.49 (216.239.41.49)  8.143 ms 209.85.253.113 (209.85.253.113)  6.918 ms
10  108.170.237.243 (108.170.237.243)  13.162 ms 108.170.234.119 (108.170.234.119)  13.782 ms  14.450 ms
11  172.253.65.176 (172.253.65.176)  82.152 ms 172.253.65.174 (172.253.65.174)  81.404 ms  82.054 ms
12  216.239.57.196 (216.239.57.196)  97.747 ms 216.239.58.254 (216.239.58.254)  95.406 ms 216.239.57.196 (216.239.57.196)  97.062 ms
13  209.85.143.103 (209.85.143.103)  125.711 ms  125.826 ms 72.14.234.9 (72.14.234.9)  104.933 ms
14  108.170.233.245 (108.170.233.245)  135.612 ms 209.85.241.247 (209.85.241.247)  138.604 ms 108.170.227.203 (108.170.227.203)  139.323 ms
15  209.85.249.41 (209.85.249.41)  256.095 ms  272.307 ms 209.85.249.75 (209.85.249.75)  279.740 ms
16  74.125.252.172 (74.125.252.172)  274.489 ms 209.85.251.170 (209.85.251.170)  258.495 ms 74.125.252.166 (74.125.252.166)  258.259 ms
17  74.125.252.217 (74.125.252.217)  260.745 ms 74.125.253.87 (74.125.253.87)  255.310 ms 209.85.253.11 (209.85.253.11)  259.805 ms
18  * * *
19  * * *
20  * * *
21  * * *
22  * * *
23  * * *
24  * * *
25  * * *
26  * * *
27  tk-in-f26.1e100.net (64.233.188.26)  266.329 ms  254.216 ms  256.788 ms

root@crow:/home/rene/data1/htdocs/localhost# telnet 64.233.188.26 25
Trying 64.233.188.26...
^C


results on the machine i used earlier are identical. they are on the same LAN.

---

### Post by SeijiSensei on 2019-07-29
Hmm. Well if your IP isn't blocked by Google, then I have to wonder whether what your ISP told you was correct.  Someone is blocking those port 25 connections.  Maybe the support person at your ISP didn't understand what you were asking about.

---

### Post by HermanAB on 2019-07-29
As I mentioned before, change to Secure SMTP.  It runs on a different port which usually not blocked, since it is not used by spammers, as it will identify them.

---

