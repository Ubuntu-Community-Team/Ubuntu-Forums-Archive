---
title: "Something is running in the background on my machine 12.04 LTS"
date: 2016-06-09
forum: General Help
---

### Post by nwpll on 2016-06-09
Hi 

My internet speed is only 0.7 mbps so anything running in the background is causing me problems. I found a post from 2013 and i have copied and pasted below. When i type into a terminal i get the following message but what do i do to run nethogs????

Sorry about Copy and Pasting. 

Peter


peter@peter-Dell-DE051:~$ sudo nethogs eth0
[sudo] password for peter: 
creating socket failed while establishing local IP - are you root?
peter@peter-Dell-DE051:~$ 



[h=2]Re: Internet runs in background and consumes more data[/h] 		 				 				 					 				 		 			 				[INDENT] 					You can use 'nethogs' command to see which process is using the bandwidth. But you'll have to install it first :
 	Code:
 	sudo apt-get install nethogs 
Once installed, you can run it anytime on a desired interface as  root. For example, if your network interface in use is eth0, then-
 	Code:
 	sudo nethogs eth0 
If it is a USB modem, the interface is usually ppp0, just replace  eth0 with that or whatever is the name of the interface in use.

There is a native lightweight program to monitor the app/process  consuming the bandwidth, but I don't remember it (saw once in a post of  moderator oldos2er).

Once the culprit process is identified, we can suggest more precise ways to control it. 				[/INDENT]

---

### Post by ajgreeny on 2016-06-09
Are you sure the eth0 is correct?  Occasionally the system will give it another name, eg, eth1.

What does **ifconfig** output when run in terminal?

---

### Post by nwpll on 2016-06-09
HI Thanks for the reply

I tried Sudo nethogs eth1 and got the same message as before 

I then tried ifconfig and got the answer below, sorry but it means nothing to me.

Thanks

Peter

peter@peter-Dell-DE051:~$ sudo nethogs eth1
[sudo] password for peter: 
creating socket failed while establishing local IP - are you root?
peter@peter-Dell-DE051:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:13:20:b9:3b:dd  
          inet addr:192.168.1.33  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:20ff:feb9:3bdd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1545912 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1076809 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1810155228 (1.8 GB)  TX bytes:115801809 (115.8 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:10306 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10306 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1045199 (1.0 MB)  TX bytes:1045199 (1.0 MB)

peter@peter-Dell-DE051:~$

---

### Post by ajgreeny on 2016-06-09
That does show that you were correct using eth0, but I do not know nethogs so can not help any more.

---

### Post by nwpll on 2016-06-12
Hi

Anybody know how i can find what is running in the background using the internet.

Thanks

---

### Post by SeijiSensei on 2016-06-12
Use "sudo netstat -avp | grep tcp" to start.  The entries marked "LISTEN" are daemons that are listening for remote connections. The ones marked "ESTABLISHED' are outbound connections from your machine.  The right-hand column will give the process ID and daemon name.  For instance, here's an entry for minidlnad, a DLNA daemon I use:
```
tcp        0      0 *:8200                  *:*                 LISTEN      1181/minidlnad 
```
and here's one for an outbound SSH connection:
```
tcp        0      0 192.168.100.1:38949 192.168.100.100:ssh     ESTABLISHED 2732/ssh 
```
That shows the connection originates on port 38949 of 192.168.100.1 and terminates at the SSH port (22) on 192.168.100.100.

You can also replace "tcp" with "udp" above to see connections using that protocol.  I'm guessing anything significant will be using TCP though.

---

