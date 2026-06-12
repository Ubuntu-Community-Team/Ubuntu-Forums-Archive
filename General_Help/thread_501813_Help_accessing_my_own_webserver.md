---
title: "Help accessing my own webserver"
date: 2007-07-15
forum: General Help
---

### Post by william_hunter on 2007-07-15
OK, I have hunted all aorund, and I am stumped. I have set up a phpbb2 forum on my Edgy machine, and it is currently running, and accessible from within my LAN via the internal IP address because I set the domain name to localhost for the time being so I can get to it. Problem is this:

I do not know how to make my forum accessible to people outside the firewall AND myself (inside, of course). When I change the domain name to the DYNDNS name i have reserved, everyone can access it nicely, and everything works, but I cannot because the forum redirects me to the outside DNS given name, which, because of the hardware router, I cannot load. Is the solution to set the server on a DMZ?

As you can tell, I am grasping a little here. I have banged my head against this for a week now, and cannot figure out how to make my problem go away.

---

### Post by Mr. C. on 2007-07-15
Setup your domain name to use your WAN IP address.

Setup either /etc/hosts to map your domain name to your LAN address, or use an internal DNS server for your LAN addresses.

MrC

---

### Post by william_hunter on 2007-07-15
Oh, you mean the actual IP , not the name I chose. Interesting. Never would have thought of that.

I don't find an /etc/hosts dir. Should this be part of the default Ubuntu set up?

---

### Post by Mr. C. on 2007-07-15
/etc/hosts is a file.

The file contains entires like:

```
127.0.0.1   localhost
```

Add your own enty, such as:
```
192.168.0.1  host.mydomain.com
```

using your server's LAN IP and the external hostname you want to be the same internally and externally.

MrC

---

### Post by william_hunter on 2007-07-15
Ah, so I can make one if it does not exist and put it in the etc dir? I searched for it and dont find one.

---

### Post by Mr. C. on 2007-07-15
The /etc/hosts file is and has been on every Unix/Linux system I have seen.  Perhaps you don't have one, but that would be a surprise to me.

Via command line, what is the output of :

```
cat /etc/hosts
```

MrC

---

### Post by william_hunter on 2007-07-15
> 
127.0.0.1 localhost
127.0.1.1 whunter-desktop

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts


I guess I was missing it somehow. So, all I need to do is add my internal IP and the host name and I should be able to access it from inside the network and then I can change the domain name to let people outside get on, right?

---

### Post by Mr. C. on 2007-07-15
Correct - from that machine, you'll be able to access it by name.  To access by name from other machines on your LAN, you need to update their hosts files.

Setup the same domain name at your dyndns service.

The hosts file is referenced before DNS queries - that's why this works.  Your host will access the hosts file, while outsiders use DNS.

MrC

---

### Post by william_hunter on 2007-07-15
So, I have to just go find that file on my mac and I am good to go. Now i get it. Thanks.

---

