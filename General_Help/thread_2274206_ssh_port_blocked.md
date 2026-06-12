---
title: "ssh port blocked"
date: 2015-04-18
forum: General Help
---

### Post by apophis2 on 2015-04-18
hey all,

im very new in using ubuntu and not very skilled in programming. 

Until now i never had any problems with ssh or port forwarding (just the normal trouble) but since
i get my new notebook (schenker p505 pro 15'' core i7) by using ubuntu (14.04 lts 64 bit) everything get out 
of control.

From my laptop i can't connect by ssh in my home- or work network but vice versa it's possible.

Ping is working fine.

By typing:

```
 
usr@fourier:~$ ssh -vvvvv user@ip
OpenSSH_6.6.1, OpenSSL 1.0.1f 6 Jan 2014
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to 192.168.xxx.xx [192.168.xxx.xx] port 22.
debug1: connect to address 192.168.xxx.xx port 22: Connection refused
ssh: connect to host 192.168.xxx.xx port 22: Connection refused

```

First i disabled ufw and tried to open this port in iptables

```

sudo iptables -A OUTPUT -p tcp --sport 22 -j ACCEPT
sudo iptables -A INPUT -p tcp --dport ssh -j ACCEPT

```

But still the same error.

on a webpage i have checked if the port is really open and it's saying yes, but by typing:

```

usr@fourier:~$ sudo nmap -p 22 ip
[sudo] password for apophis: 

Starting Nmap 6.40 ( http://nmap.org ) at 2015-04-18 19:11 CEST
Nmap scan report for pcname.fritz.box (192.168.xxx.xx)
Host is up (0.080s latency).
PORT   STATE  SERVICE
22/tcp closed ssh
MAC Address: 00:C2:C6:3A:73:89 (Intel Corporate)

Nmap done: 1 IP address (1 host up) scanned in 0.75 seconds

```

Then i have checked my ssh_conf and sshd_conf file but there is nothing obviously damaged.
But as already mentioned, unfortunately i'm a beginner... 

Has somebody how i could solve this problem?

many thx in advance!

cheers,
apo

---

### Post by nerdtron on 2015-04-18
who is doing the port forwarding? a home router?

> First i disabled ufw and tried to open this port in iptables

What do you want to achieve on those iptables? If you just want to open port 22, why not use ufw for simpler syntax?

---

### Post by The Cog on 2015-04-18
From your post, I cannot work out whether you are trying to connect to your laptop or from your laptop, from home to work or from work to home, or what works and what doesn't.

On your SSH server (the one you are tryng to connect to), run the command ```
netstat -lntp
``` and you should see 0.0.0.0 port 22 listening (probably also ::22, the IPv6 port), opened by sshd. 
If so then maybe you have a firewall configuraton problem. 
If not then you have a configuration problem with sshd. 

