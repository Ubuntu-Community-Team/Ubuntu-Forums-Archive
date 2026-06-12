---
title: "How incomming &amp; outgoing traffic works"
date: 2013-09-10
forum: General Help
---

### Post by Kashyap01 on 2013-09-10
Hello
I want to know how incomming & outgoing request works internally,How ports are chosen.

What happens if we close all out going port except few required once,will that impact on server or response time?

---

### Post by SeijiSensei on 2013-09-10
You should do some [reading]("http://www.tcpipguide.com/free/t_TCPIPServicesandClientServerOperation.htm") about how TCP/IP services work.  Quick answer:

1)  Port numbers are assigned by the Internet Assigned Numbers Authority.  Only root can run a program that listens on a ports < 1024.  Ports between 1024 and 65535 can be attached by ordinary users, though some have been informally assigned to well-known services.  The Squid proxy, for instance, uses 3128 by default.  Look at the file /etc/services on your system to see a list of ports and their uses.

2) When your machine communicates with a remote server, say an HTTP server on port 80, the client program chooses a random high port (>1024) that it uses as the source port for the connection.  The destination port in this case is 80.  If you want to control where users can go, you need to concentrate on the destination ports.  (In business settings, I also block all communication that uses high ports for both the source and destination.  Often these are connections to streaming media, torrents, or other things you might not want available in the workplace.)

As for performance, I manage gateway routers with hundreds of iptables rules.  Whatever effect they might have on performance is miniscule.

---

### Post by Kashyap01 on 2013-09-11
Thanks for your help.

Can you please give some idea,basically I want to block all outgoing request accept 80,443 & other whichever required, but problem is that I can see many lots of request going out from high numbers port(>30000).If we block this all outgoing port then what will happen to out going traffic , will it impact on performance?

---

### Post by SeijiSensei on 2013-09-11
If this is a machine sitting between your local network and the Internet, you could block access to all remote services except HTTP and HTTPS with rules like this:

```
/sbin/iptables -A INPUT -i eth1 -p tcp --dport 80 -j ACCEPT
/sbin/iptables -A INPUT -i eth1 -p tcp --dport 443 -j ACCEPT
/sbin/iptables -A INPUT -i eth1 -j DENY

```

These are INPUT rules that are attached to the inward-facing interface ("eth1" in this case).  The rules allow HTTP and HTTPS traffic arriving on that interface but block everything else.

In general, firewalls should block by default with only the specific services you need to allow permitted.

As I said before, and you have confirmed empirically, the outgoing traffic uses a randomly-chosen high port.  You want to block on the destination port; ignore the source ports entirely.

---

### Post by Kashyap01 on 2013-09-11
I already blocked incoming request but wanted to block outgoing request as well,This is for server ,so just consern if we block most of the outgoing ports then will it make any delay in responding ? & what will be the best approach to to block outgoing request.

---

### Post by Lars Noodén on 2013-09-11
You might need to allow outgoing connections for DNS and NTP at the least.  There might be more depending on your set up.  At the beginning you should enable logging of anything you block just to be sure you are not missing something crucial.  Later after things are settled you can reduce or turn off the packet logging.  Also, this kind of lock down might be applicable to a server that is in production (unchanging) but is unlikely to be suitable for a home desktop.  So the rules have to match the usage.

---

### Post by The Cog on 2013-09-11
Whan a client connects to a server, the client (almost) always chooses a random high number for its own port, but has to use the well-know low port number for the server because that is the port we know the server is listening on. So for instance, a connection to a web server might have a source port any number > 1024, but will have a destination port of 80. So for outgoing connections, you can only afford to worry about the destination (service) port number. If you try to block outgoing connection attemps based on the source port, you will end up causing connections to time out for no apparent reason.

To block outgoing connections, I would probably use the following rules. First, block outgoing packets by default:
[COLOR=#0000cd][FONT=Courier New]**iptables -P OUTPUT DROP**[/FONT][/COLOR]
Then allow packets on any connections that have already been allowed by other firewall rules (including accepted inoming connections):
[COLOR=#0000cd][FONT=Courier New]**iptables -A OUTPUT -m state --state ESTABLISHED -j ACCEPT**[/FONT][/COLOR]
Then allow the server to talk to itself (always needed):
[COLOR=#0000cd]**[FONT=courier new]iptables -A OUTPUT -o lo -j ACCEPT[/FONT]**[/COLOR]
Then just allow the new connections that you want the server to make. 
For instance, this allows new NTP name lookup connections. We ignore the (random) source port number:
[COLOR=#0000cd][FONT=Courier New]**iptables -A OUTPUT -p udp --dport 53 -m state --state NEW -j ACCEPT**[/FONT][/COLOR]
As Lars Nooden points out, you may also want to allow outgoing NTP connections but off the top of my head I can't remember if that is TCP or UDP.

---

### Post by Lars Noodén on 2013-09-11
> **The Cog said:**
>  If you try to block outgoing connection attemps based on the source port, you will end up causing connections to time out for no apparent reason.

Speaking of timeouts, it is [better to use REJECT than DROP](http://www.chiark.greenend.org.uk/~peterb/network/drop-vs-reject).  The --policy option for a chain won't allow you to default to REJECT, even though [REJECT is better than DROP](http://www.chrisbrenton.org/2009/07/why-firewall-reject-rules-are-better-than-firewall-drop-rules/) in nearly all cases.  The way around it is to add a **-j REJECT** rule to the end of each chain so that no packets ever pass through the whole chain to become affected by the default policy.  

If I could I would write a patch for the kernel to allow a default policy of REJECT, but since I can't that workaround has to suffice.

---

### Post by The Cog on 2013-09-11
> Speaking of timeouts, it is better to use REJECT than DROP. 
A very good point. A REJECT will cause instant failure, and perhaps a "Connection refused" message which is rather more helpful than just "Timeout".

---

