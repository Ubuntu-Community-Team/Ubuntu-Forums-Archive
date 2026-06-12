---
title: "Why are these ports open? How to close?"
date: 2007-06-03
forum: General Help
---

### Post by UpAndRunning on 2007-06-03
Hello, just got up and running with Ubuntu, a few days ago.

I ran a scan from [www.grc.com](www.grc.com) using their ShieldsUp! and it showed the following ports are open on my computer: 21, 22, 23, and 80.

Ubuntu Docs say that by default all ports are closed. I installed Firestarter firewall, but running the ShieldsUp scan again shows the same ports are still open and failing the security test.

Any ideas how I can secure my computers ports? Or at least determine what's opened them?

Searched everywhere online for answers, but couldn't find anything. Many thanks

---

### Post by pseudonym on 2007-06-03
Was it just a standard desktop installation you did? If yes, then no ports should be open. If no, then those open ports usually means you're running FTP, SSH, Telnet, and HTTP servers (in that order). When you run the scan at grc.com it can show you what ports serve what functions...

---

### Post by BigSilly on 2007-06-03
That's interesting. On my PC Firestarter is set to start on boot up. You don't get the GUI, but it's there in the boot-up manager. I've just been to Shields Up, without the Firestarter GUI enabled, and all my ports apart from 2 are closed. The spare 2 are stealthed apparently. But, when I start up the Firestarter GUI and go back to Shields Up for the same test (first 1056 ports) they are *all* stealthed!!

How comes?

---

### Post by UpAndRunning on 2007-06-03
I installed the standard desktop version. I did install a few applications, including aMule (P2P sharing app), could this app have opened my ports? It's not running by default.

ShieldsUp shows the purpose of each port, (FTP, SSH, etc) but doesn't show the application that is using it.

---

### Post by dbott67 on 2007-06-03
A few questions:

Are you behind a firewall or is your computer directly connected to the internet?  

If you're on a corporate/school LAN (or even have your own NAT router), their firewall may have port-forwarding rules for 21 (FTP), 22 (SSH), 23 (Telnet), 80 (HTTP).

Can you post the output of the following commands:

Listing the status of iptables will help determine if it's configured correctly:
```
dbott@feisty:~$ [COLOR=Red]**sudo iptables -L**[/COLOR]
Password:
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```Outputting the status of all listening ports will help us determine if you've got any services running (such as SSH, FTP, Telnet, HTTP, etc.)

