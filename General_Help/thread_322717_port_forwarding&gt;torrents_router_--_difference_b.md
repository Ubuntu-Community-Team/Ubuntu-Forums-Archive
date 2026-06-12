---
title: "port forwarding&gt;torrents router -- difference between inet addr and bcast, relevance?"
date: 2006-12-20
forum: General Help
---

### Post by ImplicitProcrastination on 2006-12-20
PROBLEM SOLVED. Thanks everybody!

Hi ubuntu people,

What exactly is the difference between inet addr and bcast?

How can I use that information to discern what I need to enter into http://www.portforward.com/english/routers/port_forwarding/Motorola/SBG900/Utorrent.htm"> 

```
ath0      Link encap:Ethernet  HWaddr 00:90:96:C5:B1:9C
          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::290:96ff:fec5:b19c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:157436 errors:27067 dropped:0 overruns:0 frame:27067
          TX packets:143137 errors:150 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:200
          RX bytes:101432915 (96.7 MiB)  TX bytes:11333232 (10.8 MiB)
          Interrupt:209 Memory:dcac0000-dcad0000

eth0      Link encap:Ethernet  HWaddr 00:02:3F:D6:7E:D3
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:201 Base address:0xe800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:130192 errors:0 dropped:0 overruns:0 frame:0
          TX packets:130192 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:6835167 (6.5 MiB)  TX bytes:6835167 (6.5 MiB)

```

Thanks in advance. It is my hope that this post can become a clearer version than http://ubuntuforums.org/showthread.php?t=294998&highlight=port+forwarding+static+IP+router+torrent"> this mess which constitutes the only thing I can easily find using the search engine relevant to my problem.

also what exactly are beans and what did I do to accrue 79 of them?

---

### Post by FlashOmega on 2006-12-21
I dont know what the second one is... but your ip address would be the 192.168.0.3  NOT the one ending in .255

---

### Post by ImplicitProcrastination on 2006-12-21
thanks,

If that number is the correct one to enter as Static IP address then my ports are forwarded correctly, and so this is not the problem.

Any idea how I can help you guys figure out how to help me? I miss my torrents and star trek episodes are running thin on the youtube. :(

---

### Post by ImplicitProcrastination on 2006-12-21
bump,

any theories?

---

### Post by dannyboy79 on 2006-12-21
beans are bascially equivalent to amount of threads you have posted. are you forwarding the same ports to both your windows and your ubuntu box??? we can;'t really help if you don't tell us what's the error is????

---

### Post by ImplicitProcrastination on 2006-12-21
No, I'm forwarding the ports to only one box.

The error is that the trackers seem to be unreachable. 0 kpbs upload and download.

---

### Post by ImplicitProcrastination on 2006-12-21
wow this sucks. my frostwire is down too.

no error messages, just nonresponsiveness. not from the programs themselves but from their functions.

---

### Post by Littleweseth on 2006-12-22
For the record :

Your 'inet addr' is your IP address, the (relatively) unique identifier used to send things to your computer.

The 'bcast' address is the range of addresses targeted when your computer sends a broadcast message - in the case of 192.168.0.255, a broadcast message sent by your computer will reach all computers with IP addresses starting with '192.168.0.[nnn]'. Broadcasts are sent by programs like Samba (Windows Sharing) or network games to advertise their presence - the equivalent of yelling 'HEY EVERYONE ELSE! I have a windows share you might be interested in over here!' or 'HEY EVERYONE! There's an Unreal Tournament server over here!'

---

### Post by ImplicitProcrastination on 2006-12-22
interesting.

unfortunately my bittorrent programs still elude me.

im puzzled, can't even figure out where to start.

---

### Post by dannyboy79 on 2006-12-22
please post the results of sudo iptables -L. also, how many seeders and leechers does the torrent that you are trying to run have???? i would suggest to test out your box you find a torrent with hundreds of seeds that way you can rule that out as being the problem. also, do a port scan to see if the ports you want open are actually open. also, are you sure you're forwarding the ports to the correct ip?? if you use dhcp (not recommended for a server) than it's possible that the ip within your router config is wrong. start with these simple things. also, what client are you using?

---

### Post by ImplicitProcrastination on 2006-12-22
I've been using uTorrent through wine and KTorrent neither work.

sudo iptables -L:
```

Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

```

that seems pretty enigmatic, what does it all mean?

the torrents I've been trying have plenty of seeds.

a port scan? let me look into that. dhcp is where the ISP automatically assigns you an IP right? I think  thats what I'm running, although it was in the tutorial (as opposed to Static right?). How that doesn't mean I'm out of luck. I'll try to find the website for a port scan and get back at you.

---

### Post by OffHand on 2006-12-23
> **ImplicitProcrastination said:**
> I've been using uTorrent through wine and KTorrent neither work.

sudo iptables -L:
```

Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

```

that seems pretty enigmatic, what does it all mean?

the torrents I've been trying have plenty of seeds.

a port scan? let me look into that. dhcp is where the ISP automatically assigns you an IP right? I think  thats what I'm running, although it was in the tutorial (as opposed to Static right?). How that doesn't mean I'm out of luck. I'll try to find the website for a port scan and get back at you.

DHCP is indeed how your ISP assigns you an IP. Dynamic Host Configuration Protocol. Your router will get his IP for the outside world this way. In your internal network you can use static IP addresses though.

---

### Post by dannyboy79 on 2006-12-25
what that means ferom iptables is tyhat you have no firewall rules setup which is bad for security but is good in terms of trying to troubleshoot your torrent issue. so basically you aren't blocking the ports that torrents use, wehich is what you want. a good port scanner would be [http://www.hackerwatch.org/probe/](http://www.hackerwatch.org/probe/) or simply use nmap within your own ubuntu. you  would just do sudo nmap -P0 external ip here. example: sudo nmap -P0 45.345.9873.12
that is a zero after the P not the letter O. this will tell you if your firewall has any ports open. nmap will only test ports 0-1024, the P0 option doesn't use ping, because some routers won't respond to a ping. you want to test which ever port you're telling your torrent client to use. so you would type in sudo nmap  -p T:6881-6889 external ip here. example 
nmap -p T:6881-6889 45.345.9873.12, would scan TCP ports 6881 thru 6889 at that ip addresss and tell you if they were open, closed, steathed, or what. to learn more about nmap, just read the man pages. I love the man pages, they tell you everything you need to knoqw about a program. you would type man nmap at the command line. good luck

---

