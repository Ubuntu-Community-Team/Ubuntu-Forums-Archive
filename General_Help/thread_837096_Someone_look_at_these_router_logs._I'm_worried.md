---
title: "Someone look at these router logs. I'm worried"
date: 2008-06-22
forum: General Help
---

### Post by garethsimpsonuk on 2008-06-22
Hi everyone well I've been learning /setting up my server lately and it's mostly been off my home network. I forgot to close port 80 while doing this and have just checked my router logs this morning. I done a whois lookup on one of the ip addresses and it come back as a virgin.net and others are 23.com address but from amsterdam. Here they are:

```
Sun, 2002-09-08 12:00:42 - Initialize LCP.
Sun, 2002-09-08 12:00:43 - LCP is allowed to come up.
Sun, 2002-09-08 12:00:47 - CHAP authentication success
Sun, 2002-09-08 12:00:54 - Send out NTP request to time-g.netgear.com
Wed, 2008-06-18 15:32:26 - Receive NTP Reply from time-g.netgear.com
Wed, 2008-06-18 15:31:32 - Router start up
Wed, 2008-06-18 20:31:10 - TCP Packet - Source:65.41.154.17,1953 Destination:82.9.17.55,80 - [HTTP rule match]
Wed, 2008-06-18 22:26:36 - TCP Packet - Source:125.65.112.135,6000 Destination:82.9.17.55,80 - [HTTP rule match]
Wed, 2008-06-18 23:57:21 - TCP Packet - Source:192.168.0.7,1048 Destination:82.9.17.55,80 - [HTTP rule match]
Wed, 2008-06-18 23:59:23 - TCP Packet - Source:192.168.0.7,1066 Destination:82.9.17.55,80 - [HTTP rule match]
Thu, 2008-06-19 00:03:28 - TCP Packet - Source:207.46.199.112,16475 Destination:82.9.17.55,80 - [HTTP rule match]
Thu, 2008-06-19 00:04:13 - TCP Packet - Source:192.168.0.2,1157 Destination:82.9.17.55,80 - [HTTP rule match]
Thu, 2008-06-19 00:04:34 - TCP Packet - Source:192.168.0.2,1160 Destination:82.9.17.55,80 - [HTTP rule match]
Thu, 2008-06-19 00:04:55 - TCP Packet - Source:192.168.0.2,1162 Destination:82.9.17.55,80 - [HTTP rule match]
Thu, 2008-06-19 00:04:58 - TCP Packet - Source:192.168.0.2,1164 Destination:82.9.17.55,80 - [HTTP rule match]
Thu, 2008-06-19 00:05:16 - TCP Packet - Source:192.168.0.2,1165 Destination:82.9.17.55,80 - [HTTP rule match]
Thu, 2008-06-19 00:05:19 - TCP Packet - Source:192.168.0.2,1166 Destination:82.9.17.55,80 - [HTTP rule match]
Thu, 2008-06-19 00:07:18 - TCP Packet - Source:192.168.0.2,1170 Destination:82.9.17.55,80 - [HTTP rule match]
Thu, 2008-06-19 00:07:39 - TCP Packet - Source:192.168.0.2,1183 Destination:82.9.17.55,80 - [HTTP rule match]
Thu, 2008-06-19 00:08:12 - TCP Packet - Source:192.168.0.2,1215 Destination:82.9.17.55,80 - [HTTP rule match]
Thu, 2008-06-19 00:08:33 - TCP Packet - Source:192.168.0.2,1228 Destination:82.9.17.55,80 - [HTTP rule match]
Thu, 2008-06-19 00:09:25 - TCP Packet - Source:192.168.0.2,1248 Destination:82.9.17.55,80 - [HTTP rule match]
Thu, 2008-06-19 00:09:46 - TCP Packet - Source:192.168.0.2,1249 Destination:82.9.17.55,80 - [HTTP rule match]
Thu, 2008-06-19 00:10:10 - TCP Packet - Source:192.168.0.2,1270 Destination:82.9.17.55,80 - [HTTP rule match]
Thu, 2008-06-19 00:10:31 - TCP Packet - Source:192.168.0.2,1276 Destination:82.9.17.55,80 - [HTTP rule match]
Thu, 2008-06-19 00:11:40 - TCP Packet - Source:192.168.0.2,1294 Destination:82.9.17.55,80 - [HTTP rule match]
Thu, 2008-06-19 00:12:02 - TCP Packet - Source:192.168.0.2,1295 Destination:82.9.17.55,80 - [HTTP rule match]
Thu, 2008-06-19 00:12:23 - TCP Packet - Source:192.168.0.7,1086 Destination:82.9.17.55,80 - [HTTP rule match]
Thu, 2008-06-19 00:12:58 - TCP Packet - Source:192.168.0.2,1315 Destination:82.9.17.55,80 - [HTTP rule match]
Thu, 2008-06-19 00:13:05 - TCP Packet - Source:192.168.0.2,1317 Destination:82.9.17.55,80 - [HTTP rule match]
Thu, 2008-06-19 00:13:19 - TCP Packet - Source:192.168.0.2,1368 Destination:82.9.17.55,80 - [HTTP rule match]
Thu, 2008-06-19 00:13:26 - TCP Packet - Source:192.168.0.2,1373 Destination:82.9.17.55,80 - [HTTP rule match]
Thu, 2008-06-19 00:21:07 - TCP Packet - Source:192.168.0.2,1454 Destination:82.9.17.55,80 - [HTTP rule match]
Thu, 2008-06-19 00:21:28 - TCP Packet - Source:192.168.0.2,1468 Destination:82.9.17.55,80 - [HTTP rule match]
Thu, 2008-06-19 00:28:02 - TCP Packet - Source:192.168.0.7,1095 Destination:82.9.17.55,80 - [HTTP rule match]
Thu, 2008-06-19 00:43:41 - TCP Packet - Source:192.168.0.7,1103 Destination:82.9.17.55,80 - [HTTP rule match]
Thu, 2008-06-19 05:05:25 - TCP Packet - Source:125.65.112.135,6000 Destination:82.9.17.55,80 - [HTTP rule match]
Thu, 2008-06-19 12:00:10 - <DDNS>IP address is the same, and does not need to be updated!
Thu, 2008-06-19 17:03:48 - TCP Packet - Source:189.139.57.248,13201 Destination:82.9.17.55,80 - [HTTP rule match]
Thu, 2008-06-19 20:21:43 - TCP Packet - Source:192.168.0.3,1431 Destination:86.131.80.124,49239 - [torrentflux rule not match]
Thu, 2008-06-19 20:27:33 - TCP Packet - Source:192.168.0.3,1431 Destination:86.131.80.124,49239 - [torrentflux rule not match]
Thu, 2008-06-19 21:12:47 - TCP Packet - Source:192.168.0.3,1431 Destination:86.131.80.124,49239 - [torrentflux rule not match]
Thu, 2008-06-19 22:09:04 - TCP Packet - Source:125.65.112.135,6000 Destination:82.9.17.55,80 - [HTTP rule match]
Fri, 2008-06-20 00:26:35 - TCP Packet - Source:82.51.151.252,62073 Destination:82.9.17.55,80 - [HTTP rule match]
Fri, 2008-06-20 05:09:20 - TCP Packet - Source:125.65.112.135,6000 Destination:82.9.17.55,80 - [HTTP rule match]
Fri, 2008-06-20 10:34:30 - TCP Packet - Source:210.51.23.7,2434 Destination:82.9.17.55,80 - [HTTP rule match]
Fri, 2008-06-20 14:23:12 - TCP Packet - Source:125.65.112.135,6000 Destination:82.9.17.55,80 - [HTTP rule match]
Fri, 2008-06-20 17:16:01 - TCP Packet - Source:192.168.0.3,2982 Destination:82.33.74.54,49216 - [torrentflux rule not match]
Fri, 2008-06-20 21:27:06 - TCP Packet - Source:125.65.112.135,6000 Destination:82.9.17.55,80 - [HTTP rule match]
Fri, 2008-06-20 21:41:03 - TCP Packet - Source:41.196.120.248,4163 Destination:82.9.17.55,80 - [HTTP rule match]
Sat, 2008-06-21 03:31:13 - TCP Packet - Source:85.96.116.115,2602 Destination:82.9.17.55,80 - [HTTP rule match]
Sat, 2008-06-21 04:58:24 - TCP Packet - Source:125.65.112.135,6000 Destination:82.9.17.55,80 - [HTTP rule match]
Sat, 2008-06-21 06:01:10 - TCP Packet - Source:90.51.96.236,4058 Destination:82.9.17.55,80 - [HTTP rule match]
Sat, 2008-06-21 07:16:52 - TCP Packet - Source:62.117.42.195,2862 Destination:82.9.17.55,80 - [HTTP rule match]
Sat, 2008-06-21 13:32:26 - Send out NTP request to time-g.netgear.com
Sat, 2008-06-21 13:32:29 - Receive NTP Reply from time-g.netgear.com
Sat, 2008-06-21 17:15:32 - Administrator login successful - IP:192.168.0.2
Sat, 2008-06-21 17:29:00 - Administrator login successful - IP:192.168.0.2
Sat, 2008-06-21 17:59:20 - Administrator login successful - IP:192.168.0.2
Sat, 2008-06-21 18:17:17 - Administrator login successful - IP:192.168.0.2
Sat, 2008-06-21 18:50:53 - Administrator login successful - IP:192.168.0.2
Sat, 2008-06-21 19:45:35 - TCP Packet - Source:89.212.6.194,4925 Destination:82.9.17.55,80 - [HTTP rule match]
Sat, 2008-06-21 21:16:52 - TCP Packet - Source:125.65.112.135,6000 Destination:82.9.17.55,80 - [HTTP rule match]
Sat, 2008-06-21 21:35:30 - TCP Packet - Source:192.168.0.2,3298 Destination:82.9.17.55,80 - [HTTP rule match]
Sat, 2008-06-21 22:14:12 - Administrator login successful - IP:192.168.0.2
Sat, 2008-06-21 22:41:47 - Administrator login successful - IP:192.168.0.2
Sun, 2008-06-22 04:21:23 - TCP Packet - Source:82.201.179.184,2998 Destination:82.9.17.55,23 - [DOS]
Sun, 2008-06-22 04:21:23 - TCP Packet - Source:82.201.250.46,3281 Destination:82.9.17.55,23 - [DOS]
Sun, 2008-06-22 04:21:23 - TCP Packet - Source:82.201.233.101,2450 Destination:82.9.17.55,23 - [DOS]
Sun, 2008-06-22 04:21:23 - TCP Packet - Source:82.201.253.63,2070 Destination:82.9.17.55,23 - [DOS]
Sun, 2008-06-22 04:21:23 - TCP Packet - Source:82.201.215.217,3292 Destination:82.9.17.55,23 - [DOS]
Sun, 2008-06-22 04:21:23 - TCP Packet - Source:82.201.233.55,3928 Destination:82.9.17.55,23 - [DOS]
Sun, 2008-06-22 04:21:23 - TCP Packet - Source:82.201.222.225,4480 Destination:82.9.17.55,23 - [DOS]
Sun, 2008-06-22 04:21:23 - TCP Packet - Source:82.201.221.107,2104 Destination:82.9.17.55,23 - [DOS]
Sun, 2008-06-22 04:21:23 - TCP Packet - Source:82.201.207.213,4978 Destination:82.9.17.55,23 - [DOS]
Sun, 2008-06-22 04:21:25 - TCP Packet - Source:82.201.249.40,3628 Destination:82.9.17.55,23 - [DOS]
Sun, 2008-06-22 04:21:26 - TCP Packet - Source:82.201.250.46,3281 Destination:82.9.17.55,23 - [DOS]
Sun, 2008-06-22 04:21:26 - TCP Packet - Source:82.201.233.101,2450 Destination:82.9.17.55,23 - [DOS]
Sun, 2008-06-22 04:21:26 - TCP Packet - Source:82.201.253.63,2070 Destination:82.9.17.55,23 - [DOS]
Sun, 2008-06-22 04:21:26 - TCP Packet - Source:82.201.215.217,3292 Destination:82.9.17.55,23 - [DOS]
Sun, 2008-06-22 04:21:26 - TCP Packet - Source:82.201.233.55,3928 Destination:82.9.17.55,23 - [DOS]
Sun, 2008-06-22 04:21:26 - TCP Packet - Source:82.201.222.225,4480 Destination:82.9.17.55,23 - [DOS]
Sun, 2008-06-22 04:21:26 - TCP Packet - Source:82.201.221.107,2104 Destination:82.9.17.55,23 - [DOS]
Sun, 2008-06-22 04:21:26 - TCP Packet - Source:82.201.207.213,4978 Destination:82.9.17.55,23 - [DOS]
Sun, 2008-06-22 04:21:32 - TCP Packet - Source:82.201.179.184,2998 Destination:82.9.17.55,23 - [DOS]
Sun, 2008-06-22 04:21:32 - TCP Packet - Source:82.201.250.46,3281 Destination:82.9.17.55,23 - [DOS]
Sun, 2008-06-22 04:21:32 - TCP Packet - Source:82.201.233.101,2450 Destination:82.9.17.55,23 - [DOS]
Sun, 2008-06-22 04:21:32 - TCP Packet - Source:82.201.253.63,2070 Destination:82.9.17.55,23 - [DOS]
Sun, 2008-06-22 04:21:32 - TCP Packet - Source:82.201.215.217,3292 Destination:82.9.17.55,23 - [DOS]
Sun, 2008-06-22 04:21:32 - TCP Packet - Source:82.201.233.55,3928 Destination:82.9.17.55,23 - [DOS]
Sun, 2008-06-22 04:21:32 - TCP Packet - Source:82.201.221.107,2104 Destination:82.9.17.55,23 - [DOS]
Sun, 2008-06-22 04:21:32 - TCP Packet - Source:82.201.207.213,4978 Destination:82.9.17.55,23 - [DOS]
Sun, 2008-06-22 04:50:51 - TCP Packet - Source:125.65.112.135,6000 Destination:82.9.17.55,80 - [HTTP rule match]
Sun, 2008-06-22 07:26:17 - TCP Packet - Source:85.107.42.189,2094 Destination:82.9.17.55,80 - [HTTP rule match]
Sun, 2008-06-22 09:51:58 - Administrator login successful - IP:192.168.0.2
```

