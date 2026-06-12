---
title: "Can ping, can't ssh"
date: 2007-11-12
forum: General Help
---

### Post by abrichr on 2007-11-12
I have gutsy installed on my laptop and on my desktop.  My desktop is connected directly to the internet, my laptop is behind a d-link router.  I  have the latest version of openssh-server from the repos installed on the desktop.

From my laptop, I can ping the desktop, but I can't connect via ssh:

```
$ ssh ##.##.###.##
ssh: connect to host ##.##.###.## port 22: Connection timed out

```

Typing "ssh localhost" on the desktop works fine.  What's going on here?

---

### Post by abrichr on 2007-11-15
Bump.  Still not working.  The desktop is 32-bit, the laptop 64.

---

### Post by jinx099 on 2007-11-15
describe your network more.  are the 2 computers on the same network?

---

### Post by mellowd on 2007-11-15
Yeah we need a bit more information on the actualy network itself. Which device is connected to which and how?

---

### Post by abrichr on 2007-11-15
My desktop is at home, and is connected directly to the internet.  This means it is not on any internal network.  I bring my laptop to work, where it sits behind a d-link router.  Incidentally, it did not work when my laptop was at home behind my linksys router, either (I have more than one internet connection at home).

---

### Post by jinx099 on 2007-11-15
Make sure your sshd service is running.

Also, post the results of nmap to your home IP.

---

### Post by abrichr on 2007-11-16
I tried stopping and starting sshd.  I tried sshfs.  Still no go.

```
$ nmap 69.17.173.98

Starting Nmap 4.20 ( http://insecure.org ) at 2007-11-16 20:12 EST
Note: Host seems down. If it is really up, but blocking our ping probes, try -P0
Nmap finished: 1 IP address (0 hosts up) scanned in 4.005 seconds

$ nmap 69.17.173.98 -P0

Starting Nmap 4.20 ( http://insecure.org ) at 2007-11-16 20:13 EST
Stats: 0:00:24 elapsed; 0 hosts completed (1 up), 1 undergoing Connect() Scan
Connect() Scan Timing: About 6.78% done; ETC: 20:18 (0:05:30 remaining)
```

...doesn't seem to be going anywhere from there.  I really don't understand why this is happening; any more ideas?

---

### Post by abrichr on 2007-11-16
It finished:

```
nmap 69.17.173.98 -P0

Starting Nmap 4.20 ( http://insecure.org ) at 2007-11-16 20:13 EST
Stats: 0:00:24 elapsed; 0 hosts completed (1 up), 1 undergoing Connect() Scan
Connect() Scan Timing: About 6.78% done; ETC: 20:18 (0:05:30 remaining)
Stats: 0:03:38 elapsed; 0 hosts completed (1 up), 1 undergoing Connect() Scan
Connect() Scan Timing: About 63.94% done; ETC: 20:18 (0:02:02 remaining)
All 1697 scanned ports on xtreme-14-98.dyn.aci.on.ca (69.17.173.98) are filtered

Nmap finished: 1 IP address (1 host up) scanned in 351.093 seconds

```

So it DOES see it.

---

### Post by tinycamp on 2007-11-16
it seems that u cant connect to anything on that ip... all ports seem to be filtered...

are u using iptables???

```

sudo iptables -L

```

---

### Post by Zack McCool on 2007-11-16
> **abrichr said:**
> 
```
$ ssh ##.##.###.##
ssh: connect to host ##.##.###.## port 22: Connection timed out

```

Typing "ssh localhost" on the desktop works fine.  What's going on here?

Firewall?  You say that this desktop is directly connected to the internet.  No router?  Are IPTables configured?  Does your internet provider allow traffic on port 22?

---

### Post by abrichr on 2007-11-16
From [http://insecure.org/nmap/man/man-port-scanning-basics.html:](http://insecure.org/nmap/man/man-port-scanning-basics.html:)

> filtered

    Nmap cannot determine whether the port is open because packet filtering prevents its probes from reaching the port. The filtering could be from a dedicated firewall device, router rules, or host-based firewall software. These ports frustrate attackers because they provide so little information. Sometimes they respond with ICMP error messages such as type 3 code 13 (destination unreachable: communication administratively prohibited), but filters that simply drop probes without responding are far more common. This forces Nmap to retry several times just in case the probe was dropped due to network congestion rather than filtering. This slows down the scan dramatically.

...so there's a firewall running on my desktop?  i'll have to look into the iptables manpages...

---

### Post by tinycamp on 2007-11-16
maybe it's not in your system, it might be at your ISP network.

---

