---
title: "LiveCD -- how to run a service? (i.e., apache, sshd, etc.)"
date: 2006-11-01
forum: General Help
---

### Post by Dunhausen on 2006-11-01
I am trying to get tor working from the livecd.  I try "sudo apt-get install tor privoxy" and that all goes fine, and "ps -A" shows tor and privoxy running as services, but the tor firefox extension does not work and "nmap localhost" always reveals "631/tcp open  ipp" as the only port that is open.

```
ubuntu@ubuntu:/etc/privoxy$ /usr/sbin/privoxy
Nov 01 11:29:34 Privoxy(b7e3a6c0) Info: loading configuration file '/etc/privoxy/config':
Nov 01 11:29:34 Privoxy(b7e3a6c0) Info: Privoxy version 3.0.3
Nov 01 11:29:34 Privoxy(b7e3a6c0) Info: Program name: /usr/sbin/privoxy
Nov 01 11:29:34 Privoxy(b7e3a6c0) Info: Listening on port 8118 for local connections only[/quote]
BUT
[code]ubuntu@ubuntu:/etc/privoxy$ nmap localhost

Starting Nmap 4.03 ( http://www.insecure.org/nmap/ ) at 2006-11-01 11:29 UTC
Interesting ports on localhost (127.0.0.1):
(The 1673 ports scanned but not shown below are in state: closed)
PORT    STATE SERVICE
631/tcp open  ipp

Nmap finished: 1 IP address (1 host up) scanned in 0.201 seconds

```

:-| 

(This is for a remastered copy, btw, so hopefully if there is a solution it can be implemented in a way that would also carry over to an install.)

---

