---
title: "Installed postfix to new server, cannot connect from remote client"
date: 2016-02-25
forum: General Help
---

### Post by marc-britten on 2016-02-25
Hi,

I'm playing around setting up a personal server for a domain I own - setup  a Virtual server running 12.04.  Its been a number of years since i've setup something like this but I've been fumbling through it fairly well.

Installed postfix and dovecot 

dovecot is working, I can connect with clients and even copied in some backed up emails, every client sees the changes.

postfix receives mails sent from remote servers (gmail.com address and I received an automated email from a service)  however I cannot get clients to conntect via SMTP to send emails (like not even connect let alone any possible configuration issue).


telnet into the various ports (25, 587, 465) on the server itself works fine (get all the right responses, etc).  trying it from home times out, no connection.  This is on my PC, tablet and phone.  The PC has a VPN connection so I can try from the same IP as the other devices or a different one out of the New York area.  Doesn't make a difference.

The devices can connect to another setup I have access to without issue, so its not on the house side.

Not sure what to look at.

---

### Post by newbie-user on 2016-02-26
By default, postfix is configured to allow smtp access to the server itself. You can change that by setting postfix for SASL to authenticate remote clients and/or setting up a trusted network for which postfix will serve as a relay. You can learn more here: [http://www.postfix.org/SMTPD_ACCESS_README.html]("http://www.postfix.org/SMTPD_ACCESS_README.html")

---

### Post by marc-britten on 2016-02-26
I forgot to add SASL works.  If I turn off requiring encryption for one of the secure ports ([COLOR=#333333][FONT=UbuntuMono]smtp_tls_security_level = may) [/FONT][/COLOR]I can even authenticate manually from the localhost.

I used [https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix) as the guide for getting setup.

The documentation for smtpd_client_restrictions indicates it defaults to allow all.  

The problem is that as far as I can tell the system isn't even listening to those ports, however in main.cf inet_interfaces=all and netstat shows it bound correctly

tcp        0      0 0.0.0.0:25              0.0.0.0:*               LISTEN      16285/master
tcp        0      0 0.0.0.0:587             0.0.0.0:*               LISTEN      16285/master
tcp        0      0 0.0.0.0:465             0.0.0.0:*               LISTEN      16285/master
tcp6       0      0 :::25                   :::*                    LISTEN      16285/master
tcp6       0      0 :::587                  :::*                    LISTEN      16285/master
tcp6       0      0 :::465                  :::*                    LISTEN      16285/master

Edit: more info
telnet session from PC
Microsoft Telnet> open 104.153.210.198 587
Connecting To 104.153.210.198...Could not open connection to the host, on port 587: Connect failed
Microsoft Telnet>



Telnet session from server
root@server:/etc/postfix# telnet 104.153.210.198 587
Trying 104.153.210.198...
Connected to 104.153.210.198.
Escape character is '^]'.
220 server.bai-llc.com ESMTP Postfix (Ubuntu)


the VPS company confirmed they're not filtering anything and even double check to make sure there wasn't a default in Ubuntu causing issues.

---

### Post by SeijiSensei on 2016-02-27
I can connect to all three of those ports on 104.153.210.198 using telnet from my server at Linode.

Perhaps the ISP that provides service to your home is blocking those connections.  Many ISPs block connections to remote port 25, though blocking 587 and 465 is much less common.

---

### Post by marc-britten on 2016-02-28
Thanks,

I just confirmed with a website checker that those ports are open too (at least I'm not going insane).  I'll check with AT&T and look at my firewall,etc. 

I didn't think it could be me because I'm literally just moving the server to something I control, it worked with a different service without issue.  Maybe AT&T blacklisted this IP block for spam reasons.

---

### Post by SeijiSensei on 2016-02-28
No, most ISP block outbound SMTP connections over residential services.  This was a result of the enormous spread of spambot Windows machines that were taken over by malware over the past decade.  Try running this:
```
telnet gmail-smtp-in.l.google.com 25
```
Can you connect?  How about if you replace 25 with 587 or 465?  Any better?  If none of those connect, you're being blocked by AT&T.

Some ISPs won't be very cooperative about this either, because the Terms of Service you agreed to when you signed up for the account usually has a "no-servers" clause.  

You might consider creating a point-to-point tunnel with OpenVPN as described [here](http://openvpn.net/static.html).  That will let you connect to your remote server without any interference.

---

