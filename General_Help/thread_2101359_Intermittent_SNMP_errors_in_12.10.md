---
title: "Intermittent SNMP errors in 12.10"
date: 2013-01-04
forum: General Help
---

### Post by Obi-Wan-YJ on 2013-01-04
I have an old RHEL3 box on my network which I monitor via SNMP from my Ubuntu server running MRTG.  I've been doing this for years with continually-updated versions of 32-bit Ubuntu, and have never had problems.

Over the long New Years weekend, I replaced my 32-bit 12.04 install with a fresh 64-bit 12.10 install.  The SNMP & MRTG configs were copied from the 12.04 install (on a separate drive, so it's still accessible).  Ever since then, I've been getting intermittent connectivity errors with SNMP to the RHEL server ("yavin").  MRTG polls every 5 minutes, and most of the time, it succeeds.  It fails at variable intervals ranging from 10 minutes to 4 hours, but probably averaging one failure every 30 minutes.  Here's the error message I'm emailed each time:

SNMP Error:
no response received
SNMPv1_Session (remote host: "yavin" [192.168.21.246].161)
                  community: "undisclosed"
                 request ID: 2110321503
                PDU bufsize: 8000 bytes
                    timeout: 5s
                    retries: 5
                    backoff: 1)
 at /usr/share/perl5/SNMP_util.pm line 492
SNMPGET Problem for ifInOctets.2 ifOutOctets.2 sysUptime sysName on undisclosed@yavin::::::v4only at /usr/bin/mrtg line 2339
2013-01-04 09:15:01: WARNING: skipping because at least the query for ifInOctets.2 on  yavin did not succeed
2013-01-04 09:15:01: WARNING: no data for ifInOctets&ifOutOctets:undisclosed@yavin. Skipping further queries for Host yavin in this round.
2013-01-04 09:15:30: ERROR: Target[yavin-eth0][_IN_] ' $target->[28]{$mode}  * 8' (warn): Use of uninitialized value in multiplication (*) at (eval 74) line 1.
2013-01-04 09:15:30: ERROR: Target[yavin-eth0][_OUT_] ' $target->[28]{$mode}  * 8' (warn): Use of uninitialized value in multiplication (*) at (eval 75) line 1.

All further queries to yavin for that round of MRTG also fail.  The SNMP line from MRTG is pretty straightforward, and works most of the time:

Target[yavin-eth0]: ifInOctets.2&ifOutOctets.2:undisclosed@yavin * 8

Logs on yavin don't show anything.  /etc/snmp/snmp.conf on the Ubuntu box contains only comments.  This worked 100% of the time before the Ubuntu 12.10 upgrade, so I don't believe it's a hardware problem.

Any ideas what's going on?

---

### Post by jonobr on 2013-01-04
Hello


Try getting a trace on the this and see if you can get it when it fails.

If you can, I would run a trace on both ends.
From command line

```
sudo tcpdump -w snmp.pcap -i any -s 1600 port 161
```

You should get both good and bad polls,

Reading
"Use of uninitialized value in multiplication"
Almost sounds as if the OID is not populated and its extracting nothing.

Again, the tcpdump may show that.

Given its working most of the time, I figure its not a config issue either

---

### Post by Obi-Wan-YJ on 2013-01-04
OK, I ran tcpdump on both servers, and both showed the same results.  Here's the first couple queries from a good run:

13:55:06.764129 IP tatooine.jedi.com.35116 > yavin.jedi.com.snmp:  C=undisclosed GetRequest(74)  interfaces.ifTable.ifEntry.ifInOctets.2 interfaces.ifTable.ifEntry.ifOutOctets.2 system.sysUpTime.0 system.sysName.0
13:55:06.768366 IP yavin.jedi.com.snmp > tatooine.jedi.com.35116:  C=undisclosed GetResponse(100)  interfaces.ifTable.ifEntry.ifInOctets.2=1422920290 interfaces.ifTable.ifEntry.ifOutOctets.2=188977680 system.sysUpTime.0=14482448 system.sysName.0="yavin.jedi.com"
13:55:06.771810 IP tatooine.jedi.com.35116 > yavin.jedi.com.snmp:  C=undisclosed GetRequest(74)  interfaces.ifTable.ifEntry.ifInOctets.3 interfaces.ifTable.ifEntry.ifOutOctets.3 system.sysUpTime.0 system.sysName.0
13:55:06.774815 IP yavin.jedi.com.snmp > tatooine.jedi.com.35116:  C=undisclosed GetResponse(100)  interfaces.ifTable.ifEntry.ifInOctets.3=117860310 interfaces.ifTable.ifEntry.ifOutOctets.3=1367914333 system.sysUpTime.0=14482449 system.sysName.0="yavin.jedi.com"

And here's the first couple queries from a bad run.  The query gets sent from the Ubuntu box five times at 5-second intervals, and the RHEL box never responds.

