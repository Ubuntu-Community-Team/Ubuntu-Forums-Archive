---
title: "openssh connection refused"
date: 2008-05-15
forum: General Help
---

### Post by poomalairaj on 2008-05-15
hi all,

Today i have installed ubuntu hardy and openssh.
when i try to connect to my ubuntu box by using the command 
```
ssh -p 33  poomalai.homelinux.com
```  (this is dyndns address)
It says,
```
ssh: connect to host poomalai.homelinux.com port 33: Connection refused.
```

I tried to connect to my machine using public  ip too. (found it using whatismyip.com) but same error.

But i am able to connect to my machine by using ssh -p 33 192.168.1.5

I have following firewall rules:

```

To                         Action  From
--                         ------  ----
22:tcp                     ALLOW   Anywhere
22:udp                     ALLOW   Anywhere
33:tcp                     ALLOW   Anywhere
33:udp                     ALLOW   Anywhere
5800:tcp                   ALLOW   Anywhere
5800:udp                   ALLOW   Anywhere
5900:tcp                   ALLOW   Anywhere
5900:udp                   ALLOW   Anywhere
```

I have set up my router to forward ports 22 and 33 and 80.
Actually i am able to forward port 80 in my router. (I was able to access my website) So there is no problem with my router.

I was using ssh in ubuntu gusty and there was no problem.
But now i am not able to access my machine through SSH. 

Please anyone help me.

Thanks in advance
Poomalairaj

---

### Post by eldragon on 2008-05-15
have you set the port in sshd.conf?

otherwise, try port 22.

---

### Post by bodhi.zazen on 2008-05-15
Works fine here :

> bodhi@ubuntu:~$ ssh poomalai.homelinux.com -p 33
**[color=red]bodhi@poomalai.homelinux.com's password:     [/color]**

---

### Post by s.l.i.m on 2010-02-22
i have the same problem

when i type :

```

ssh -p 27 bhiri@192.168.1.4

```

it works perfectly

but when i type :

```

ssh -p 27 bhiri@bhiri.dyndns.ws

```

it doesn't work. 

i have also tried :

```

ssh bhiri@bhiri.dyndns.ws -p 27
 **and**
 ssh bhiri.dyndns.ws -p 27

```

and still the same problem.

i have tried also with my adresse ip directly without the dyndns adresse but i still have the same error.

---

### Post by gmargo on 2010-02-22
Check to see if the secure shell daemon is listening on all interfaces or just on the localhost interface.```
  netstat -ln | egrep ":22|:27|Recv"
```

---

### Post by bodhi.zazen on 2010-02-22
You may also need to forward port 27 from your router to your server.

---

### Post by mahela007 on 2010-03-03
Hi everyone!
I'm having the same problem. COuld y'all help me solve it? Here's what the command in post #5 gives
```
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN     
tcp6       0      0 :::22                   :::*                    LISTEN   
```The funny thing is that this worked very well yesterday. I was able to login by using the IP adress of my router. (So I'm guessing it's not an issue with port forwarding).
Since I'm still testing my setup, both computers are connected to the same router and I'm using key based logins.

---

### Post by mbaas on 2010-03-03
Hi,

Are you trying to reach your external IP adress from within your LAN? Not all routers support loopback connections (connecting from behind your router to the internet (WAN) and then back in to the LAN again).

---

### Post by mahela007 on 2010-03-03
Yup.. that's what I was trying. Maybe my router doesn't support this. Thanks for the tip. 
By the way, I tried connecting from another connection (i.e a wireless modem) to my ssh server. Whenever I give it the IP address it works. However, when I provide the ssh client with  the _dyndns_ name of my server name it gives me a similar  'connection refused error'.

---

### Post by troll1602 on 2010-03-14
I keep getting a similar "connection refused". It happens while trying to access my home computer which has a dynamic dns. I'm going through port 22 and my firewall/router haven't prevented access in the past.

I'm not sure to the cause, but everytime I reinstall openssh-server, the problem goes away for a few weeks. However the problem does keep coming back.

Hopefully this info helps :)

---

### Post by asmoore82 on 2010-03-14
I've seen a problem with routers before,
My old compaq one couldn't "loop-forward" the ports from inside to the external IP and back inside.
But my current Dlink doesn't care.

---

