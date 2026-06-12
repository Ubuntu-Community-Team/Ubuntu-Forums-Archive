---
title: "problem with public ports"
date: 2007-02-06
forum: General Help
---

### Post by kfaber on 2007-02-06
Here's the problem;

I'm installed apache2 and oidentd on a fresh install of 6.06 behind a di-604 router.  the box is dmz on the router.  when i nmap localhost ports 80 and 113 are open.  when i nmap my ip or do a portscan from a website the ports show closed.  when i open firestarter it shows the ports are being blocked, but i don't keep firestarter running.  so obviously the connections are coming through to the box, but for some reason its not responding.  any help would be appreciated, this is driving me insane!

---

### Post by Gannin on 2007-02-07
Just so you know, even when you close Firestarter, it keeps running in the background.  It usually starts running when your computer obtains its IP address.  Also, some ISPs automatically block those ports.

---

### Post by kfaber on 2007-02-12
Ok, I found out that apache wasn't working because my isp blocks port 80, which is super gay , but at least I know.  The oidentd I still can't get to work though, the port is definitely open, so its not a router issue.

I did a tcpdump in one terminal and then i ssh'ed to a box on a totally different network and did a 'telnet <my-ip> auth'
tcpdump shows this..
01:26:37.261433 IP oblivion.quadspeedi.net.4401 > 192.168.0.100.auth: S 2129120688:2129120688(0) win 16384 <mss 1460,nop,wscale 0,nop,nop,timestamp 3380772936 0>
01:26:37.261505 IP 192.168.0.100.auth > oblivion.quadspeedi.net.4401: S 2863901334:2863901334(0) ack 2129120689 win 5840 <mss 1460>
01:26:37.297728 IP oblivion.quadspeedi.net.4401 > 192.168.0.100.auth: . ack 1 win 17520

so from this other box on the internet after i telnet to the auth port I type in ' 113,4401 '
and it returns:

[kris@oblivion ~/]$ telnet 24.235.36.199 auth
Trying 24.235.36.199...
Connected to dhcp-0-f-3d-4f-c5-71.cpe.cabletv.on.ca.
Escape character is '^]'.
113,4401
113 , 4401 : USERID : UNIX : nobody
Connection closed by foreign host.

[oblivion.quadspeedi.net - 06:26:57 #40]


meanwhile, the oidentd client is running as user 'nobody' but i am 'kris' on the box, and its still not returning any kind of reply to irc servers..

i'm confused, please help!

---

