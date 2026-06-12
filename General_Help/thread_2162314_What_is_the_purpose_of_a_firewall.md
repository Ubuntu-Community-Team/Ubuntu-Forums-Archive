---
title: "What is the purpose of a firewall?"
date: 2013-07-14
forum: General Help
---

### Post by carmen2012 on 2013-07-14
I'm just wondering, I like to use my laptop at Starbucks once in a while.  I'm running Ubuntu 13.04 with Cinnamon.

I haven't created any shared folders on my computer (mostly because I don't know how ), but would I need to run a firewall and if so why?  I know I have GUFW but it is not enabled.

Thank you

---

### Post by 3rdalbum on 2013-07-14
A firewall blocks incoming connections.

There are two services running on Ubuntu by default that listen for incoming local network connections (not from the internet, though). It's possible that a savvy attacker in the same Starbucks could open a connection to one of those services on your computer, and use an unreported security vulnerability in that service to run code on your computer.

It is very improbable, but it is possible. If you use a firewall that blocks all incoming ports to your computer, you can completely avoid such an attack.

---

### Post by claracc on 2013-07-14
I think, this sticky [http://ubuntuforums.org/showthread.php?t=1871177](http://ubuntuforums.org/showthread.php?t=1871177) can answer your question.

---

### Post by HiImTye on 2013-07-14
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]
a firewall restricts access to your computer from outside. iptables/netfilter is the firewall built into the linux kernel, and UFW, GUFW, etc are the most commonly used tools to modify iptables by people that don't know iptables (or prefer the simplicity). UFW is a good starting point, but it's a good idea to know iptables just in case, however, your mileage will vary. if you don't have Samba shares then the most common island hop is closed, however, it's always a good idea to learn about your security, especially for publically accessable devices.

---

### Post by coldraven on 2013-07-14
As I understand it the problem is not so much someone getting into your PC but rather intercepting your traffic.
The bad guy would be sitting in Starbucks and create an ad-hoc wifi network on his laptop called "Starbucks supafast" for example. Not knowing that this is a phoney network you connect to it and he can catch your login details and cookies when you sign in to your bank or social network.
That is why people use VPNs, it would "tunnel" through the phoney network and connect to the internet at a trusted location.
I am not an expert in this field so you might want to do some more research or start another thread.

---

### Post by carmen2012 on 2013-07-14
> **HiImTye said:**
>  if you don't have Samba shares then the most common island hop is closed, however, it's always a good idea to learn about your security, especially for publically accessable devices.

While I haven't created any shares myself, is there a command that I can run to see if there are any shares that exist on my system?

---

### Post by HiImTye on 2013-07-14
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]
you can see if the Samba daemon is running
```
ps -ef | grep smbd
```
@coldraven, you can sniff out unencrypted wifi traffic by using your adapter in monitor mode as well. best practices are to always use SSL when on wifi

---

### Post by carmen2012 on 2013-07-15
> **HiImTye said:**
> you can see if the Samba daemon is running
```
ps -ef | grep smbd
```
@coldraven, you can sniff out unencrypted wifi traffic by using your adapter in monitor mode as well. best practices are to always use SSL when on wifi

I ran this command from terminal and received the below response.  Could you tell me what this means?

1645  1569  0 22:36 pts/0    00:00:00 grep --color=auto smbd

---

### Post by HiImTye on 2013-07-15
> **carmen2012 said:**
> 1645  1569  0 22:36 pts/0    00:00:00 grep --color=auto smbd

