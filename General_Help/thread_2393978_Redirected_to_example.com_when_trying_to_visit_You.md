---
title: "Redirected to example.com when trying to visit Youtube"
date: 2018-06-10
forum: General Help
---

### Post by chunefung on 2018-06-10
I cannot visit Youtube and some other websites like the google account setting. I notice that when I type 

```

ping www.youtube.com

Output:
PING www.youtube.com (127.0.0.2) 56(84) bytes of data.
64 bytes from example.com (127.0.0.2): icmp_seq=1 ttl=64 time=0.043ms
64 bytes from example.com (127.0.0.2): icmp_seq=2 ttl=64 time=0.035ms

```

It looks like it is redirected to example.com. How can I fix this?

---

### Post by QIII on 2018-06-10
Moved to General Help.  Not a network issue.

---

### Post by wyliecoyoteuk on 2018-06-11
check the contents of your /etc/hosts file.
127.0.0.2 is a loopback address

---

### Post by chunefung on 2018-06-11
> **wyliecoyoteuk said:**
> check the contents of your /etc/hosts file.
127.0.0.2 is a loopback address

There is no file named hosts in /etc. Should I create one? And what should I put into the file?

My another computer also does not have the hosts file, but I can visit Youtube on it without any problem.

---

### Post by wyliecoyoteuk on 2018-06-11
Sounds like some program that you have installed has set up a redirection in DNS.
Example.com is probably from an example configuration file.
What software have you installed lately?
Can you post the contents of /etc/resolv.conf ?

---

### Post by chunefung on 2018-06-11
> **wyliecoyoteuk said:**
> Sounds like some program that you have installed has set up a redirection in DNS.
Example.com is probably from an example configuration file.
What software have you installed lately?
Can you post the contents of /etc/resolv.conf ?

I am not sure which software may be the cause. I could visit Youtube on that laptop some months ago, but one day it failed. I could not fix it and then just left it unfixed because I didn't really need to visit Youtube. But now I notice that I also cannot visit the google account setting (can visit google though). 

resolv.conf
```

# This file is managed by man:systemd-resolved(8). Do not edit.
#
# This is a dynamic resolv.conf file for connecting local clients to the
# internal DNS stub resolver of systemd-resolved. This file lists all
# configured search domains.
#
# Run "systemd-resolve --status" to see details about the uplink DNS servers
# currently in use.
#
# Third party programs must not access this file directly, but only through the
# symlink at /etc/resolv.conf. To manage man:resolv.conf(5) in a different way,
# replace this symlink by a static file or a different symlink.
#
# See man:systemd-resolved.service(8) for details about the supported modes of
# operation for /etc/resolv.conf.


nameserver 127.0.0.53
search local



```

---

### Post by yancek on 2018-06-11
The nameserver from your last post shows a localhost entry when it probably should be your router IP.  Not sure what you are using but you can find the router IP with:  route -n

---

### Post by Habitual on 2018-06-11
Can't "fix" yours, but...
ping uses /etc/hosts by default, so try
```
host youtube.com 

```and compare IPs. 
127.x.x..x is wrong in so many ways.

Is this related to a VPN?

I use in /etc/resolve.conf
```
domain localdomain
nameserver 1.1.1.1
nameserver 1.0.0.1

```

after editing resolv.conf, no reboot or restart needed.
after edit,
ping yahoo.com
again and you may get what I got - 216.58.216.14

Note: This IP of 216.58.216.14 
did NOT open youtube.com in my browser.

but google.com

---

### Post by chunefung on 2018-06-11
No it is not my router IP.

---

### Post by chunefung on 2018-06-11
> **Habitual said:**
> Can't "fix" yours, but...
ping uses /etc/hosts by default, so try
```
host youtube.com 

```and compare IPs. 
127.x.x..x is wrong in so many ways.

Is this related to a VPN?

I use in /etc/resolve.conf
```
domain localdomain
nameserver 1.1.1.1
nameserver 1.0.0.1

```

after editing resolv.conf, no reboot or restart needed.
after edit,
ping yahoo.com
again and you may get what I got - 216.58.216.14

Note: This IP of 216.58.216.14 
did NOT open youtube.com in my browser.

but google.com

```

host youtube.com

Output:
youtube.com has address 216.58.197.110

```

If I type

```

host www.youtube.com

Output:
www.youtube.com has address 127.0.0.2
www.youtube.com is an alias for youtube-ui.l.google.com.

```

After editing resolv.conf

```

ping yahoo.com

Output:
PING yahoo.com (98.138.219.231) 56(84) bytes of data.

```

By the way, the resolv.conf is exactly the same on my another computer which has no problem of visiting Youtube.

---

### Post by mc4man on 2018-06-12
> **chunefung said:**
> 

By the way, the resolv.conf is exactly the same on my another computer which has no problem of visiting Youtube.
That is the default for 18.04, see same here. So your (previous) issue was originally caused elsewhere

---

