---
title: "Patch broke networking?"
date: 2005-03-26
forum: General Help
---

### Post by infornography on 2005-03-26
Hi,

I just installed some security patches for Hoary. I didn't pay much attention to what the patches were (shame on me) but I assume they had something to do with networking, because when I rebooted my internet connection no longer worked.

I have a 265k ADSL connection through eth0. Is there a way to get it back up and running?

Normally I would just wait for a patch to fix the patch, but with no internet its going to be pretty hard to download it.

Sorry I cant provide more information. I guess it will teach me to always be aware of what I'm installing. Even when its official packages.

---

### Post by arctic on 2005-03-26
could you post a bit of information about your network? maybe it only needs simple reactivation or new dns-entries? are you using a router or only a adsl-modem?
please post the sudo result of *ifup eth0*,  *ifconfig* and *cat /etc/resolv.conf*.

---

### Post by alastair on 2005-03-26
[QUOTE=infornography]Hi,

I just installed some security patches for Hoary. I didn't pay much attention to what the patches were (shame on me) but I assume they had something to do with networking, because when I rebooted my internet connection no longer worked.

I have a 265k ADSL connection through eth0. Is there a way to get it back up and running?
[/QUOTE]

As requested in the last comment - more information if you can. It is probably quite a simple issue.

e.g.

You have a router accessed via eth0? So, the router is your default gateway. You know the router IP address?

Check :

ifconfig eth0
route -n

If you do :

sudo ifup eth0

Check the logs :

/var/log/syslog

and see what is printed (perhaps "tail -f /var/log/syslog" as you do the "ifup".

DHCP is also a possible cause (if you use DHCP).

If problem persists, output of the above command (before and after "ifup") - and look at the logs.

---

### Post by Brian McConnell on 2005-03-26
This may be the same problem a lot of Ubuntu users are experiencing. For me (apple G5, ethernet, no router) my network went down after applying some updates. It appears there is a typo in the dhclient.conf file. Try this:

**sudo gedit /etc/dhcp3/dhclient.conf**

go to line 21. there will be an entry saying: 

**netbios-name-servers, net-scope interface-mtu**

now simply add a comma between the last two entries so that you get:

**netbios-name-servers, net-scope, interface-mtu**

save your changes, exit and run:

**sudo ifup eth0**


that got me back online in a hot minute!

Thanks to **arctic** for sharing this info right here at the Ubuntu forums:
**[http://www.ubuntuforums.org/showthread.php?t=22263](http://www.ubuntuforums.org/showthread.php?t=22263)**

---