My Dad received a virus a while ago to. He tried to delete a spam post off one of our forums ( served from a datacentre ) and he viruses wre downloaded. We thought some malicious code had been installed on the forum but maybe it was because of this.
We have a lot of data on our network which is mainly windows
What do these logs show? Has someone got in? What happened with that DOS attack? Did it knock my firewall or is it o.k?
What shall I do?
Thanks

edit: some of them are from asia to. did they get in? the last 2 say 'rule match'...

---

### Post by alastair on 2008-06-22
A Netgear router/firewall? Like mine.

The "rule match" is the firewall letting the port 80 through.
The "DOS" is the firewall blocking DOS packets i.e. firewall working.

I see a lot of this earlier this month (13-14 June 2008). I don't know why but no harm done - the packets are blocked. As to the web server requests (port 80), maybe check the web server access/error logs and see what the requests were. Probably no harm done there either.

Alastair

---

### Post by garethsimpsonuk on 2008-06-22
Yea it's a netgear. The thing is no-one should be accessing port 80 but me. I haven't had my server connected lately so where would thety be going. 
The thing I'm worried about is that an IP tried dossing me, then lateer on they get a 'rule match' does that mean they got in? 
I don't have them logs because my servers not been on. How do I access them for future reference? 
Do you know of a good how to for home server security?
I have a dyndns then a .co.nr redirector but I don't think it was me accessing my server on port 80. ( i usually used the lan address )
That's why I'm worried that someones been let through a few times.
Thanks for the reply