14:00:06.727703 IP tatooine.jedi.com.49999 > yavin.jedi.com.snmp:  C=undisclosed GetRequest(74)  interfaces.ifTable.ifEntry.ifInOctets.2 interfaces.ifTable.ifEntry.ifOutOctets.2 system.sysUpTime.0 system.sysName.0
14:00:11.732841 IP tatooine.jedi.com.49999 > yavin.jedi.com.snmp:  C=undisclosed GetRequest(74)  interfaces.ifTable.ifEntry.ifInOctets.2 interfaces.ifTable.ifEntry.ifOutOctets.2 system.sysUpTime.0 system.sysName.0

This seems to point to the RHEL box as the source of the problem, but it seems awfully coincidental that it just started during my 12.04 to 12.10 upgrade.  I still have the 12.04 root drive.  I may try booting from it to see what happens.

---

### Post by Obi-Wan-YJ on 2013-01-04
Curiouser and curiouser.  The RHEL box (yavin) is my network firewall.  The tcpdump inspired me to check the iptables logs, and it appears that every time SNMP fails, I also get a log entry saying the packet was blocked by iptables:

Jan  4 14:00:06 yavin kernel: RULE 8 -- DENY IN=eth1 OUT= MAC=00:02:a5:e9:31:da:04:4b:80:80:80:03:08:00 SRC=
192.168.225.2 DST=192.168.21.246 LEN=120 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=49999 DPT=161 LEN=10
0 

My iptables config script is non-trivial, so I'll have to do some digging to see why Rule 8 is occasionally blocking SNMP requests from the new 12.10 OS.

Thanks for pointing me in the right direction, jonobr.

---

### Post by Obi-Wan-YJ on 2013-01-05
OK, it's getting weirder.  I mentioned that yavin (the RHEL box, and destination for these SNMP queries) is my firewall as well as my DNS & DHCP server.  DNS is set to reply with the internal LAN IP when queried from the LAN, and with the external IP when queried from the Internet.  The firewall is set to only allow SNMP queries to the LAN IP, not the external IP.

Well, for some reason, the MRTG Ubuntu box on the LAN is randomly resolving yavin to either the LAN or the external IP.  When it gets the external IP, the SNMP queries fail (as they should).

This just started after the 64-bit 12.10 install.  I rebooted onto the old 32-bit 12.04 root disk last night & ran all night without a single error.  Booted back into 64-bit 12.10 this morning, and the problem popped up again.  Nothing about the DNS or DHCP setup (on yavin) has changed in months.

What would cause 12.10 to randomly resolve the wrong IP?  This shouldn't be possible with my named setup, but it obviously only happens under this new Ubuntu install.  Nslookup, host, and dig from the Ubuntu box all resolve the correct LAN IP when I run them from the command line.

The only difference I can find is that the DHCP-created resolv.conf lists the server as 127.0.0.1 under 12.04, but as 127.0.1.1 under 12.10.  Doesn't seem like that should matter, though...

---

### Post by Obi-Wan-YJ on 2013-01-05
> **Obi-Wan-YJ said:**
> Nslookup, host, and dig from the Ubuntu box all resolve the correct LAN IP when I run them from the command line.

Oops.  Not always.  In finally saw them return the wrong (external) IP for yavin... once.  Then back to the correct (internal) IP again.  I guess the problem is not SNMP-specific.

---

### Post by Obi-Wan-YJ on 2013-01-05
Wow, what a rabbit trail.  In the interest of redundancy, my DHCP server was handing out the IP's of 3 different DNS serves--itself plus two at my upstream ISP (both of which act as secondaries for my own domains).

Apparently, Ubuntu 12.04 and prior would always query the first DNS server in the list unless it was unreachable.  12.10, it appears, now distributes the load among all of the DNS servers in the list.

My internal DNS server was correctly handing out the LAN IP for yavin.  The other DNS servers, of course, only knew about the public IP for yavin.  When my U12.10 MRTG box queried my internal DNS server, it got the correct internal IP.  When it queried the external DNS servers, it got the external IP, and my SNMP queries failed.

The solution was to remove the two external DNS servers from the list handed out by DHCP.  Since my internal DNS server is also the firewall, if it's down, my various internal computers won't be able to get out to the world anyway, so no harm is done.

Problem solved.

---

### Post by Obi-Wan-YJ on 2013-01-05
With this problem out of the way, I've summarized the situation & my solution in this post on my Prairie Rim Tech blog:

[http://tech.PrairieRim.com/2013/01/snmp-dns-dhcp-and-ubuntu-1210.html](http://tech.PrairieRim.com/2013/01/snmp-dns-dhcp-and-ubuntu-1210.html)

---

### Post by jonobr on 2013-01-08
Apologies I must give for getting back so late... Busy have I been,

Interesting your findings are- 
Previously in posts I have seen , much displeasure in handing of DNS.
Weighted it should be, or round robin-
Young Padwans and older Jedi their displeasure do they show at DNS query handling.  

(Ok, switching from Yoda to regular)

interesting to see that this has been changed to a more round robin approach.
I think (open to correction) it use to go for DNS 1 a few times, then consider it offline and then go to two , slowing requests.

Anyway Thanks for posting back with the details of the fix...

Cheers

Jonobr

---