You'll see on my computer, I've got SSH, VNC and Samba running, but they are only available internally.  I've created a couple of rules on my NAT-router firewall to permit inbound SSH and one other remote service on non-standard ports so that I can access my machine remotely, otherwise, there are no other accessible services remotely.
```
dbott@feisty:~$ [COLOR=Red]**netstat -l -n**[/COLOR]
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 127.0.0.1:2208          0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN     [COLOR=Purple]*<--- SMB*[/COLOR]
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN     [COLOR=Purple]*<--- HTTP*[/COLOR]
tcp        0      0 0.0.0.0:631             0.0.0.0:*               LISTEN     [COLOR=Purple]*<--- CUPS*[/COLOR]
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN     [COLOR=Purple]*<--- SMB*[/COLOR]
tcp        0      0 127.0.0.1:2207          0.0.0.0:*               LISTEN     
tcp6       0      0 :::5900                 :::*                    LISTEN     [COLOR=Purple]*<--- VNC*[/COLOR]
tcp6       0      0 :::22                   :::*                    LISTEN      [COLOR=Purple]*<--- SSH*[/COLOR]
tcp6       0      0 :::631                  :::*                    LISTEN     [COLOR=Purple]*<--- CUPS*[/COLOR]
udp        0      0 0.0.0.0:32768           0.0.0.0:*                          
udp        0      0 192.168.1.106:137       0.0.0.0:*                          
udp        0      0 0.0.0.0:137             0.0.0.0:*                          
udp        0      0 192.168.1.106:138       0.0.0.0:*                          
udp        0      0 0.0.0.0:138             0.0.0.0:*                          
udp        0      0 0.0.0.0:68              0.0.0.0:*                          
udp        0      0 0.0.0.0:5353            0.0.0.0:*                          
udp        0      0 0.0.0.0:631             0.0.0.0:*                          
Active UNIX domain sockets (only servers)
Proto RefCnt Flags       Type       State         I-Node Path
unix  2      [ ACC ]     STREAM     LISTENING     16383    /var/run/gdm_socket
unix  2      [ ACC ]     STREAM     LISTENING     16435    /tmp/.X11-unix/X0
unix  2      [ ACC ]     STREAM     LISTENING     17375    /tmp/ssh-mZNNOd5276/agent.5276
unix  2      [ ACC ]     STREAM     LISTENING     17406    /tmp/orbit-dbott/linc-14c9-0-aab76959fd2
unix  2      [ ACC ]     STREAM     LISTENING     17416    /tmp/orbit-dbott/linc-149c-0-63d95dea6adba
unix  2      [ ACC ]     STREAM     LISTENING     17620    /tmp/.ICE-unix/5276
unix  2      [ ACC ]     STREAM     LISTENING     17197    /var/run/apache2/cgisock.5137
unix  2      [ ACC ]     STREAM     LISTENING     16190    /var/run/avahi-daemon/socket
unix  2      [ ACC ]     STREAM     LISTENING     17386    @/tmp/dbus-7mas6PLqB5
unix  2      [ ACC ]     STREAM     LISTENING     14926    /var/run/dbus/system_bus_socket
unix  2      [ ACC ]     STREAM     LISTENING     14947    @/var/run/hald/dbus-Q2nQID3Nu6
unix  2      [ ACC ]     STREAM     LISTENING     14680    /var/run/acpid.socket
unix  2      [ ACC ]     STREAM     LISTENING     17629    /tmp/keyring-BPWKkd/socket
unix  2      [ ACC ]     STREAM     LISTENING     17650    /tmp/orbit-dbott/linc-14ce-0-688a20d13874d
unix  2      [ ACC ]     STREAM     LISTENING     17678    /tmp/.esd-1000/socket
unix  2      [ ACC ]     STREAM     LISTENING     17731    /tmp/orbit-dbott/linc-14db-0-48457a8e5d400
unix  2      [ ACC ]     STREAM     LISTENING     17752    /tmp/orbit-dbott/linc-14e0-0-180e13af98e53
unix  2      [ ACC ]     STREAM     LISTENING     17817    /tmp/orbit-dbott/linc-14e1-0-6ad7300ce3b6a
unix  2      [ ACC ]     STREAM     LISTENING     17831    /tmp/orbit-dbott/linc-14e4-0-60e58490f12d3
unix  2      [ ACC ]     STREAM     LISTENING     17868    /tmp/orbit-dbott/linc-14eb-0-122ddd0260831
unix  2      [ ACC ]     STREAM     LISTENING     17872    /tmp/orbit-dbott/linc-14e7-0-122ddd026277c
unix  2      [ ACC ]     STREAM     LISTENING     17928    /tmp/orbit-dbott/linc-14f2-0-7a23bdd73343d
unix  2      [ ACC ]     STREAM     LISTENING     17970    /tmp/orbit-dbott/linc-14f0-0-122ddd04674d
unix  2      [ ACC ]     STREAM     LISTENING     17978    /tmp/orbit-dbott/linc-1502-0-361d2c144a485
unix  2      [ ACC ]     STREAM     LISTENING     18000    /tmp/orbit-dbott/linc-1503-0-361d2c1475943
unix  2      [ ACC ]     STREAM     LISTENING     18028    /tmp/orbit-dbott/linc-14fb-0-361d2c153030a
unix  2      [ ACC ]     STREAM     LISTENING     18072    /tmp/orbit-dbott/linc-150f-0-5b9878c1cb3f6
unix  2      [ ACC ]     STREAM     LISTENING     18137    /tmp/orbit-dbott/linc-14f8-0-a5f1596b3d86
unix  2      [ ACC ]     STREAM     LISTENING     18141    /tmp/mapping-dbott
unix  2      [ ACC ]     STREAM     LISTENING     18195    /tmp/orbit-dbott/linc-1529-0-6191919cb836a
unix  2      [ ACC ]     STREAM     LISTENING     18206    /tmp/orbit-dbott/linc-152b-0-6191919cbf8bf
unix  2      [ ACC ]     STREAM     LISTENING     18785    /tmp/orbit-dbott/linc-1536-0-3714b08c5351c
unix  2      [ ACC ]     STREAM     LISTENING     18828    /tmp/orbit-dbott/linc-1552-0-7d753564b31ab
unix  2      [ ACC ]     STREAM     LISTENING     18868    /tmp/orbit-dbott/linc-155a-0-597f26d368bde
unix  2      [ ACC ]     STREAM     LISTENING     19066    /tmp/orbit-dbott/linc-15c0-0-44f30f7aea4a
unix  2      [ ACC ]     STREAM     LISTENING     19197    /tmp/orbit-dbott/linc-168b-0-547e8654bc6f0
unix  2      [ ACC ]     STREAM     LISTENING     27501    /tmp/orbit-dbott/linc-329a-0-54a56395a6c1
unix  2      [ ACC ]     STREAM     LISTENING     24395    /tmp/orbit-dbott/linc-25ab-0-3a70621cb4bdc
unix  2      [ ACC ]     STREAM     LISTENING     24399    /tmp/OSL_PIPE_1000_SingleOfficeIPC_9ace6cc5e12826dc3c5547ccd9f6a894
unix  2      [ ACC ]     STREAM     LISTENING     17087    /var/run/sdp
unix  2      [ ACC ]     STREAM     LISTENING     14944    @/var/run/hald/dbus-ywIS5XLuUG
unix  2      [ ACC ]     STREAM     LISTENING     16606    /var/run/cups/cups.sock
unix  2      [ ACC ]     STREAM     LISTENING     16231    @/tmp/dbus-sjzbRbj5L0

```Running ifconfig will help determine if you're behind a NAT firewall.  If you get a 192.168.x.y address, GRC is not seeing your computer, rather they are probing the firewall:
```
dbott@feisty:~$ [COLOR=Red]**ifconfig**[/COLOR]
eth0      Link encap:Ethernet  HWaddr 00:50:BA:C0:A7:55  
          inet addr:192.168.1.106  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::250:baff:fec0:a755/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:303924 errors:0 dropped:0 overruns:0 frame:0
          TX packets:171492 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:320471364 (305.6 MiB)  TX bytes:18124398 (17.2 MiB)
          Interrupt:17 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

```-Dave