---

### Post by spiderbatdad on 2008-06-22
If you have a port forwarded by your router, you are going to have hits on it...it is as simple as that. It doesn't mean anyone "got in." It means a request was made. Your error and access logs should show you what request was made and what the response was.

There is no cloak of security out there that will let you have a forward facing server and keep the world out at the same time. Furthermore whatever security you manage to implement is not just set up and good to go...security is a process...companies spend tens to hundreds of thousands of dollars maintaining and monitoring security. Your best bet is to have a dedicated server and learn little by little about security...there is way too much to know to just read through a book or two and be all set. And you'll always be one step behind hackers anyway.

---

### Post by garethsimpsonuk on 2008-06-22
Yeah I'm learning all the time like everyone else. I'm a web designer not an admin and I've spent the last 2 months educating myself with linux servers. I had port 80 forwarded to my servers ip I planned for only a select few ( family ) to access the server. I thought if I never put a link anywhere to my server then it would never be spidered and therefore visible. I assumed that if my i.p is not known then no one would usually get to it without specifically looking. How do they do it? Is it just port scanning random IP ranges?
As I said before I can see where the request was blocked ( or not answered ) but there is a couple where 'rule match' is apparent does that mean they got in? My server wasn't on at the time ( where port 80 was forwarded ) so where would the request have gone? What happens when a firewall forward rule is routed to a computer that isn't on? Which is what happened. 
I understand that I have to learn a lot before being reasonably safe so I'm asking where can I learn this? I just need confirmation that everything is o.k. 
Like I said I wont have logs if the server was off. For now I have blocked all ports as my samba isn't safe but I will ( maybe not as soon as I expected ) open up again. Here is what I know to do:-

