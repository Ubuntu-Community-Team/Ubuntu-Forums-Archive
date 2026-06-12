---
title: "PC not recognised from Router"
date: 2006-12-20
forum: General Help
---

### Post by rado_london on 2006-12-20
Hey people
Just got a new PC from my college so I will run a server on it. I installed everything and when I tried to run apache I ended up with the following error:
```
root@server-ubuntu:/home/server#  /usr/sbin/apache2ctl start
(98)Address already in use: make_sock: could not bind to address 127.0.0.1:80
no listening sockets available, shutting down
Unable to open logs

```

I edited all the configuration files that must be edited. I dont know where my error is. But I found something weird. I am behind a router and often check who is attached. Now this PC is not listed as attached device which  looked rather strange to me.
Well people any way I can get apache up and running?

Best Regards and Merry Christmas
Radoslav Petsov

---

### Post by rado_london on 2006-12-21
Bump!!!

---

### Post by koenn on 2006-12-21
your problem is similar to this one : [http://www.ubuntuforums.org/showthread.php?t=307986](http://www.ubuntuforums.org/showthread.php?t=307986)
although it's about lighttpd and you're using apache, the solution is also similar :

- check that your pc indeed has an ip address (run ifconfig)
- make sure the webserver is conbfigured to listen at this address (edit apache config file)

---

### Post by rado_london on 2006-12-21
> **koenn said:**
> your problem is similar to this one : [http://www.ubuntuforums.org/showthread.php?t=307986](http://www.ubuntuforums.org/showthread.php?t=307986)
although it's about lighttpd and you're using apache, the solution is also similar :

- check that your pc indeed has an ip address (run ifconfig)
- make sure the webserver is conbfigured to listen at this address (edit apache config file)

How do I edit the config file? I mean what line to edit.
Here is the output of ifconfig:
```
root@server-ubuntu:/home/server# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:50:BA:BD:1A:B5
          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::250:baff:febd:1ab5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:130705 errors:0 dropped:0 overruns:0 frame:0
          TX packets:98901 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:159333063 (151.9 MiB)  TX bytes:10638916 (10.1 MiB)
          Interrupt:193 Base address:0x6c00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3657 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3657 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:391557 (382.3 KiB)  TX bytes:391557 (382.3 KiB)

```

My ip address from [www.whatismyip.com](www.whatismyip.com) is 82.27.199.134. Hope you now have enough info to help me out:)

Cheers

---

### Post by Halcy0n on 2006-12-21
The error you are giving suggests that you already have something running and bound to port 80.  Do you have any other web servers running?  Is apache maybe running in the background already?

---

### Post by rado_london on 2006-12-21
> **Halcy0n said:**
> The error you are giving suggests that you already have something running and bound to port 80.  Do you have any other web servers running?  Is apache maybe running in the background already?

Fixed it. Went to the router config and changed port 80 to be open for 192.168.0.3 instead of the  old 192.168.0.2. I found it is .3 in the ifconfig. Now my site is up and you can check it out on [www.maxstorage.tk](www.maxstorage.tk)
Still not installed but will do tonight

Thanks alot for the help

This was your first post it was so helpful:)
I hope all your posts are as helpfull as this one:D

---

