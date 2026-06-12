---
title: "Why por t 32770 is open."
date: 2005-10-17
forum: General Help
---

### Post by nmarmol on 2005-10-17
Hello.

I'm installed ubuntu breezy and it is a rock.

I executed a command 'nmap localhost' and appears this

Starting nmap 3.81 ( [http://www.insecure.org/nmap/](http://www.insecure.org/nmap/) ) at 2005-10-17 08:23 AST
Interesting ports on localhost.localdomain (127.0.0.1):
(The 1661 ports scanned but not shown below are in state: closed)
PORT      STATE SERVICE
631/tcp   open  ipp
[B]32770/tcp open  sometimes-rpc3
[/B]

My question is:  Why port 32770 is open?  What'is the use of this port?

Regards
Nelson

---

### Post by plumcreek on 2005-10-17
[quote=nmarmol]My question is:  Why port 32770 is open?  What'is the use of this port?[/quote] 
Your nmap output says that the service is: **sometimes-rpc3** and I have no idea what that is, what it is used for, or why the port is open.

Normally, the best place to look for what the different port assignments are is here: [http://www.iana.org/assignments/port-numbers]("http://www.iana.org/assignments/port-numbers")

For port 32770, it gives the following information:
```
filenet-nch     32770/tcp   Filenet NCH
filenet-nch     32770/udp   Filenet NCH
#                           Daniel Whelan <dwhelan@filenet.com>
``` 
Ports 1024 through 49151 are what are known as *registered ports*. Which means that someone has gone to the trouble to register it with IANA, which is what Filenet seems to have done with port 32770.

Of course, that doesn't mean that that is what the port is being used for, just what the port is *registered* for (and your nmap output says that the port is being used for **sometimes-rpc3**, whatever that is). For example, telent is reserved for port 23, but I can telnet to port 80 (normally http) **if** my telnet server is set to listen on that port (and my http server is turned off or assigned to a different port). Most server daemons can be set to non-standard ports, if not all. I have no idea what filenet-nch is, BTW.

---

### Post by nmarmol on 2005-10-17
Thansk for respond.  But my question is still open.

I telnet localhost 32770

Trying 127.0.0.1...
Connected to localhost.localdomain.
Escape character is '^]'.
<ENTER>
msg=messageerror
result-code=5

What happend?.  I don't want security hole  in my workstation or my server.  What is the result if i close the port?  Please, ubuntu developers should have to know why this port is open?

Regards
Nelson

---

### Post by Confuse on 2005-10-17
Weird, I have it too. Think its an app we both have running NOT by default?

---

### Post by dracnor on 2005-10-17
Seems to be running here too.  If you do 

```
sudo netstat -nap | grep 32770
```

you will see:

```
tcp        0      0 127.0.0.1:32770         0.0.0.0:*               LISTEN     7229/hpiod 
tcp        0      0 127.0.0.1:32770         127.0.0.1:51867         ESTABLISHED7229/hpiod 
```

So I googled hpiod, and it looks like it is for the [HP Linux Imaging and Printing System]("http://www.linuxprinting.org/pipermail/inkjet-list/2005q1/000637.html").

---

### Post by suoko on 2005-10-28
I also was wondering what those open ports were:

32770/tcp open  sometimes-rpc3
32771/tcp open  sometimes-rpc5

and I can tell you I have hplip installed as well so that could be the door opener

---

### Post by drgonzo69 on 2005-11-24
Try and run 'netstat -tnp' on the command line. The -n option will return the IP addresses and numerical port names, the -p will show the program that open the port and the -t will only show tcp connections. 

On my machine I get:

tcp        0      0 127.0.0.1:32770         127.0.0.1:37852         ESTABLISHED9089/python
tcp        0      0 127.0.0.1:37852         127.0.0.1:32770         ESTABLISHED9104/python

Because I run eric - a Python QT IDE that uses the ports 32770 37852 for debugging. You might have something else...

---

### Post by towsonu2003 on 2005-11-24
127.0.0.1 is loopback. to confirm: ```
sudo ifconfig
``` will bring this (or similar): ```
**lo**        Link encap:Local Loopback
          inet addr:**127.0.0.1**  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:25944 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25944 errors:0 dropped:0 overruns:0 carrier:0https://www.grc.com/x/ne.dll?bh0bkyd2
          collisions:0 txqueuelen:0
          RX bytes:1070920 (1.0 MiB)  TX bytes:1070920 (1.0 MiB)

```

lo is loopback and corresponds to 127.0.01 ip address. same for you? 

It is closed to outside (any other than your own computer itself) traffic. So it nothing. 

But, for the record, I have sometimes-rpc3 as well :) don't care for now as long as it's on loopback... 

Best security check is either nmap (or better yet, nessus) scanning your machine from someone else's using your ip as target, or go to this site (usually reliable) and make it scan you: [https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2) that will show you open port to the **net**. good luck...

---