- reroute all common ports to random ones ( only close family will access this server so is it o.k to reroute port 80 to a random one, then access with [http://url:portnumber](http://url:portnumber) )

- I know of keyrings, I would like to carry a key on usb so only I / whoever has key can access the server

- SSH tunnell can I access a hosted website via SSH?

- Restrict IP's. Not viable for me, can I restrict to just my pda's mac address?

- I heard of port knocking, where a port is opened by using a 'secret knock'

- My bittorrent ports will be open, what can I do about them?

Any help would be great although I am a great advocate of 'google it'. Tell me what I should research / point me in the right direction and I'll be fine.

Thanks for the replies,
Gareth

---

### Post by fahadsadah on 2008-06-22
You could set the webserver to listen on a randomised port, well over 10000.
You could also password protect the webpage.
As for the BT ports, there is nothing you can do. You need these open, full stop.

---

### Post by spiderbatdad on 2008-06-22
For apache setting up .htaccess is fairly easy. Also having apache run from an unprivileged user account with no shell access is fairly easy. Though none of this is 100% effective. The requests you mention, were most likely silently dropped. "webalizer" might interest you for monitoring access to your server. It is doubtful that you offer much of a target to potential crackers. Chrooting your server is another option, but it is difficult, has to be done during compilation, and is statically configured...so any module changes, etc, require re-compiling...a real pain.

As for bit torrent...no clue...if you're paranoid about being hacked, don't use bit torrents. For that matter don't put any holes in your firewall...turn your computer off, and disconnect all cables...LOL.

:)


Looking back at your question...you asked about random port scan...IDK. But if you are running your server on the same machine you use to surf and make http requests with, then it isn't really random. Think of it as...you knock on a door, and the person inside looks out through a peep hole. When you visit a site, you are requesting information. The same site can make a request of your computer. If the port is open and the computer is configured to handle the request, then information passes. It may be nothing more than image files and text that comprise your http index.

---

