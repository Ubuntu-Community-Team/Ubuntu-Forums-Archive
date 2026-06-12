---
title: "Problems connecting to cups"
date: 2008-02-09
forum: General Help
---

### Post by matti_bauer on 2008-02-09
Hello,
I'm using Ubuntu 7.10 and I have trouble connecting to cups from other computers. The connection can be established but there are really long waiting times involved. For example when i try to access [http://192.168.1.9:631](http://192.168.1.9:631) 

On the client side i tried Ubuntu 7.10, Windows XP and MacOS X 10.4.

I turned LogLevel in "cupsd.conf" to "debug". There i could see, that after each occurance of "cupsdAcceptClient" a pause of exactly 20 seconds before the next entry appears. So it looks to me like cups is waiting for some kind of timeout.

This is an example:
```
[09/Feb/2008:19:17:12 +0100] cupsdAcceptClient: 19 from 192.168.1.10:631 (IPv4)
D [09/Feb/2008:19:17:32 +0100] cupsdNetIFUpdate: "lo" = localhost...
D [09/Feb/2008:19:17:32 +0100] cupsdNetIFUpdate: "ath0" = 192.168.1.9...
D [09/Feb/2008:19:17:32 +0100] cupsdNetIFUpdate: "lo" = localhost...
D [09/Feb/2008:19:17:32 +0100] cupsdNetIFUpdate: "ath0" = fe80::209:5bff:fee7:1521%ath0...
D [09/Feb/2008:19:17:32 +0100] cupsdAcceptClient: 20 from 192.168.1.10:631 (IPv4)
D [09/Feb/2008:19:17:52 +0100] cupsdReadClient: 19 GET /classes/ HTTP/1.1
D [09/Feb/2008:19:17:52 +0100] cupsdAuthorize: No authentication data provided.
D [09/Feb/2008:19:17:52 +0100] [CGI] /usr/lib/cups/cgi-bin/classes.cgi started - PID = 6327
I [09/Feb/2008:19:17:52 +0100] Started "/usr/lib/cups/cgi-bin/classes.cgi" (pid=6327)
D [09/Feb/2008:19:17:52 +0100] cupsdSendCommand: 19 file=22
D [09/Feb/2008:19:17:52 +0100] cupsdReadClient: 20 GET /classes/ HTTP/1.1
D [09/Feb/2008:19:17:52 +0100] cupsdAuthorize: No authentication data provided.
D [09/Feb/2008:19:17:52 +0100] [CGI] /usr/lib/cups/cgi-bin/classes.cgi started - PID = 6328

```

What could be the cause of this? 

thank you in advance
matti

---

### Post by matti_bauer on 2008-02-10
i have some more information that may help. I used to have a similar problem with ssh. It took a long time between the start of the programme and the password prompt. And I just confirmed, that this were exactly 20 seconds, too.

sshd paused on a message that said: "Trying to reverse map address 192.168.1.10"

But I was able to fix this problem by adding 192.168.1.10 to /etc/hosts. Obviously some reverse DNS lookup failed to respond. But I don't know what the actual cause was. And this fix doesn't help cups. 

thanks in advance
matti

---

### Post by matti_bauer on 2008-02-10
okay.. here is the current result of my ongoing research: everything works fine if i connect the two computers directly via cable or if i set the nameserver in "resolv.conf" to something like "localhost".

So its probably a DNS-problem? I read that the ssh-problem may be related to a buggy DNS-implementation in some routers. 

Does anyone have an idea what I can do about this? Maybe disable this unnecessary check, that cups obviously performs before connecting?

I hope, someone can help me with this.... its  getting frustrating.. 

thanks
matti

---

### Post by matti_bauer on 2008-02-10
me again.. i had a look at the cups sourcecode to find out, where the waiting is happening... 


in cups/http-addr.c:
```
    if (getnameinfo(&addr->addr, httpAddrLength(addr), name, namelen,
		    NULL, 0, 0))
      return (httpAddrString(addr, name, namelen));
```

it takes getnameinfo 20 seconds to return: Temporary failure in name resolution.

I deleted the first to lines and now it works perfect. 
But i don't like having my own version of cups. 

bye
chris

---

