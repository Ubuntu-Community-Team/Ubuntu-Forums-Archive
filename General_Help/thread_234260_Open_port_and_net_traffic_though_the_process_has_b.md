---
title: "Open port and net traffic though the process has been killed"
date: 2006-08-11
forum: General Help
---

### Post by timetunnel on 2006-08-11
Hi,
I have been running aMule for only a few minutes and completely quit it. No aMule process is running anymore. However, I can still see net traffic in the GNOME system monitor. Starting Firestarter shows that there's still an open connection on port 4662 (which is the aMule port I configured).

I tried the following, but to my surprise all returned nothing:
```
netstat | grep 4662 lsof -i :4662
```
If I start aMule, the following commands return:
```
:~$ lsof -i :4662
amule   11518 username   15u  IPv4 142937       TCP *:4662 (LISTEN)

:~$ netstat | grep 4662
tcp        0      0 192.168.1.2:4662        toronto-HSE-ppp42:61748 TIME_WAIT
tcp        0      0 192.168.1.2:4662        140.115.152.69:1394     TIME_WAIT
tcp        0      0 192.168.1.2:4662        adsl-220-229-149-:28564 TIME_WAIT
tcp        0  15972 192.168.1.2:60225       chello084010173009:4662 VERBUNDEN
tcp        0    138 192.168.1.2:4662        mar44-3-82-235-65-:4995 VERBUNDEN
tcp        0    498 192.168.1.2:55097       p54A32C3A.dip0.t-i:4662 VERBUNDEN
```
(VERBUNDEN means CONNECTED)

Can anybody help me understand what's going on here? How can the port still be open and download/upload stuff when the process that opened the port and started the download has been killed? Has my computer been hijacked?

Thanks

---

### Post by kvonb on 2006-08-11
Sorry I can't be of too much help as I don't use amule, however I would recommend trying a process listing, ie ps uax to see what processes are running.  Also have you tried to run amule again from the icon?  It might pickup where it left off, maybe an X problem but the daemon is still running.

If no luck, kill the amule process (kill -9 <process#> ), then run amule from a terminal to see the output for any errors.  Also try: amule --?  or man amule  It might give some help.

Hope it works!

Regards,  Kev :)

---

### Post by timetunnel on 2006-08-12
Thanks for your reply, but it doesn't help me. I already wrote in my initial post that the amule process is *not running* anymore when the problem occurs. There's no amule daemon as well. And "netstat" doesn't even report the open amule port but Firestarter does. 

I'd really like to know if I've got a security problem here (Rootkit?)

Anyone?

---

### Post by chonger on 2006-08-14
It is possible those sockets are in a TIME_WAIT state. 

After you close aMule (or any other "servers"), you may run as root,

```
netstat -tnp 
```

-t = TCP connections
-n = Do not use DNS to resolve IPs
-p = Show pid

And look for any tcp connections that are still in the TIME_WAIT state. You'll see that the PID is not there (the process has terminated), but Linux will still obey TCP rules and sit in TIME_WAIT until that socket can be safely closed.

See this document for more information:

[http://www.tcpipguide.com/free/t_TCPConnectionTermination-2.htm](http://www.tcpipguide.com/free/t_TCPConnectionTermination-2.htm)

The only thing I find curious is that you say running netstat after aMule has terminated showed no sockets in the TIME_WAIT state. Really netstat should be showing them.

---