---

### Post by UpAndRunning on 2007-06-03
Here's the output from the first command:

ald@ald:~$ sudo iptables -L
Password:
Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  RT                   anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  RT                   anywhere            
ACCEPT     0    --  anywhere             anywhere            
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 
DROP       0    --  anywhere             255.255.255.255     
DROP       0    --  anywhere             192.168.1.255       
DROP       0    --  BASE-ADDRESS.MCAST.NET/8  anywhere            
DROP       0    --  anywhere             BASE/8              
DROP       0    --  255.255.255.255      anywhere            
DROP       0    --  anywhere             0.0.0.0             
DROP       0    --  anywhere             anywhere            state INVALID 
LSI        0    -f  anywhere             anywhere            limit: avg 10/min burst 5 
INBOUND    0    --  anywhere             anywhere            
LOG_FILTER  0    --  anywhere             anywhere            
LOG        0    --  anywhere             anywhere            LOG level info prefix `Unknown Input' 

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 
LOG_FILTER  0    --  anywhere             anywhere            
LOG        0    --  anywhere             anywhere            LOG level info prefix `Unknown Forward' 

Chain OUTPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  192.168.1.101        RT                  tcp dpt:domain 
ACCEPT     udp  --  192.168.1.101        RT                  udp dpt:domain 
ACCEPT     0    --  anywhere             anywhere            
DROP       0    --  BASE/8               anywhere            
DROP       0    --  anywhere             BASE/8              
DROP       0    --  255.255.255.255      anywhere            
DROP       0    --  anywhere             0.0.0.0             
DROP       0    --  anywhere             anywhere            state INVALID 
OUTBOUND   0    --  anywhere             anywhere            
LOG_FILTER  0    --  anywhere             anywhere            
LOG        0    --  anywhere             anywhere            LOG level info prefix `Unknown Output' 

Chain INBOUND (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
LSI        0    --  anywhere             anywhere            

Chain LOG_FILTER (5 references)
target     prot opt source               destination         

Chain LSI (2 references)
target     prot opt source               destination         
LOG_FILTER  0    --  anywhere             anywhere            
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN 
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST 
LOG        icmp --  anywhere             anywhere            icmp echo-request limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       icmp --  anywhere             anywhere            icmp echo-request 
LOG        0    --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Inbound ' 
DROP       0    --  anywhere             anywhere            

Chain LSO (0 references)
target     prot opt source               destination         
LOG_FILTER  0    --  anywhere             anywhere            
LOG        0    --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Outbound ' 
REJECT     0    --  anywhere             anywhere            reject-with icmp-port-unreachable 

Chain OUTBOUND (1 references)
target     prot opt source               destination         
ACCEPT     icmp --  anywhere             anywhere            
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     0    --  anywhere             anywhere            
ald@ald:~$

---

### Post by UpAndRunning on 2007-06-03
And from the second command:

ald@ald:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:06:5B:B8:17:DC  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0xec00 

eth0:avah Link encap:Ethernet  HWaddr 00:06:5B:B8:17:DC  
          inet addr:169.254.7.141  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:11 Base address:0xec00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2137 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2137 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:153884 (150.2 KiB)  TX bytes:153884 (150.2 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:09:5B:89:DA:BF  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::209:5bff:fe89:dabf/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:61485 errors:0 dropped:0 overruns:0 frame:0
          TX packets:41689 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:81882350 (78.0 MiB)  TX bytes:5125461 (4.8 MiB)

wmaster0  Link encap:UNSPEC  HWaddr 00-09-5B-89-DA-BF-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
ald@ald:~$

---

### Post by dbott67 on 2007-06-03
> **UpAndRunning said:**
> And from the second command:

```
amphibian@amphibian-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:06:5B:B8:17:DC  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0xec00 