that's the ```
grep
```command searching for the string you gave it (smbd). if smbd was running you would have seen entries like this```
root <some numbers> <start time> ? <cpu time> smbd -F
```as well as the entry above. if you don't want to see grep in the ps output then you would grep -v it, such as```
ps -ef | grep smbd | grep -v grep
```hope this helps!
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]

---

### Post by 1clue on 2013-07-15
Can't believe nobody said it so far, but a firewall prevents unauthorized traffic, both inbound and outbound.  People don't seem to understand that if somebody gets in, they could do all sorts of nasty things from your box, like installing their own software and attacking another box, or communicating with whatever the bad guys are using to do what they do.

Something like http or https is going to be tough to limit, but you could easily limit the types of queries that can go out without affecting your personal use of your computer.

You could also limit access of those shares based on one or two single IP addresses that you have at home, which would reduce the likelihood that the Starbucks attacker would be able to get in.

---

### Post by HiImTye on 2013-07-15
> **1clue said:**
> Can't believe nobody said it so far, but a firewall prevents unauthorized traffic, both inbound and outbound.  People don't seem to understand that if somebody gets in, they could do all sorts of nasty things from your box, like installing their own software and attacking another box, or communicating with whatever the bad guys are using to do what they do.

Something like http or https is going to be tough to limit, but you could easily limit the types of queries that can go out without affecting your personal use of your computer.

You could also limit access of those shares based on one or two single IP addresses that you have at home, which would reduce the likelihood that the Starbucks attacker would be able to get in.

that is absolutely true, but unlikely. still, you should learn how to use the firewall, and make a set of basic rules.
[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)
[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)
here are my rules
```

Status: active
Logging: on (low)
Default: deny (incoming), allow (outgoing)
New profiles: skip

To                         Action      From
--                         ------      ----
Anywhere                   ALLOW IN    127.0.0.1
137:139,445/tcp            ALLOW IN    192.168.0.0/24
137:139,445/tcp            ALLOW IN    192.168.1.0/24
137:139,445/udp            ALLOW IN    192.168.0.0/24
137:139,445/udp            ALLOW IN    192.168.1.0/24
8200/tcp                   ALLOW IN    192.168.0.0/24
8200/tcp                   ALLOW IN    192.168.1.0/24
1900/udp                   ALLOW IN    192.168.0.0/24
1900/udp                   ALLOW IN    192.168.1.0/24
6600,7990/tcp              ALLOW IN    192.168.0.0/24
6600,7990/tcp              ALLOW IN    192.168.1.0/24
3128/tcp                   ALLOW IN    192.168.0.0/24
3128/tcp                   ALLOW IN    192.168.1.0/24
8100/tcp                   ALLOW IN    192.168.0.0/24
8100/tcp                   ALLOW IN    192.168.1.0/24
62223/tcp                  ALLOW IN    Anywhere
22/tcp                     ALLOW IN    192.168.0.0/24
22/tcp                     ALLOW IN    192.168.1.0/24
8888/tcp                   ALLOW IN    Anywhere
3128                       ALLOW IN    192.168.1.0/24

