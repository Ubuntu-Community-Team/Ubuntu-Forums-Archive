---
title: "Sender address rejected: need fully-qualified address"
date: 2015-11-03
forum: General Help
---

### Post by sindhu3 on 2015-11-03
nagios is not sending alerts to particular email address. The error in mail.log is postfix error

> 
Nov  3 11:07:30 nagios-2015 postfix/smtp[1568]: 174B942F2E:  to=<alerts911@website.com>,  relay=smtp17.msoutlookonline.net[64.78.22.100]:25, delay=0.75,  delays=0.01/
0.39/0.26/0.1, dsn=5.5.2, status=bounced (host  smtp17.msoutlookonline.net[64.78.22.100] said: 504 5.5.2  <nagios@ip-10-0-10-149>: Sender address rejected: need fully-qualified address (in reply to RCPT TO command))

---

### Post by SeijiSensei on 2015-11-03
"nagios@ip-10-0-10-149" doesn't end with a top-level domain suffix like .com.  If you're trying to send mail to an IP address, you need to enclose it in brackets like this 
```
nagios@[10.0.10.149]
```

---

### Post by efflandt on 2015-11-03
And even that would likely be rejected by most smtp servers, since it is a private IP not reachable from the Internet (unless sending main locally internally and your postfix server is configure to handle it). So you likely need a sender address that at least appears to be valid, preferably that actually works.

It has been years since I used postfix, but I had the server configured with FQDN of a noip dynamic DNS name (at least to my LAN IPs in /etc/hosts) and also specified that FQDN in **main.cf** under **myhostname =** (noip name that publicly resolved to my public IP). So mail that went out had a valid sender address that could actually reach me on that server from the Internet. Although, I had to relay mail through my ISP's relay because many MX servers would reject mail from what they perceived to be dynamic IP addresses from reverse lookup, even though my postfix server identified itself by a name that resolved to it.

---

### Post by SeijiSensei on 2015-11-03
> **efflandt said:**
> And even that would likely be rejected by most smtp servers, since it is a private IP not reachable from the Internet (unless sending main locally internally and your postfix server is configure to handle it).
I was assuming that the public server knows how to route packets for the 10.0.10.0/24 network, presumably the network behind it. And, yes, if Postfix is accepting mail for 10.0.10.149, it would need to have [10.0.10.149] as an entry in the "mydestination" directive of the main.cf configuration file.

---

### Post by sindhu3 on 2015-11-04
i changed myhostname parameter to [10.0.10.149] and 10.0.10.149 error was bad parameter.

ubuntu@nagios-2015:~$ sudo service postfix restart
 * Stopping Postfix Mail Transport Agent postfix                                postmulti: warning: valid_hostname: invalid character 91(decimal): [10.0.10.149]
postmulti: fatal: file /etc/postfix/main.cf: parameter myhostname: bad parameter value: [10.0.10.149]
                                                                         [ OK ]
 * Starting Postfix Mail Transport Agent postfix                                postmulti: warning: valid_hostname: invalid character 91(decimal): [10.0.10.149]
postmulti: fatal: file /etc/postfix/main.cf: parameter myhostname: bad parameter value: [10.0.10.149]
                                                                         [ OK ]

ubuntu@nagios-2015:~$ sudo service postfix restart
 * Stopping Postfix Mail Transport Agent postfix                                postmulti: warning: valid_hostname: numeric hostname: 10.0.10.149
postmulti: fatal: file /etc/postfix/main.cf: parameter myhostname: bad parameter value: 10.0.10.149

then i gave actual hostname and restarted postfix.
still have mail error.
Nov  4 16:24:10 nagios-2015 postfix/smtp[7088]: 11D1E42AC8: to=<alerts911@website.com>, relay=smtp17.msoutlookonline.net[64.78.22.100]:25, delay=0.53, delays=0.01/0/0.27/0.24, dsn=5.5.2, status=bounced (host smtp17.msoutlookonline.net[64.78.22.100] said: 504 5.5.2 <ubuntu@nagios-2015>: Sender address rejected: need fully-qualified address (in reply to RCPT TO command))

```
ubuntu@nagios-2015:~$ cat /etc/hosts
127.0.0.1 localhost
127.0.0.1 nagios-2015
# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback

fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

Where do i have to specify FQDN?

---

### Post by SeijiSensei on 2015-11-04
As I said, it should be added to the list in *mydestination*, not myhostname.  

```
$mydestination = other_stuff, [10.0.10.149]
```

However, it seems highly unlikely that smtp17.msoutlookonline.net [64.78.22.100] is connected to the 10.0.10.0/24 network.  You cannot send packets over the public Internet to private addresses starting with 10. (or 172.16-31, or 192.168).

If that server is not configured to route traffic to 10.0.10.0/24, then you'll need to send the mail to a regular mailbox somewhere like gmail.com.

---

### Post by sindhu3 on 2015-11-09
can i give my public ip of host  here instead of private ip . will that cause any security issues?
$mydestination = other_stuff, [10.0.10.149]

---

### Post by SeijiSensei on 2015-11-09
Yes, you can, and no it will not.  If you were to advertise [email]nagios@[your.pub.ip.addr[/email]] on a web page or something like that, then it would quickly become a spam target.  

Now it's still an open question as to whether that msoutlookonline.net host will send to a bracketed IP address.  Just because something is an Internet standard doesn't mean all providers support it.  Microsoft in particular has had a history of choosing which standards it wants to support.

---