Your "connection refused" errors and the nmap "closed" suggest that sshd might not be listening on port 22 (firewalls normally drop the packets so you don't normally get a connection refused response from them, just a timeout).

But it worries me that you are trying to connect to 192.168.x.x - this is a private (home?) address range and will not be reachable over the interenet, from work to home for instance. To do that, you would need to connect to your public IP address (assigned to your home router) and configure the router to forward the connection on to the 192.168.x.x internal address.

---

### Post by apophis2 on 2015-04-18
many thx for your replies!

@nertdtron: i have disabled ufw because allowing the ports in ufw didn't work. i thought i could determine this way where the problem comes from.

@the cog: sry of this mess. in my home network are 2 laptops connected by wlan by using a fritzbox router. in this network i can connect from laptop 2 to laptop 1 (my laptop)
without any problems (i'm running ubuntu 14.04 also on this laptop). But vice versa the error occur. And the same problem i have in my work network with static ip's. Pinging
always works from my maschine but nothing more.
in my router i have already opened the ports, i think there is not the problem.

netstat -lntp gives:

```

apophis@fourier:~$ sudo netstat -lntp
[sudo] password for apophis: 
Aktive Internetverbindungen (Nur Server)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      976/sshd        
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      6732/cupsd      
tcp        0      0 0.0.0.0:17500           0.0.0.0:*               LISTEN      2010/dropbox    
tcp        0      0 127.0.1.1:53            0.0.0.0:*               LISTEN      2144/dnsmasq    
tcp6       0      0 :::22                   :::*                    LISTEN      976/sshd        
tcp6       0      0 ::1:631                 :::*                    LISTEN      6732/cupsd      

```

i think no problem, isn't it?

any idea were this comes from? or how can i figure out where it comes from?

many thx!

cheers,
apo

---

### Post by nerdtron on 2015-04-18
> without any problems (i'm running ubuntu 14.04 also on this laptop). But  vice versa the error occur. And the same problem i have in my work  network with static ip's. Pinging
always works from my maschine but nothing more.
in my router i have already opened the ports, i think there is not the problem.


so you don't need any port forwarding? you just want to have ssh access on your local machines on your LAN?

---

### Post by apophis2 on 2015-04-18
yes, right.

---

### Post by nerdtron on 2015-04-18
1. I don't see the point of having active firewall then, since this is only local network.

2. If you really want to use a firewall, this is easy to setup on ufw.

You said ssh is having problems so you disabled ufw and switched to iptables instead. You could have caused conflicts on when you shutdown ufw and then used iptables.

I suggest the following
#disable ufw first
sudo ufw disable
# reset ufw rules
sudo ufw reset
# reboot PC to clear your iptables, (I assume you did not save you iptables entries)

On next reboot, your firewall won't be active and iptables are all cleared. Test SSH first on both machine if it's working.
If ssh works without firewall, we can proceed on activating the firewall.
#allow port 22 on ufw
sudo ufw allow ssh
# enable firewall
sudo ufw enable
Now only ssh port should be allowed on your server.

Don't mix and match iptables and ufw. Although ufw backend is still iptables, don't create iptables rules when your already have used UFW.

---

### Post by apophis2 on 2015-04-19
hey!

many thx for your answer!

i have done what you have written and then strange things happened.... 

after rebooting i couldn't login anymore and after some research i figured out that moving of .Xauthority solved the problem.
But i have still the same problem also after repeating your discription. 

Yes you were right, i have totally mixed up ufw and iptables! i'm trying to learn more about that...

Is there something like an "End-solution"? What can i check anymore?

cheers,
apo

---

### Post by The Cog on 2015-04-19
Hi apophis2, sorry for the delay in answering.
Your netstat output shows that sshd is indeed listening - the port is not really closed.

I bow to nerdtron's better familiarity with the firewall configuration. 

I just tried enabling UFW and tested - UFW does NOT reject incoming connections by default - it just drops the packet. So you should not be getting "connection refused" if the firewall is the problem, you should be getting "timeout". I am not convinced that your laptop is the one refusing the connection. I wonder if there is a second PC on that network with the same IP address, and the other one is rejecting the connection. Try shutting the laptop down and then try connecting to it. You should get "no route to host".

A final proof of whether the laptop itself is rejecting the connection would be to run
```
sudo tcpdump -np -i wlan0
``` on the PC you are trying to connect to, which will list all the incoming and outgoing packets. Post the trace here and we can explain what it means.

EDIT:
Looks like you posted while I was messing around typing this and playing with firewall rules.
I still think your firewall rules are not the problem, but I think this is the way to clear all the firewall rules, at least temporarily:
```
sudo iptables -F
sudo iptables -X
sudo iptables -P INPUT ACCEPT
sudo iptables -P OUTPUT ACCEPT
sudo iptables -P FORWARD ACCEPT
```
and to see what the current rules are, I always use
```
sudo iptables-save
```
Here is the output when the iptables filters are cleared (The date and the packet:byte counts in brackets will differ):
```
# Generated by iptables-save v1.4.21 on Sun Apr 19 13:45:00 2015
*filter
:INPUT ACCEPT [2:104]
:FORWARD ACCEPT [0:0]
:OUTPUT ACCEPT [2:104]
COMMIT
# Completed on Sun Apr 19 13:45:00 2015

```

---

### Post by apophis2 on 2015-04-19
thx for your reply :-)

this is the output of tcdump -np -i wlan0|grep myIP (because output is freaking big!) from the computer i want to connect to (My computer  (the problem computer) has the address 192.168.178.21 the other one  192.168.178.24 (where i run tcpdump)):

apophis@fourier:~$ grep 192.168.178.21 ~/Downloads/output.txt
14:43:23.727667 IP 192.168.178.21.17500 > 192.168.178.255.17500: UDP, length 104
14:43:53.722289 IP 192.168.178.21.17500 > 255.255.255.255.17500: UDP, length 104
14:43:53.724013 IP 192.168.178.21.17500 > 192.168.178.255.17500: UDP, length 104
14:44:23.827252 IP 192.168.178.21.17500 > 192.168.178.255.17500: UDP, length 104
14:44:53.829946 IP 192.168.178.21.17500 > 192.168.178.255.17500: UDP, length 104
14:45:23.832416 IP 192.168.178.21.17500 > 192.168.178.255.17500: UDP, length 104
14:45:53.937608 IP 192.168.178.21.17500 > 192.168.178.255.17500: UDP, length 104
14:46:23.940119 IP 192.168.178.21.17500 > 192.168.178.255.17500: UDP, length 104
14:46:53.942735 IP 192.168.178.21.17500 > 192.168.178.255.17500: UDP, length 104
14:47:24.047750 IP 192.168.178.21.17500 > 192.168.178.255.17500: UDP, length 104
14:47:54.050373 IP 192.168.178.21.17500 > 192.168.178.255.17500: UDP, length 104
14:48:24.155318 IP 192.168.178.21.17500 > 192.168.178.255.17500: UDP, length 104
14:48:54.158811 IP 192.168.178.21.17500 > 192.168.178.255.17500: UDP, length 104
14:49:24.161674 IP 192.168.178.21.17500 > 192.168.178.255.17500: UDP, length 104
14:49:46.891522 IP 192.168.178.21 > 224.0.0.22: igmp v3 report, 1 group record(s)
14:49:46.994716 IP 192.168.178.21.5353 > 224.0.0.251.5353: 0 [2q] PTR (QM)? _ipps._tcp.local. PTR (QM)? _ipp._tcp.local. (45)
14:49:47.097472 IP 192.168.178.21.5353 > 224.0.0.251.5353: 0 [4q] [7n] ANY (QM)? 7.4.8.4.f.7.e.f.f.f.a.1.e.d.6.3.0.0.0.0.0.0.0.0.0.0.0.0.0.8.e.f.ip6.arpa. ANY (QM)? fourier.local. ANY (QM)? 21.178.168.192.in-addr.arpa. ANY (QM)? fourier [34:de:1a:7f:48:47]._workstation._tcp.local. (320)
14:49:47.199967 IP 192.168.178.21.5353 > 224.0.0.251.5353: 0*- [0q] 2/0/0 PTR _workstation._tcp.local., PTR fourier [34:de:1a:7f:48:47]._workstation._tcp.local. (114)
14:49:47.404442 IP 192.168.178.21.5353 > 224.0.0.251.5353: 0 [4q] [7n] ANY (QM)? 7.4.8.4.f.7.e.f.f.f.a.1.e.d.6.3.0.0.0.0.0.0.0.0.0.0.0.0.0.8.e.f.ip6.arpa. ANY (QM)? fourier.local. ANY (QM)? 21.178.168.192.in-addr.arpa. ANY (QM)? fourier [34:de:1a:7f:48:47]._workstation._tcp.local. (320)
14:49:47.609640 IP 192.168.178.21.5353 > 224.0.0.251.5353: 0 [4q] [7n] ANY (QM)? 7.4.8.4.f.7.e.f.f.f.a.1.e.d.6.3.0.0.0.0.0.0.0.0.0.0.0.0.0.8.e.f.ip6.arpa. ANY (QM)? fourier.local. ANY (QM)? 21.178.168.192.in-addr.arpa. ANY (QM)? fourier [34:de:1a:7f:48:47]._workstation._tcp.local. (320)
14:49:47.814092 IP 192.168.178.21.5353 > 224.0.0.251.5353: 0*- [0q] 7/0/0 (Cache flush) PTR fourier.local., (Cache flush) A 192.168.178.21, (Cache flush) PTR fourier.local., (Cache flush) HINFO, (Cache flush) SRV fourier.local.:9 0 0, (Cache flush) TXT "", (Cache flush) AAAA fe80::36de:1aff:fe7f:4847 (296)
14:49:47.916541 IP 192.168.178.21 > 224.0.0.22: igmp v3 report, 1 group record(s)
14:49:47.917453 ARP, Request who-has 192.168.178.1 tell 192.168.178.21, length 28
14:49:48.019019 IP 192.168.178.21.5353 > 224.0.0.251.5353: 0 [2q] PTR (QM)? _ipps._tcp.local. PTR (QM)? _ipp._tcp.local. (45)
14:49:48.325858 IP 192.168.178.21.5353 > 224.0.0.251.5353: 0*- [0q] 6/0/0 PTR _workstation._tcp.local., PTR fourier [34:de:1a:7f:48:47]._workstation._tcp.local., (Cache flush) TXT "", (Cache flush) SRV fourier.local.:9 0 0, (Cache flush) AAAA fe80::36de:1aff:fe7f:4847, (Cache flush) A 192.168.178.21 (199)
14:49:49.043141 IP 192.168.178.21.5353 > 224.0.0.251.5353: 0*- [0q] 7/0/0 (Cache flush) PTR fourier.local., (Cache flush) A 192.168.178.21, (Cache flush) PTR fourier.local., (Cache flush) HINFO, (Cache flush) SRV fourier.local.:9 0 0, (Cache flush) TXT "", (Cache flush) AAAA fe80::36de:1aff:fe7f:4847 (296)
14:49:49.964639 IP 192.168.178.21.5353 > 224.0.0.251.5353: 0 [2q] PTR (QM)? _ipps._tcp.local. PTR (QM)? _ipp._tcp.local. (45)
14:49:50.476339 IP 192.168.178.21.5353 > 224.0.0.251.5353: 0*- [0q] 6/0/0 PTR _workstation._tcp.local., PTR fourier [34:de:1a:7f:48:47]._workstation._tcp.local., (Cache flush) TXT "", (Cache flush) SRV fourier.local.:9 0 0, (Cache flush) AAAA fe80::36de:1aff:fe7f:4847, (Cache flush) A 192.168.178.21 (199)
14:49:51.192643 IP 192.168.178.21.5353 > 224.0.0.251.5353: 0*- [0q] 7/0/0 (Cache flush) PTR fourier.local., (Cache flush) A 192.168.178.21, (Cache flush) PTR fourier.local., (Cache flush) HINFO, (Cache flush) SRV fourier.local.:9 0 0, (Cache flush) TXT "", (Cache flush) AAAA fe80::36de:1aff:fe7f:4847 (296)
14:49:53.959078 ARP, Request who-has 192.168.178.24 tell 192.168.178.21, length 28
14:49:53.961816 IP 192.168.178.21.54806 > 192.168.178.24.22: Flags [S], seq 1149287276, win 29200, options [mss 1460,sackOK,TS val 617800 ecr 0,nop,wscale 7], length 0
14:49:53.961902 IP 192.168.178.24.22 > 192.168.178.21.54806: Flags [R.], seq 0, ack 1149287277, win 0, length 0
14:49:54.060496 IP 192.168.178.21.5353 > 224.0.0.251.5353: 0 [2q] PTR (QM)? _ipps._tcp.local. PTR (QM)? _ipp._tcp.local. (45)
14:49:54.266462 IP 192.168.178.21.17500 > 255.255.255.255.17500: UDP, length 104
14:49:54.268157 IP 192.168.178.21.17500 > 192.168.178.255.17500: UDP, length 104
14:49:56.636165 IP 192.168.178.21.54808 > 192.168.178.24.22: Flags [S], seq 648288592, win 29200, options [mss 1460,sackOK,TS val 618493 ecr 0,nop,wscale 7], length 0
14:49:56.636244 IP 192.168.178.24.22 > 192.168.178.21.54808: Flags [R.], seq 0, ack 648288593, win 0, length 0
14:49:57.422439 IP 192.168.178.21.54809 > 192.168.178.24.22: Flags [S], seq 2952112363, win 29200, options [mss 1460,sackOK,TS val 618689 ecr 0,nop,wscale 7], length 0
14:49:57.422523 IP 192.168.178.24.22 > 192.168.178.21.54809: Flags [R.], seq 0, ack 2952112364, win 0, length 0
14:49:57.972742 IP 192.168.178.21.54810 > 192.168.178.24.22: Flags [S], seq 50094971, win 29200, options [mss 1460,sackOK,TS val 618827 ecr 0,nop,wscale 7], length 0
14:49:57.972818 IP 192.168.178.24.22 > 192.168.178.21.54810: Flags [R.], seq 0, ack 50094972, win 0, length 0
14:49:58.972513 ARP, Request who-has 192.168.178.21 tell 192.168.178.24, length 28
14:49:59.082389 ARP, Reply 192.168.178.21 is-at 34:de:1a:7f:48:47, length 28
14:50:02.047754 IP 192.168.178.21.5353 > 224.0.0.251.5353: 0 [1a] [2q] PTR (QM)? _ipps._tcp.local. PTR (QM)? _ipp._tcp.local. (83)
14:50:18.022000 IP 192.168.178.21.5353 > 224.0.0.251.5353: 0 [1a] [2q] PTR (QM)? _ipps._tcp.local. PTR (QM)? _ipp._tcp.local. (83)
14:50:24.269913 IP 192.168.178.21.17500 > 255.255.255.255.17500: UDP, length 104
14:50:24.271588 IP 192.168.178.21.17500 > 192.168.178.255.17500: UDP, length 104


I also tried the iptables thing you suggested but there is still nothing happening :-/ still the same error: connection refused.

---

### Post by The Cog on 2015-04-19
These two lines (repeated several times) show that the machine is refusing the connections.
```
14:49:56.636165 IP 192.168.178.21.54808 > 192.168.178.24.22: Flags [S], seq 648288592, win 29200, options [mss 1460,sackOK,TS val 618493 ecr 0,nop,wscale 7], length 0
14:49:56.636244 IP 192.168.178.24.22 > 192.168.178.21.54808: Flags [R.], seq 0, ack 648288593, win 0, length 0

```The first packet contains an S flag which tries to start a connection. The reply contains R which says reset the connection - a refusal. I don't believe this is a firewall issue - firewalls don't generally issue reset like that. I think there must be something wrong with the sshd configuration. But I don't know what - we know it's listening because netstat shows says so.

You may find something in the log files - /var/log/syslog or /var/log/auth.log.

---

### Post by apophis2 on 2015-04-21
Many thx :-)

But i really don't understand the output of that log files :-/

Isn't there a straightforward method for reconfiguring my sshd quickly?

cheers,
apo

---

### Post by nerdtron on 2015-04-21
> Isn't there a straightforward method for reconfiguring my sshd quickly? 
It would be straightforward if you hadn't messed up the firewall settings. That's why you need to reset what you have done on the firewall. Have you tried my answer on you post?
Also, what is the current "iptables -list" of both machines? Be sure that ufw is disabled before listing the iptables.

> But i really don't understand the output of that log files :-/
You can post some logs here, especially when you try to connect and then the connection is refused, it will surely generate logs on the receiving machine, so post that here.

---