``` [CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]

---

### Post by 3rdalbum on 2013-07-15
Outbound is a waste of time IMHO. Every time you want to use a new internet app (for instance, IRC or a new instant messenger) you need to change your firewall settings to allow that port. It doesn't stop an attacker communicating with their malware via standard ports like port 80. If the attacker can run code on your system, you have lost anyway - it can be very easy to socially engineer a user to get their sudo password and then silently turn off the firewall.

Best not to create such enormous hassle and annoyance for yourself, just to delay an attacker by 60 seconds.

---

### Post by 1clue on 2013-07-15
So there's no Linux, Mac, Windows, Android, TV set or anything at all that somebody could click on a bad link, and cause your home internet connection to assist in illegal activity from some remote entity?

And what uses IRC anymore?  Mostly malware, that's who.  The younger set who asks this sort of question probably doesn't even know what it stands for.

Go read this:
[https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)

Including the links.

---

### Post by 1clue on 2013-07-15
These are the known, published security holes in Ubuntu right now, as published by Canonical.

[http://www.ubuntu.com/usn/](http://www.ubuntu.com/usn/)

Are you protected?

These are categories of vulnerabilities I can think, not all of which would be on that list.  It's easier to categorize by groups of things it could be, rather than list every permutation.
[LIST=1]
[*]Known by a hostile agent?
[*]Known by a benign agent?
[*]Functional exploit(s) exists in the wild?
[*]Functional fix/patch/configuration to block the exploit is known to benign agents?
[*]Functional fix/patch/configuration is released to communities of users?
[*]Functional fix/patch/configuration is applied to all your computers?
[/LIST]


Notice that of all the possible combinations of those, the only case where you are protected is where both of the last two questions have a "yes".  You, as a user, have control over exactly one of those answers, but only if the other is a "yes" first.

The only items which would show up on the list at the top of this post are if items 4 and 5 are "yes".

These are the ways I know of where vulnerabilities are found:
[LIST=1]
[*]A benign agent discovers the problem in a clean room environment.
[*]A malicious agent discovers them through testing or real-world attack.
[*]A user discovers it by having a system become compromised.
[/LIST]

A benign agent (the developer, some distribution, some company who has their own test program) discovering a problem is pretty much controlled, and chances are a fix will be available before the problem is published.

A malicious agent discovering a problem, chances are we won't know about it until sites have been hacked.

A user issue, well that would mean the user would need to detect the problem, contact somebody who knows what to do about it and provide enough information to localize the problem.  Put yourself in this scenario and ask yourself how likely that would be.

Also notice that a good share of security exploits involve an uneducated or non-careful user who clicks on a bad link or opens a bad email.  Or downloads something which appears to be benign but is in fact malware.

This is one of the main purposes of a firewall -- not only to prevent bad guys from getting in, but to prevent bad guys from getting stuff out, or from using your hardware in a malicious way, once they do get in.  You can talk probabilities all you want, but frankly there are exploits and techniques for exploitation which would not be detected by a "stock" Ubuntu installation.

Since this thread is about what firewalls are for, why don't we restrict the discussion to facts?

***Edited for accuracy***

---

### Post by HiImTye on 2013-07-15
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]
there's also full & responsible disclosure

---

### Post by 1clue on 2013-07-15
I don't think full and responsible disclosure applies to a user forum.

Sorry for getting so grouchy about it, but it's a genuine disservice to the community to suggest that ANY linux distro (or any other operating system) needs no further security, and I used to be one of those guys right up until I got owned.

Linux's most critical vulnerability is this impenetrable conviction in the heads of its users that it's not susceptible to malware.

The firewall is important.  Penetration detection on your Ubuntu box, as well as additional security to fit your situation, are also important.  Educated users are important.

---

### Post by 3rdalbum on 2013-07-16
If you could stop malware from communicating to the outside world, that would be great. My point is that you won't stop or even seriously hinder malware from communicating with the outside world with an outgoing firewall. It will just use port 80, which you will always allow. Game over. Attacker 1, User 0.

However, the user will be constantly changing their firewall settings to allow new ports every time they want to use a new networking program, whether that be accessing a Samba share, connecting to an FTP site, using a new IM, or wanting to SSH into a different computer.

In short, you gain nothing in security, but you create a lot of work for yourself. 

I agree that Linux can be vulnerable to malware, and complacency is potentially a big problem, but outgoing firewalls are not any sort of answer. Invest your time into extra AppArmour profiles instead of an outgoing firewall.

---

### Post by 1clue on 2013-07-16
You can be fatalistic if you like, but the truth is that an outbound firewall can limit the traffic to something knowable, instead of giving your attacker carte blanche on your network once he pays the cover charge.  Make them work for what they get, there's no reason to just roll over and play dead once they get past the door.

Defense in depth is necessary for good security.  AppArmor, tripwire, an external firewall, actual rules for it, a private firewall and other protection for each box, antivirus on windows boxes, whatever you can come up with.  If you get ambitious then stick a proxy in there.

Frankly, I set my firewall up a couple years back and haven't had to touch the firewall since.  I still have to look up the docs on that sort of thing because I don't just mess with it for the sake of messing.  I think you're being pessimistic about how much maintenance is necessary.

---

