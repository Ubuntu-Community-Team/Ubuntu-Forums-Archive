---
title: "Running rdesktop through a SSH tunnel - unable to connect :("
date: 2013-03-26
forum: General Help
---

### Post by b0rre on 2013-03-26
Hi, i'm trying to connect to my windows machine at home by tunneling RDP traffic through a SSH tunnel from a remote network, but it doesn't work. In my home network i also have a Raspberry Pi (with dynDNS) running and I'm trying to use the PI to reach my windows machine. My router is configured to forward all incoming SSH request to the PI.

I've been googling a lot, but i cannot see why the following commands fails:

from a remote network with my laptop, open terminal window #1: ssh <my dyndns address> -p 22 -L 3392:10.0.0.20:3389

after logged in to the PI, open terminal window #2 from laptop: rdesktop 10.0.0.20:3392 -u <my user name>

where 10.0.0.20 is the IP address to my windows machine. 

Output from terminal window #2:

Autoselected keyboard map en-us
ERROR: 10.0.0.20: unable to connect

I'm not sure why this is failing as i can telnet to 10.0.0.20 on port 3389 FROM my PI (which is located in the same network as my windows machine). 

Please advice.

Thanks:)

---

### Post by The Cog on 2013-03-26
You need to be connecting to your laptop with RDP, which will then forward it to the windows machine. Try this rdesktop command on your laptop instead:
rdesktop 127.0.0.1:3392 -u <my user name>

Incidentally, your laptop only needs to accept connections from itself so it only needs to listen on 127.0.0.1. That prevents other people connecting to (through) your laptop to your home windows.
And port 22 is the default so you don't need to specify it:
 ssh <my dyndns address> -L 127.0.0.1:3392:10.0.0.20:3389

---

### Post by b0rre on 2013-03-26
> **The Cog said:**
> You need to be connecting to your laptop with RDP, which will then forward it to the windows machine. Try this rdesktop command on your laptop instead:
rdesktop 127.0.0.1:3392 -u <my user name>

Incidentally, your laptop only needs to accept connections from itself so it only needs to listen on 127.0.0.1. That prevents other people connecting to (through) your laptop to your home windows.
And port 22 is the default so you don't need to specify it:
 ssh <my dyndns address> -L 127.0.0.1:3392:10.0.0.20:3389

Hi,

thanks for the quick reply and detailed explanation:) Much appreciated! 

I've just tried what you said, but i still get the same error message:( Perhaps my windows machine is acting weird, and just needs a reboot :P However, a work around would be to access my router and add my currently remote IP address to the configuration. Can this be done with tunneling as well?

---

### Post by The Cog on 2013-03-26
> I've just tried what you said, but i still get the same error message 
You mean "ERROR: 127.0.0.1: unable to connect" ? I don't understand that. 
While the tunneling ssh connection is logged in, can you do ```
netstat -lnt
``` and post the results here. You should see a listening socket on port 3392.

---

### Post by b0rre on 2013-03-26
> **The Cog said:**
> You mean "ERROR: 127.0.0.1: unable to connect" ? I don't understand that. 
While the tunneling ssh connection is logged in, can you do ```
netstat -lnt
``` and post the results here. You should see a listening socket on port 3392.

I get:

"Autoselected keyboard map en-us
ERROR: Connection closed"

Which is not the same message as above. Sorry about that :(

Did a netstat while the tunnel was up and running (as requested):

:~$ netstat -lnt
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:45144         0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:17500           0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:3392          0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:55563           0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:111             0.0.0.0:*               LISTEN     
tcp6       0      0 ::1:631                 :::*                    LISTEN     
tcp6       0      0 :::51466                :::*                    LISTEN     
tcp6       0      0 :::111                  :::*                    LISTEN     


3392 is listening.

---

### Post by b0rre on 2013-03-26
Hm, i'm currently connected to internet through my iPhone, but i guess that should not affect the outcome?

---

### Post by The Cog on 2013-03-27
I don't think running the internet through your phone should be the problem. But the problem has changed form being unable to connect to being rejected for some reason. I think the RDP connection was at least accepted by your laptop. It should have tunneled through to the pi and the the pi should have tried to connect to the windows PC. Deciding which part of the chain is broken could be difficult. 

* Do any error messages appear on the original ssh login terminal while you are trying to connect with the rdp session?

* What error message to you see if you use this command instead of the rdp command?:
```
telnet 127.0.0.1 3392
```
If it appears to connect OK, (it prints "Escape character is '^]'.") then does is disconnect as soon as you press Enter?

---

### Post by b0rre on 2013-03-28
> **The Cog said:**
> I don't think running the internet through your phone should be the problem. But the problem has changed form being unable to connect to being rejected for some reason. I think the RDP connection was at least accepted by your laptop. It should have tunneled through to the pi and the the pi should have tried to connect to the windows PC. Deciding which part of the chain is broken could be difficult. 

* Do any error messages appear on the original ssh login terminal while you are trying to connect with the rdp session?

* What error message to you see if you use this command instead of the rdp command?:
```
telnet 127.0.0.1 3392
```
If it appears to connect OK, (it prints "Escape character is '^]'.") then does is disconnect as soon as you press Enter?


It does not disconnect when i press Enter.

Edit: I've just got a hold of a windows machine. RDP to my home windows machine works just fine. Perhaps rdesktop is picky regarding the arguments (e.g. rdesktop <arguments>)?  I thought rdesktop -u <nick> would be sufficient?
Edit^2: works with remmina. I'll stick to that.

---

