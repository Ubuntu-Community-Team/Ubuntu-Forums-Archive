---
title: "CUPS 1.2.1 broke something"
date: 2006-07-08
forum: General Help
---

### Post by Ramaddan on 2006-07-08
Hi,

I don't know if anyone got this yet,
but as I upgraded to the latest CUPS in the upstream,
the CUPS server refused to wrok anymore,
and the sound server also stopped working,
and a few other little things also stopped working properly.

Did anyone get this?

Thanks.

---

### Post by Ramaddan on 2006-07-09
Hi,

Am I the only one who got this CUPS problem?

I downgraded to get rid of the problem.

Thanks.

---

### Post by patrickfromspain on 2006-07-09
I'm using 1.2.1 with no problems at all. I have to use it because of turboprint

---

### Post by linuxbz on 2006-07-09
Yep, after upgrade to cupsys 1.2.1 it won't start:

```
Setting up cupsys (1.2.1-0ubuntu1) ...
 * Starting Common Unix Printing System: cupsd                                                            cupsd: Child exited with status 1!
invoke-rc.d: initscript cupsys, action "start" failed.
dpkg: error processing cupsys (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 cupsys
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by dsyates on 2006-07-09
me too, samemessage

---

### Post by yjsoon on 2006-07-10
Same here. I checked the logs and it gave me the following errors:

```

E [10/Jul/2006:14:31:16 +0800] Unknown directive RunAsUser on line 6.
I [10/Jul/2006:14:31:16 +0800] Listening to :::631 (IPv6)
I [10/Jul/2006:14:31:16 +0800] Listening to 0.0.0.0:631 (IPv4)
E [10/Jul/2006:14:31:16 +0800] Bad netmask value 10.0.0.* on line 16.
E [10/Jul/2006:14:31:16 +0800] Unknown Location directive Allow on line 16.

```

Did something change in the cupsd.conf syntax?

---

### Post by ivoks on 2006-07-10
Yes. Something did change.

[https://launchpad.net/distros/ubuntu/+source/cupsys/+bug/52390](https://launchpad.net/distros/ubuntu/+source/cupsys/+bug/52390)

---

### Post by linuxbz on 2006-07-10
That worked. In /etc/cups/cupsd.conf I commented out RunAsUser and changed the netmask from 192.168.0.* to 192.168.0.0/24, restarted cupsys, and it works fine.

And it WAS a dist-upgrade from Breezy.

---

### Post by chescobar on 2006-07-10
The solution is very simple:

In the file /etc/cups/cupsd.conf we must change  all the lines that refer to network in the syntax:

192.168.1.* 

to:

192.168.1.0/24

where the network is 192.168.1.0 and netmask is 255.255.255.0

for the network 192.168.1.0 and netmask 255.255.0.0, the notation must be:

192.168.1.0/16

For printers that is shared in the network with ipp we must keep the line:

port 631

after of 
# Listen /var/run/cups/cups.sock

---

### Post by Ramaddan on 2006-07-11
Hi,

The issue was resolved for me.
The lastest CUPS 1.2.1-Ubuntu2 fixed the problem.

Thanks to those who replied.

---

