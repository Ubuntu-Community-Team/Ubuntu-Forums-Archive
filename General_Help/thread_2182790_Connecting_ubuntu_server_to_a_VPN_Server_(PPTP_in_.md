---
title: "Connecting ubuntu server to a VPN Server (PPTP in windows server)"
date: 2013-10-22
forum: General Help
---

### Post by jfg2 on 2013-10-22
Hi everyone, first post.

Can't seem to find the solution for this problem, and i've tried several things i found on google.

Installed pptp-linux and configured to try to connect to a VPN Server that is running on a windows server 2003.
So that means Ubuntu is the client and the VPN server is a windows machine


The problem im getting is:

```
Connect: ppp0 <--> /dev/pts/2
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xcbdaebb9> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xcbdaebb9> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xcbdaebb9> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xcbdaebb9> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xcbdaebb9> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xcbdaebb9> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xcbdaebb9> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xcbdaebb9> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xcbdaebb9> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xcbdaebb9> <pcomp> <accomp>]
LCP: timeout sending Config-Requests
Connection terminated.
Modem hangup

```


I believe that the problem is, the client is sending packets but the server isn't replying. Hence the time out.
The solution, im not really sure.

In the pptp-linux page they have a solution for this:
```

[LIST]
[*]No GRE transmitted by PPTP Server


Symptom: GRE packets are emitted by the client, but none are returned by the server, but a tunnel from another machine on the same LAN works fine. The client is behind a NAT gateway with respect to the server.
Diagnosis: PPTP servers will not allow a connection to start from the same IP address that they perceive an active connection on already.


Solution: use alternate PPTP server IP addresses.
[/LIST]

```


but, not only im not sure what that means, i dont believe that is my case, or the solution.

Anyone familiar with this? Really could use the help :)

---

### Post by jfg2 on 2013-10-23
anyone?

---

### Post by costis on 2014-05-12
Check my thread ([http://ubuntuforums.org/showthread.php?t=2178299]("http://ubuntuforums.org/showthread.php?t=2178299")), I had the same problem. Unfortunately my school does not use OpenVPN and it seemed it was a adsl modem issue, while it was only a kernel(/module?) issue.

---

### Post by costis on 2015-02-26
I finally (lol) understood what was going on. Both "nf_conntrack_proto_gre" and "nf_conntrack_pptp" modules must be enabled in the kernel:
```

$ sudo modprobe nf_conntrack_proto_gre nf_conntrack_pptp

```

---

### Post by OmegaPhil on 2015-03-13
Thankyou for posting this - I've spent many hours here and at work debugging this, very poor for this to suddenly no longer work without any hint of what to go on. Will be interesting to see if this is an Ubuntu screwup or if Debian also breaks in this way.

---

