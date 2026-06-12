---
title: "Ubuntu Server 14 Issue"
date: 2014-11-06
forum: General Help
---

### Post by Finriv on 2014-11-06
So, after having heard wonderful things, installing and booting ubuntu server 14 with the LAMP Server pack (fresh install) and running user@User-Server:~$ sudo apt-get install apache2 the following errors occur (similar to this thread; [http://ubuntuforums.org/showthread.php?t=891414&highlight=failing+to+resolve+ubuntu+server+archive](http://ubuntuforums.org/showthread.php?t=891414&highlight=failing+to+resolve+ubuntu+server+archive))

```

Do you want to continue? [Y/n] y
Err http://gb.archive.ubuntu.com/ trusty/main libapr1 amd64 1.5.0-1
  Could not resolve 'gb.archive.ubuntu.com'

```

etc etc etc, see above thread. Simmilar problem.

When I try to ping a server, such as security.ubuntu.com I get the following

```

ping: unkown host security.ubuntu.com

```

Which implies to me two things. One I have screwed up somewhere in setting up the internet connections which I think is the most likely cause. Second is that (being new to ubuntu with little experience with command line and similar in general) I am simply a derp.

---

### Post by TheFu on 2014-11-06
Not sure what a derp is. 
[http://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking](http://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking) - will help determine what the network issue is and we can work to solve it after it is known.

---

### Post by QIII on 2014-11-06
The kindest definition of a derp (var: durp) is a slack-jawed, unimaginative and non-intelligent mouth-breather who, when asked a question that requires a bit of thought, can muster only "Uh ... derp?"

:)

A variation of the theme may go --

Biff:  Bill, why did you stack box A on top of box B when you know box B goes on top?

Bill, smacking self on forehead:  Derp!

---

### Post by SeijiSensei on 2014-11-06
Looks like a DNS resolution problem to me.  Can you ping machines by IP address but not by name?  For instance, does "ping 74.125.226.16" work, but "ping www.google.com" does not?

If you set up the network interface manually in /etc/network/interfaces, add a "dns-nameservers" directive with the IP addresses of the servers you wish to use.  Here's the example from the Ubuntu [Network Configuration document]("https://help.ubuntu.com/14.04/serverguide/network-configuration.html"):
```

iface eth0 inet static
    address 192.168.3.3
    netmask 255.255.255.0
    gateway 192.168.3.1
    dns-search example.com
    dns-nameservers 192.168.3.45 192.168.8.10

```
The "dns-search" directive adds "example.com" when trying to resolve unqualified names like plain "www".

---

### Post by Finriv on 2014-11-09
So after fiddling, I cannot ping machines with the IP adress, looking into it the Netowrk was disabled. After enabling it the same problem still arises with being unable to resolve host names

---

### Post by TheFu on 2014-11-09
Did you read the article and follow the troubleshooting instructions?  Any output to post here so we can help?

---

