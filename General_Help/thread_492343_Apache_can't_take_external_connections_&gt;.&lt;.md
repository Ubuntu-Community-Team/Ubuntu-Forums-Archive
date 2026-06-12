---
title: "Apache can't take external connections &gt;.&lt;"
date: 2007-07-04
forum: General Help
---

### Post by Chake99 on 2007-07-04
Alright I've been trying to work on a website on my home computer to teach myself something.

I've installed Apache2 ([http://localhost](http://localhost) works), PHP5 (works according to PHPinfo test), MySQL, PHPMyAdmin (works, meaning MySQL works too). Anyways, I've gone into my router settings and told it to redirect connections on port 80 to my computer, and I've put a very simple html file in my /var/www called index.html so when people go [http://myIP/](http://myIP/) it should display that page on their browser, right?

[http://70.48.13.214](http://70.48.13.214)

Everyone I've asked says it times out. 

I've started apache2 with this command someone gave me on IRC: >  sudo /usr/sbin/apache2ctl start 

And it seems to start up (typing it twice says it has already started,

but typing apache2 or sudo apache2 returns: ```

pyrotix@monolith:~$ sudo apache2
(98): make_sock: could not bind to address [::]:80
no listening sockets available, shutting down
Unable to open logs 
```
???

Anyways, anyone have any idea what I have to do to get apache2 to accept external connections?

---

### Post by gustolove on 2007-07-04
Many ISPs Block port 80...

I know mine does (Cox) and I know Quest, AT&T and others also do. Unless you have their business package...

So it may just be that your ISP is blocking... Try changing the port to 8080 or 81-- and then try

[http://70.48.13.214:8080](http://70.48.13.214:8080)

OR

[http://70.48.13.214:81](http://70.48.13.214:81)

-- and don't forget the forwarding for that port on your router also..

Good luck --

EDIT:

I forgot to tell you how to change the port for apache... Whoops
```

sudo gedit /etc/apache2/ports.conf

```
It will say "Listen 80" change that to "Listen 81" or whatever port you choose...

---

### Post by Chake99 on 2007-07-04
Changes made to [http://70.48.13.214:81](http://70.48.13.214:81) . According to people on IRC still doesn't work :(. Any other ideas?

---

### Post by altonbr on 2007-07-04
Use this to start and stop apache:
```
sudo /etc/init.d/apache [start/stop]
```

On your server, can you try this:
```
ping -c4 google.ca
```

Is your server also your desktop?
What does ifconfig say?
```
ifconfig
```

Are you sure you enabled NAT or Port Forwarding on port 80 to that exact address? Sometimes there is a check box beside it, allowing you to enable or disable it.

What does travelling to: [http://whatismyip.org/](http://whatismyip.org/) say?

Give me that information and then I will give you more advanced debugging tools.

Lastly, I nmaped your IP of (70.48.13.214) and it said that you had no ports open - of course, this can also mean that your server/computer is turned off. Is this IP dynamic? Are you on DSL or cable?

---

### Post by Chake99 on 2007-07-04
Pinging google returns
```

pyrotix@monolith:~$ ping -c4 google.ca
PING google.ca (64.233.187.104) 56(84) bytes of data.
64 bytes from jc-in-f104.google.com (64.233.187.104): icmp_seq=1 ttl=243 time=81.1 ms
64 bytes from jc-in-f104.google.com (64.233.187.104): icmp_seq=2 ttl=243 time=79.5 ms
64 bytes from jc-in-f104.google.com (64.233.187.104): icmp_seq=3 ttl=243 time=79.9 ms
64 bytes from jc-in-f104.google.com (64.233.187.104): icmp_seq=4 ttl=243 time=79.9 ms

```

Yes I'm trying to set up my desktop as a server

ifconfig returns:
```

ath0      Link encap:Ethernet  HWaddr 00:15:E9:2B:4E:AC
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::215:e9ff:fe2b:4eac/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:129328 errors:0 dropped:0 overruns:0 frame:0
          TX packets:105981 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:108447577 (103.4 MiB)  TX bytes:10878287 (10.3 MiB)

eth0      Link encap:Ethernet  HWaddr 00:0C:6E:7A:7F:0B
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:6eff:fe7a:7f0b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3443 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1273 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1504616 (1.4 MiB)  TX bytes:124385 (121.4 KiB)
          Interrupt:185 Base address:0xc000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1143 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1143 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1334278 (1.2 MiB)  TX bytes:1334278 (1.2 MiB)

wifi0     Link encap:UNSPEC  HWaddr 00-15-E9-2B-4E-AC-00-00-00-00-00-00-00-00-00-00
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2067413 errors:0 dropped:0 overruns:0 frame:541252
          TX packets:110965 errors:55 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199
          RX bytes:279057617 (266.1 MiB)  TX bytes:13423500 (12.8 MiB)
          Interrupt:201 Memory:ecb00000-ecb10000

```

NAT or Portforwarding to what address from ifconfig? There are three different addresses from the CLI response to ifconfig that I could tell my router to forward to. I told my router to forward ports 80-81 for both TCP and UDP to 192.168.1.100 (the numbers after the last period being the only ones editable, although as your portscan failed it is undoubtedly wrong)

what is my IP gives 70.48.13.214

No, my server is not turned off, it is the computer I'm posting from. Yes my IP is dynamic (although according to whatismyIP sites it has not changed over the course of my trying to set up apache) and I'm on DSL.

No ports open? There are about 7 ports I have opened for various reasons (although I do not recall them working recently), I assume they are not forwarding to my computer. What of the addresses given by ifconfig should I have my router forward to?

Thanks in advance.

---

### Post by altonbr on 2007-07-05
Ahh perfect, I think I found your problem:

> eth0 ...
... addr:192.168.1.102 ...

You said you have port 80 and 81 forwarding to *.100? Try *.102 and see what you get. 'eth0' is your main wired network.

---