eth0:avah Link encap:Ethernet  HWaddr 00:06:5B:B8:17:DC  
          inet addr:169.254.7.141  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:11 Base address:0xec00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2137 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2137 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:153884 (150.2 KiB)  TX bytes:153884 (150.2 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:09:5B:89:DA:BF  
          inet addr:[COLOR=Red]**192.168.1.101**[/COLOR]  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::209:5bff:fe89:dabf/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:61485 errors:0 dropped:0 overruns:0 frame:0
          TX packets:41689 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:81882350 (78.0 MiB)  TX bytes:5125461 (4.8 MiB)

wmaster0  Link encap:UNSPEC  HWaddr 00-09-5B-89-DA-BF-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

amphibian@amphibian-laptop:~$
```

It appears as though you are behind some sort of NAT firewall (as indicated by the 192.168.1.101 IP address).  GRC is not probing your computer.

What kind of network are you on?

-Dave

---

### Post by dbott67 on 2007-06-03
Can you go to [www.ipchicken.com]("http://www.ipchicken.com") and post the IP address it reports?  It will undoubtedly not be 192.168.1.101.

[COLOR=Purple]*We'll edit the post from IPChicken to hide your public IP address in a couple of minutes.*[/COLOR]

For example, my internal IP address is 192.168.1.106, but IPChicken reports 69.xx.yy.53

-Dave

---

### Post by UpAndRunning on 2007-06-03
Ok, I'm connecting through a wireless lan, and aparently the firewall is configured to:

Block Anonymous Internet Requests
Filter Multicast
Filter IDENT

VPN is configured to:

IPSec Passthrough: Enable
PPTPPassthrough: Enable
L2TP Passthrough Enable

Could these settings be the cause?

---

### Post by dbott67 on 2007-06-03
> **UpAndRunning said:**
> Ok, I'm connecting through a wireless lan, and aparently the firewall is configured to:

[COLOR=Red]** Block Anonymous Internet Requests**[/COLOR]
Filter Multicast
Filter IDENT

VPN is configured to:

IPSec Passthrough: Enable
PPTPPassthrough: Enable
L2TP Passthrough Enable

Could these settings be the cause?

Nope.  It's another device that is reporting the open ports.  Can you post your public IP from [www.ipchicken.com]("http://www.ipchicken.com") as posted above (post #9).

Your router is blocking all unsolicted inbound traffic (which is good).

Thanks,
Dave

---

### Post by UpAndRunning on 2007-06-03
I'm sorry, I'm not sure of the safety of giving out my public ip (don't mean to offend, just trying to err on the side of caution), however:

I determined the ip address, and entered it into my browser. Strangely it leads to the admin page of a combo DSL wireless router, which is definitely not mine. Any idea how this could happen?

---

### Post by dbott67 on 2007-06-03
> **UpAndRunning said:**
> I'm sorry, I'm not sure of the safety of giving out my public ip (don't mean to offend, just trying to err on the side of caution),


No offense.  If you did post it, I would have had you delete/obscure it within a minute or so.

If you want, PM me your public IP and I might be able to provide you with more information.  Rest assured that a) your computer is already protected by your own wifi router & iptables and b) I would never use the information for malicious purposes.  In fact, I may be able to help you secure that router so that some bad guy does not get into it.

Your public IP address is used with every online transaction you do.  For example, your IP is logged with every post you make here on the forums.

> **UpAndRunning said:**
> however:

I determined the ip address, and entered it into my browser. Strangely it leads to the admin page of a combo DSL wireless router, which is definitely not mine. Any idea how this could happen?

Where are you: school, work, home, dorm?

To me, it just looks like you're sharing internet access with a bunch of other folks.

-Dave

---

### Post by UpAndRunning on 2007-06-03
It's my home network, the wireless is password protected, and the router itself is password protected. There are only a few others able to connect to the network (my flat mates).

I have changed the router VPN settings to Disabled, as nobody should be accessing the network via VPN. Don't know if that'll change anything (doesn't seem to have made a difference to ShieldsUp)

Any idea why the IP address would point to someone else's router?

---

### Post by dbott67 on 2007-06-03
I'm thinking that you may be connected to someone else's unsecured AP.

A few more questions:

1. Are you on DSL or cable?
2. Does your wireless router connect directly to the cable/DSL modem?
3. Are you sure that you're associated with your wireless AP?
4. What happens if you connect to the AP via ethernet (not wireless)?  Go to IPchicken & shields up and see if the results are different.

---

### Post by dbott67 on 2007-06-03
What is your ESSID? 

Also, can you post the output of:
```
iwlist scanning
``````
dbott@dapper:~$ [COLOR=Red]**iwlist scanning**[/COLOR]

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :

Cell 01 - Address: 00:40:05:B2:AF:YY
              ESSID:"bott"
              Mode:Master
              Frequency:2.437 GHz (Channel 6)
              Quality=34/100  Signal level=39/100  Noise level=11/100
              Encryption key:on
              Bit Rate:22 Mb/s

Cell 02 - Address: 00:05:5D:FA:B2:XX
              ESSID:"soni"
              Mode:Master
              Frequency:2.437 GHz (Channel 6)
              Quality=24/100  Signal level=27/100  Noise level=12/100
              Encryption key:on
              Bit Rate:54 Mb/s

sit0      Interface doesn't support scanning.
```

---

### Post by UpAndRunning on 2007-06-03
Ok, very sorry, big mistake on my part about the router: 

In fact the ip address is pointing to the correct DSL router (forgot the fact that we changed the router recently).

The ip address that I got from ipchicken.com is the same ip address that ShieldsUp is seeing. This ip address points directly to the admin page of my DSL modem, which seems quite insecure, and I assume means that anybody who has my public ip address can access the admin login page for the router.

This strikes me as being extremely insecure for the router itself, but I assume it means that the open ports are also those of the router and not my computer, does this sound right?

Very sorry about the mistake on my part.

---

### Post by dbott67 on 2007-06-03
Yes, those are open ports on the router (not your computer) and it seems very insecure for a router to be externally accessible by default.

There should be a setting in the router to disable external configuration.  You should only allow logging in from internal IP addresses.

The HTTP access is for the web admin page; it appears as though it also has FTP, SSH and Telnet access.  Definitely disable those from the external interface or else someone my help themselves to your home network and setup a spam shop (or give themselves free internet at a bare minimum).

-Dave

---

### Post by UpAndRunning on 2007-06-03
Alright, I'll definitely change those settings, thank you very much for all of your help Dave, I really appreciate it.

---

### Post by dbott67 on 2007-06-03
By the way, if this is a Linksys WRT54G Router, then I think one of your flat mates may have enabled port-forwarding.  By default, the Linksys seems to have external access disabled.

1. Login to the router

2. Go to "Applications & Gaming" and then click on "Port Range Forward"

3. Look to see if any ports have been forwarded 21, 22, 23 & 80 and which internal IP they are going to.

4. With the internal number you should be able to determine which of your flat mates has setup the web, ssh, ftp & telnet server.

Check this emulator page:
[http://www.linksysdata.com/ui/WRT54G/v1-v4/4.20.7/Forward.htm](http://www.linksysdata.com/ui/WRT54G/v1-v4/4.20.7/Forward.htm)

-Dave

---

### Post by dbott67 on 2007-06-03
> **UpAndRunning said:**
> Alright, I'll definitely change those settings, thank you very much for all of your help Dave, I really appreciate it.

You're welcome.

-Dave

---

### Post by dbott67 on 2007-06-03
Another thing to try to determine who's running what services is to try to telnet to the service on the appropriate port and see what comes up.  For example, suppose your public IP is 192.168.1.106, you could try the following:
```
dbott@feisty:~$[COLOR=Red]** telnet 192.168.1.106 80**[/COLOR]
Trying 192.168.1.106...
Connected to 192.168.1.106.
Escape character is '^]'.
GET  [COLOR=Purple]*<-- type GET here & press ENTER*[/COLOR]
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 3.2 Final//EN">
<html>
 <head>
  <title>Index of /</title>
 </head>
 <body>
<h1>Index of /</h1>
<table><tr><th><img src="/icons/blank.gif" alt="[ICO]"></th><th><a href="?C=N;O=D">Name</a></th><th><a href="?C=M;O=A">Last modified</a></th><th><a href="?C=S;O=A">Size</a></th><th><a href="?C=D;O=A">Description</a></th></tr><tr><th colspan="5"><hr></th></tr>
<tr><td valign="top"><img src="/icons/folder.gif" alt="[DIR]"></td><td><a href="apache2-default/">apache2-default/</a></td><td align="right">20-Nov-2004 15:16  </td><td align="right">  - </td></tr>
<tr><th colspan="5"><hr></th></tr>
</table>
<address>[COLOR=Red]Apache/2.2.3 (Ubuntu) mod_perl/2.0.2 Perl/v5.8.8 Server at 127.0.1.1 Port 80[/COLOR]</address>
</body></html>
Connection closed by foreign host.
```
And
```
dbott@feisty:~$ [COLOR=Red]**telnet 192.168.1.106 22**[/COLOR]
Trying 192.168.1.106...
Connected to 192.168.1.106.
Escape character is '^]'.
[COLOR=Red]SSH-2.0-OpenSSH_4.3p2 Debian-8ubuntu1[/COLOR]
^]

