---
title: "shorewall + clamav + p3scan"
date: 2005-07-01
forum: General Help
---

### Post by pkoufalas on 2005-07-01
G'day all.

I'm trying to set up Clam AV scanning of incoming POP3 email to my Thunderbird client; I have a standalone laptop with a 56k dialup connection to my ISP.

I firkled around for ages but can't seem to get port redirection working, which I need in order to divert incoming email to p3scan for AV checking with ClamAV (daemon). 

For the port redirection, I have put in my /etc/shorewall/rules the line

DNAT  net  fw:127.0.0.1:8110  tcp  pop3  -  !127.0.0.1

p3scan is listening on 127.0.0.1:8110, and I've confirmed that using 'lsof -i'.

I've also tried changing the pop3 match from dst port to src port (after 'tcpdump -i ppp0' showed that port 110 was associated with my remote mail server, which was sending email to a different port on my laptop's Thunderbird client.) 

I've also checked shorewall.conf, /etc/network/options and /proc/sys/net/ipv4/ip_forward and ip_dynaddr (?) to make sure that IP forwarding is enabled (and it wasn't to begin with).

I've also checked via 'ifconfig lo' that interface lo is up (it wasn't to begin with).

The output of 'shorewall show nat' shows zero packets against the redirection rule no matter what I seem to do.

I've had a look at the shorewall FAQ but that only gave me the idea to append !127.0.0.1 to the rule, which didn't help. So I also tried substituting the DHCP assigned IP address on ppp0 local into the redirection rule (in place of !127.0.0.1) but that didn't help either.

Can anyone point me in the right direction?

---

### Post by pkoufalas on 2005-07-04
I just wanted to close this thread off. I now have p3scan working with shorewall and clamav on my standalone Ubuntu Hoary 5.04 linux laptop. I originally had in my /etc/shorewall/rules

DNAT net fw:127.0.0.1:8110 tcp pop3

(or equivalently, REDIRECT net 8110 tcp pop3) but what I actually needed to have was

REDIRECT fw 8110 tcp pop3 - - - !clamav

I'm running the p3scan daemon as user clamav, and have changed uid/guid on /var/spool/p3scan and /var/run/p3scan frrom p3scan to clamav--as user p3scan I was getting permission denied when calling clamdscan. So

shorewall + clamav + p3scan

is a working configuration. Clamav + p3scan must be popular as config parameters are given in the ClamAV FAQ. Though p3scan also supports spamassassin, I'm happy enough with Thunderbird's spam filter.

[If anyone is interested there are some alternative configurations discussed on the shorewall mailing list, as I posted my question there too.]

---

### Post by xwang on 2005-07-25
[QUOTE=pkoufalas]I just wanted to close this thread off. I now have p3scan working with shorewall and clamav on my standalone Ubuntu Hoary 5.04 linux laptop. I originally had in my /etc/shorewall/rules

DNAT net fw:127.0.0.1:8110 tcp pop3

(or equivalently, REDIRECT net 8110 tcp pop3) but what I actually needed to have was

REDIRECT fw 8110 tcp pop3 - - - !clamav

I'm running the p3scan daemon as user clamav, and have changed uid/guid on /var/spool/p3scan and /var/run/p3scan frrom p3scan to clamav--as user p3scan I was getting permission denied when calling clamdscan. So

shorewall + clamav + p3scan

is a working configuration. Clamav + p3scan must be popular as config parameters are given in the ClamAV FAQ. Though p3scan also supports spamassassin, I'm happy enough with Thunderbird's spam filter.

[If anyone is interested there are some alternative configurations discussed on the shorewall mailing list, as I posted my question there too.][/QUOTE]

What about writing an how-to for newbies like me?
Xwang

---

