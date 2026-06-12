---
title: "how could i stop DDoS attack"
date: 2013-05-25
forum: General Help
---

### Post by fowzan on 2013-05-25
i am running Ubuntu 12.04. i am new to this OS. i face alot of DDoS attacks on my static IP. is there anyway i could block the attack or atleast stop it form utilizing the entire bandwidth?

---

### Post by 3rdalbum on 2013-05-25
Not from within the operating system. There are hosting providers that can deflect attacks to an extent, if you are really having a DDoS problem you could try them.

What symptoms are you experiencing? Maybe this is not really a DDoS but something harmless?

---

### Post by HiImTye on 2013-05-25
only your ISP can lessen the effects of  a DDoS/DRDoS attack. you can report the IPs attacking you to their ISPs if they are listed in thr whois info

---

### Post by VinDSL on 2013-05-25
> **fowzan said:**
> i am running Ubuntu 12.04. i am new to this OS. i face alot of DDoS attacks on my static IP. is there anyway i could block the attack or atleast stop it form utilizing the entire bandwidth?
Here's the router I'm using, in my home:  [http://www.netgear.com/business/products/security/wired-vpn-firewalls/fvs318g.aspx](http://www.netgear.com/business/products/security/wired-vpn-firewalls/fvs318g.aspx)

It provides lots of network hardening features, including hardware denial-of-service protection.


[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-25-may-2013-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-25-may-2013-1.png")[/INDENT]


Works pretty good (despite what some amateur "reviewers" say)  ;)

---

### Post by fowzan on 2013-05-26
> **HiImTye said:**
> only your ISP can lessen the effects of  a DDoS/DRDoS attack. you can report the IPs attacking you to their ISPs if they are listed in thr whois info
tracking IPs is impractical. one DDoS attack would send atleast 100+ IPs if not 1000+.
I have seen DDoS Deflate kind of  stuff which would help a bit. can someone help me set it up.

---

### Post by prodigy_ on 2013-05-26
You can't block DDoS but you can tune iptables and kernel parameters to add more resilience. Look here for some ideas:
[http://files.directadmin.com/services/all/iptables](http://files.directadmin.com/services/all/iptables)
[https://docs.indymedia.org/Sysadmin/SecurityTuning](https://docs.indymedia.org/Sysadmin/SecurityTuning)

---

### Post by fowzan on 2013-05-27
> **prodigy_ said:**
> You can't block DDoS but you can tune iptables and kernel parameters to add more resilience. Look here for some ideas:
[http://files.directadmin.com/services/all/iptables](http://files.directadmin.com/services/all/iptables)
[https://docs.indymedia.org/Sysadmin/SecurityTuning](https://docs.indymedia.org/Sysadmin/SecurityTuning)
i am a total newb at ubuntu. it would tak me ages to learn how this stuff works. could you help me set this up? i would pay if you could

---

### Post by Charlotte18 on 2013-05-27
Wouldn't it make more sense for you to use an external firewall like Sonicwall?

---

### Post by fowzan on 2013-05-28
> **Charlotte18 said:**
> Wouldn't it make more sense for you to use an external firewall like Sonicwall?
i have considered external firewalls, but they are way too expensive. and setting up those would require a professional which is out of my reach.

---

### Post by 3rdalbum on 2013-05-28
> **fowzan said:**
> i have considered external firewalls, but they are way too expensive. and setting up those would require a professional which is out of my reach.

It seems like you're an ordinary home user, yet you complain of being DDoS'ed. It sounds very unusual for an ordinary person to be DDoS'ed - it's a lot of effort and expense to DDoS somebody, so an attacker normally would go after a major website instead of a single person.

What exactly is happening to your computer, that makes you think you are being DDoS'ed?

---

### Post by fowzan on 2013-05-31
> **3rdalbum said:**
> It seems like you're an ordinary home user, yet you complain of being DDoS'ed. It sounds very unusual for an ordinary person to be DDoS'ed - it's a lot of effort and expense to DDoS somebody, so an attacker normally would go after a major website instead of a single person.

What exactly is happening to your computer, that makes you think you are being DDoS'ed?
i run a dedicated game server from my home. and thats where all the problem jumps in. i keep monitoring the network usage on my internet from time to time. it averages at 5-6mpbs. but when the ddos kicks in the bandwidth (15mbps) is completely saturated and the internet stops working.

---

### Post by lemonoid on 2013-05-31
> **VinDSL said:**
> Here's the router I'm using, in my home:  [http://www.netgear.com/business/products/security/wired-vpn-firewalls/fvs318g.aspx](http://www.netgear.com/business/products/security/wired-vpn-firewalls/fvs318g.aspx)

It provides lots of network hardening features, including hardware denial-of-service protection.

[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-25-may-2013-1%28650x520%29.png[/IMG]]("http://vindsl.com/images/vindsl-desktop-25-may-2013-1.png")[/INDENT]


Works pretty good (despite what some amateur "reviewers" say)  ;)

this is off topic and I'm sorry, because I can't provide much info on this, other than contacting your ISP like said above, but I have a question? the widget on the side of your screen, is that purely conky?

---

### Post by 3rdalbum on 2013-05-31
If it is a DDoS, there is nothing you can do without spending loads of money.

For my money though, I think you are just experiencing how much load a game server can experience at peak periods.

---

### Post by VinDSL on 2013-05-31
> **lemonoid said:**
> this is off topic and I'm sorry, because I can't provide much info on this, other than contacting your ISP like said above, but I have a question? the widget on the side of your screen, is that purely conky?
Yes, Conky.  The weather parser is called ConkyWX.

There's a HOWTO link in my sig, if you're interested...  ;)

---