telnet> quit
Connection closed.

```
```
dbott@feisty:~$ [COLOR=Red]**telnet 192.168.1.2 21**[/COLOR]
Trying 192.168.1.2...
Connected to 192.168.1.2.
Escape character is '^]'.
220 NET Disk FTP Server ready.
^]

telnet> quit
Connection closed.
```

Enumerating the services in this manner provides information on the version & what-not.

-Dave

---

### Post by UpAndRunning on 2007-06-03
Another piece of info:

There is a process running on my machine named ssh-agent. Could this be the culprit for the port 22 and 23? I don't know why it's running or exactly what it does.

---

### Post by UpAndRunning on 2007-06-03
Here's the output from port 80:

Escape character is '^]'.
UNKNOWN 408 Request Timeout
Server: mini_httpd/1.19 19dec2003
Date: Mon, 04 Jun 2007 00:30:04 GMT
Cache-Control: no-cache,no-store
Content-Type: text/html; charset=%s
Connection: close

<HTML>
<HEAD><TITLE>408 Request Timeout</TITLE></HEAD>
<BODY BGCOLOR="#cc9999" TEXT="#000000" LINK="#2020ff" VLINK="#4040cc">
<H4>408 Request Timeout</H4>
No request appeared within a reasonable time period.
<HR>
<ADDRESS><A HREF="http://www.acme.com/software/mini_httpd/">mini_httpd/1.19 19dec2003</A></ADDRESS>
</BODY>
</HTML>
Connection closed by foreign host.

**********************************************
For port 21:

Escape character is '^]'.
Connection closed by foreign host.

**********************************************
For port 22:

Escape character is '^]'.
Connection closed by foreign host.

**********************************************
For port 23:

Escape character is '^]'.

BusyBox on localhost login: 

**********************************************

So apparently port 23 is actually asking for login.

---

### Post by dbott67 on 2007-06-03
_**Port 80:**_
The output gives us a clue that leads to [http://www.acme.com/software/mini_httpd/](http://www.acme.com/software/mini_httpd/).  This indicates that the http service is some sort of embedded application in a network device (probably the router).

If this were a full-blown web server, we'd see Apache instead.

_**Port 21 & 22:**_
Provides no data.


_**Port 23:**_
BusyBox is (generally) an embedded Linux distribution that is installed in various network appliances (like a NAS device, router or other similar device).

As with the port 80 output, if this were a full-blown linux distro, we'd see** ProFTPd** or similar.

So, seeing as both ports 80 & 23 are indicating that they are "embedded" apps, my guess is that they are part of your router.

_**SSH-AGENT**_
As for **ssh-agent**, this is a service that is installed & started by default.  From the man pages:
```
DESCRIPTION
     ssh-agent is a program to hold private keys used for public key authentication (RSA, DSA).  The idea is that ssh-agent is started in the beginning of an X-session or a login session, and
     all other windows or programs are started as clients to the ssh-agent program.  Through use of environment variables the agent can be located and automatically used for authentication
     when logging in to other machines using ssh(1).
