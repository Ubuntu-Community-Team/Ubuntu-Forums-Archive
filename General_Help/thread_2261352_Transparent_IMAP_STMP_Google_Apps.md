---
title: "Transparent IMAP STMP Google Apps"
date: 2015-01-18
forum: General Help
---

### Post by richard102 on 2015-01-18
Hi All

I wonder if anyone has any experience or can give me some advice on the following:

I use Google apps in china, which as of 2015 is completely blocked by the great firewall for both IMAP and SMTP. I wish to implement a IMAP and STMP proxy on an ubuntu server I have outside china to allow access for third party imap and stmp clients (e.g. thunderbird / mobile mail apps e.t.c).

All I want really is the most lightweight reliable proxy for IMAP & SMTP that is easy to setup and is supported on Ubuntu (14.04 LTS currently)? I am not sure if I want the proxy to be transparent or not (would that not still be blocked)?

I know I can (and do) also use solutions like VPNs, SSH tunnels to access these services. But for the sake of a simplicity I would like to go down the route described above. all settings should be the same when setting up mail in an app just the DNS address of the IMAP / SMTP server would be different.


Thanks in advice - Rich

---

### Post by SeijiSensei on 2015-01-18
Perhaps you can explain the problem a little more.  Are you trying to connect to SMTP/IMAP servers outside China?  Does China block all traffic on ports 25 and 143 or just to certain services like GMail?  If they block all outbound traffic on those ports (and others like 465 and 997), you won't be able to use the default ports in the email client.  You'll have to use custom high ports (>1023) instead.

You could run a simple TCP proxy on the Ubuntu server like [tcproxy](http://code.google.com/p/tcproxy/) and bind it to a high port like 14443 that isn't blocked.  Set the proxy's destination to the IP and port of the server you need to access.  Then a connection to yourserver:14443 would be relayed to imap_server:143.

However I would certainly recommend using a simple [point-to-point OpenVPN tunnel]("http://openvpn.net/static.html") instead.

---

### Post by richard102 on 2015-01-18
Hi, yes sorry I'll try explain in more detail. 

Firstly I should note that I do not want to do transparent proxying. That was a mistake in the post title.
Secondly I have more or less sorted the IMAP side of the problem. See the explanation below any who come after me:
In answer to your question I believe the firewall is blocking all IP's of googles IMAP and SMTP servers. They wont be blocking any ports in connection to my server - hence why I want to setup the proxy there.

I am now a wading though setting up an SMTP proxy. I am trying to use [proxSMTP]("http://thewalter.net/stef/software/proxsmtp/") to do this but am having trouble. So far I have installed it:
```
sudo apt-get install proxsmtp
```

Although I am not sure I chose the right options. So far my config file in */etc/proxsmtp.conf* reads:
```

Header: ""
Listen: 10025
OutAddress: smtp.gmail.com
user: username

```

But that's as far as I have got. I think the problem lies in the need to forward mails using SSL to googles servers. Any advise on this would be welcome?

I will look at the tcporxy solution you have offered which might be the way to go as it is agnostic of a lot of the problems (being lower down the network stack). However I think it might be abused by others as it offers no filtering options.



**IMAP**
Followed this guide: [http://www.dataparadis.net/osp/gnu-linux-server/proxy-server/gmail-imap-proxy-imapproxy-perdition/](http://www.dataparadis.net/osp/gnu-linux-server/proxy-server/gmail-imap-proxy-imapproxy-perdition/)

Installed [perdition]("http://horms.net/projects/perdition/")
```
sudo apt-get install perdition
```

Set perdition to only use IMAP4S
```
*sudo vim /etc/default/perdition* 
```

```

RUN_PERDITION=yes 
POP3=no 
POP3_FLAGS= 
POP3S=no 
POP3S_FLAGS= 
IMAP4=no 
IMAP4_FLAGS= 
IMAP4S=yes 
IMAP4S_FLAGS= 
MANAGESIEVE=no
MANAGESIEVE_FLAGS=

```

Set config for perdition
```
sudo /etc/perdition/perdition.conf
```

```

listen_port 110
protocol IMAP4S
outgoing_port 993
outgoing_server  imap.gmail.com
ssl_mode ssl_outgoing
ssl_ca_file /usr/share/ca-certificates/mozilla/Equifax_Secure_CA.crt

```

Added iptables rule
```

-A INPUT -m tcp -p tcp --dport 143 -j ACCEPT

```

**Note: **the connection to the proxy is unencrypted. It would be a good idea to set up SSL certs to improve this. It would also be a good idea to add some filtering options to make sure only connections related to your domain are allowed.

---

### Post by SeijiSensei on 2015-01-19
> **richard102 said:**
> I will look at the tcporxy solution you have offered which might be the way to go as it is agnostic of a lot of the problems (being lower down the network stack). However I think it might be abused by others as it offers no filtering options.

Just add some iptables rules to the firewall on the server.  Block all connections except from IPs you trust.

---

### Post by richard102 on 2015-01-19
IP filtering is not an option. The people using this will be out and about often using mobile/wifi networks that use dynamic IPs so IP filtering will not work.

---

### Post by SeijiSensei on 2015-01-20
How about running a webmail server like Squirrelmail or Roundcube?  Then you could use HTTPS to encrypt the connection, and it would not expose the ports. Of course, that won't work with regular clients like Thunderbird.

Otherwise I think you'll just have to leave the ports open and rely on authentication to limit access to valid users.

---

### Post by richard102 on 2015-01-21
I would like to try and use [ProxSMTP]("http://thewalter.net/stef/software/proxsmtp/") to forward the SMTP traffic to Google's servers. I am having some trouble setting this up however. Do you have any know if this solution will work with Google's SSL traffic?

You can see how far I am with my config file in my first post. Do you know what other information is needed to get this to work?

Cheers - Richard

---

### Post by SeijiSensei on 2015-01-21
From reading the man page and the project description, I don't see any way to tell proxsmtp to use SSL to communicate with Google.  It sounds like it expects to forward plain-text SMTP to another server's port 25.  If it could use SSL, the configuration file would probably include other items like the location of certificates.

For outbound SMTP forwarding you could just use a regular mail server like sendmail or Postfix configured to forward all the mail it receives to Google as the "smart host."  Both those programs would handle the SSL issue for you automatically.  You would also have greater control over who can send mail through the server.  Here is the extensive list of options for Postfix: [http://www.postfix.org/SMTPD_ACCESS_README.html](http://www.postfix.org/SMTPD_ACCESS_README.html).

---

