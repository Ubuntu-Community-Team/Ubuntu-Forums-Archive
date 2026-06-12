---
title: "Something overwrites resolv.conf"
date: 2006-10-27
forum: General Help
---

### Post by muxecoid on 2006-10-27
Some time after I connect to the Internet /etc/resolv.conf is being changed... Correct DNS is replaced with 
192.168.101.101 and 192.168.101.102 . What is the reason and what do I need to do to stop that?

---

### Post by lloyd_b on 2006-10-27
Are you using a static IP address, or one assigned by DHCP? (If unsure, could you post a copy of "/etc/network/interfaces"?).

The only thing I know of that will alter "resolv.conf" automatically is DHCP.  

Lloyd B.

---

### Post by handy on 2006-10-27
> **muxecoid said:**
> Some time after I connect to the Internet /etc/resolv.conf is being changed... Correct DNS is replaced with 
192.168.101.101 and 192.168.101.102 . What is the reason and what do I need to do to stop that?

Have a look at [***_this how-to_***]("http://ubuntuforums.org/showthread.php?t=282034"), it could be just what you are looking for?  I hope so anyway... :)

---

### Post by muxecoid on 2006-10-28
Failure. With prepend in DHCP conf my conenction script does not work.

I see
```
request domain-name-servers
```
in DHCP conf. Do I need it?

---

### Post by handy on 2006-10-28
Did you put your ISP's DNS IP addresses in like:-

**prepend domain-name-servers 208.67.222.222, 208.67.220.220;**

You can actually use that address if you choose, but you will have to tell your router to use them too?

Those DNS IP's are for [***_OpenDNS_***]("http://www.opendns.com/")

I leave the

**domain-name-servers**

In my **request** section of the **dhclient.conf**

---

### Post by muxecoid on 2006-10-28
It's what I did and the cableconnect script stoped working properly.

---