```So the answer is "no", your computer is not the culprit.

Ultimately, the answer lies within the router itself.

[COLOR=Purple][I]What's the make & model of router?  If it is the the Linksys WRT54g, then check to see if anyone setup port-forwarding.  If port-forwarding is not enabled, then the device is running those services itself.
[/I][/COLOR] 
_**Scanning your Subnet**_

If you really want to get geeky, then run an **nmap** scan on your subnet to see what your flat-mates have running on their systems (service-wise, such as FTP, SSH, etc.).  Here's the output from my subnet:
```
dbott@feisty:~$ [COLOR=Red]**nmap -A -T4 192.168.1.0/24**[/COLOR]

Starting Nmap 4.20 ( http://insecure.org ) at 2007-06-03 22:14 EDT
Interesting ports on 192.168.1.1:   [COLOR=Purple]*#<-- My D-Link DI-614+ Router*[/COLOR]
Not shown: 1696 closed ports
PORT   STATE SERVICE    VERSION
80/tcp open  tcpwrapped

Interesting ports on 192.168.1.2:   [COLOR=Purple]*#<-- My NAS Device*[/COLOR]
Not shown: 1694 closed ports
PORT    STATE SERVICE     VERSION
21/tcp  open  ftp         NET Disk ftpd
80/tcp  open  http        Linksys wireless-G WAP http config (Name NET Disk)
139/tcp open  netbios-ssn
Service Info: Device: WAP

Interesting ports on 192.168.1.10:  [COLOR=Purple]*#<-- My HP Jet Direct Print Server*[/COLOR]
Not shown: 1694 closed ports
PORT     STATE SERVICE    VERSION
23/tcp   open  telnet     HP Jet Direct printer telnetd
515/tcp  open  printer
9100/tcp open  jetdirect?
Service Info: Device: printer

Interesting ports on 192.168.1.102:  [COLOR=Purple]*#<-- My kids XP Pro box*[/COLOR]
Not shown: 1686 closed ports
PORT     STATE SERVICE       VERSION
25/tcp   open  smtp          Microsoft ESMTP 6.0.2600.2180
80/tcp   open  http          Microsoft IIS webserver 5.1
135/tcp  open  msrpc         Microsoft Windows RPC
139/tcp  open  netbios-ssn
443/tcp  open  https?
445/tcp  open  microsoft-ds  Microsoft Windows XP microsoft-ds
3389/tcp open  microsoft-rdp Microsoft Terminal Service
5800/tcp open  vnc-http      Ultr@VNC (Name piii-600; Resolution 1024x800; VNC TCP port: 5900)
5900/tcp open  vnc           VNC (protocol 3.6)
8000/tcp open  http          HP Web Jetadmin print server 2.0.39 ((Win32) mod_ssl/2.0.39 OpenSSL/0.9.6c)
8443/tcp open  http          HP Web Jetadmin print server 2.0.39 ((Win32) mod_ssl/2.0.39 OpenSSL/0.9.6c)
Service Info: Host: piii-600; OS: Windows; Device: print server

Interesting ports on 192.168.1.106:  [COLOR=Purple]*#<-- My Ubuntu Feisty Fawn box*[/COLOR]
Not shown: 1691 closed ports
PORT     STATE SERVICE     VERSION
22/tcp   open  ssh         OpenSSH 4.3p2 Debian 8ubuntu1 (protocol 2.0)
80/tcp   open  http        Apache httpd 2.2.3 ((Ubuntu) mod_perl/2.0.2 Perl/v5.8.8)
139/tcp  open  netbios-ssn Samba smbd 3.X (workgroup: MSHOME)
445/tcp  open  netbios-ssn Samba smbd 3.X (workgroup: MSHOME)
631/tcp  open  ipp         CUPS 1.2
5900/tcp open  vnc         VNC (protocol 3.7)
Service Info: OS: Linux

Interesting ports on 192.168.1.109:   [COLOR=Purple]*#<-- My MAC OSX box*[/COLOR]
Not shown: 1501 closed ports, 180 filtered ports
PORT     STATE SERVICE     VERSION
21/tcp   open  ftp         tnftpd 20040810
22/tcp   open  ssh          (protocol 1.99)
25/tcp   open  smtp?
80/tcp   open  http?
110/tcp  open  pop3?
119/tcp  open  nntp?
143/tcp  open  imap?
389/tcp  open  tcpwrapped
443/tcp  open  ssl/unknown
465/tcp  open  ssl/unknown
563/tcp  open  ssl/unknown
636/tcp  open  ssl/unknown
993/tcp  open  ssl/unknown
995/tcp  open  ssl/unknown
5900/tcp open  vnc         VNC (protocol 3.3)
6000/tcp open  X11          (access denied)
Service Info: Host: MAC-OSX.local; OS: Unix

Service detection performed. Please report any incorrect results at http://insecure.org/nmap/submit/ .
Nmap finished: 256 IP addresses (6 hosts up) scanned in 48.445 seconds 
```

A few other interesting things to note:

- My wife's XP Pro laptop went undetected, probably because the XP firewall is enabled.

Your internal subnet is the same as mine (192.168.1.0) so you can just use the same command as I did:
```
nmap -A -T4 192.168.1.0/24
```-Dave

---

### Post by UpAndRunning on 2007-06-04
The DSL modem/router is an AirTies rt-102 

Just installed and ran nmap:

 nmap -A -T4 192.168.1.0/24

Starting Nmap 4.20 ( [http://insecure.org](http://insecure.org) ) at 2007-06-04 16:19 EEST
Interesting ports on 192.168.1.1:
Not shown: 1692 filtered ports
PORT     STATE  SERVICE  VERSION
20/tcp   closed ftp-data
21/tcp   closed ftp
23/tcp   closed telnet
80/tcp   open   http     Intoto httpd 1.0
1723/tcp open   pptp?

All 1697 scanned ports on 192.168.1.101 are closed

Service detection performed. Please report any incorrect results at [http://insecure.org/nmap/submit/](http://insecure.org/nmap/submit/) .
Nmap finished: 256 IP addresses (2 hosts up) scanned in 97.560 seconds

---

### Post by dbott67 on 2007-06-04
You can see by the results that your computer (192.168.1.101) is stealthed, meaning that your computer does not respond to unsolicited inbound requests.  The advantage with a 'stealthed' port vs. a 'closed' port is that the scanner would never know that there is a computer on that IP address.  
 
The router (192.168.1.1), on the other hand is the device that has the ports visible (20, 21 & 23 are closed, but most scanners will know that there is a computer running on that IP address).
 
-Dave

---

