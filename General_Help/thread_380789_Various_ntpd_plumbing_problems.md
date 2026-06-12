---
title: "Various ntpd plumbing problems"
date: 2007-03-10
forum: General Help
---

### Post by Phrawm48 on 2007-03-10
For Dapper / 6.06, Gnome.

My system clock is pretty inaccurate (fast), most likely because my *ntpd* daemon's plumbing isn't working properly.

My */etc/ntp.conf* file contains the following server entries (for which I used ping to get the IP addresses):

> 
server 127.127.1.0
server clock.via.net     (reachable per ping, ip address equals 209.81.9.7)
server nist1.symmetricom.com     (reachable per ping, ip address equals 69.25.96.13)
server ntp.ubuntu.com    (reachable per ping as fiordland.ubuntu.com, ip address equals 82.211.81.145)


Okay, now if I watch */var/log/syslog*, I get recurring messages like these (non-contiguously):

> 
sendto(209.81.9.7): Bad file descriptor
sendto(69.25.96.13): Bad file descriptor
sendto(82.211.81.145): Bad file descriptor


So it seems that my ntdp daemon is getting the server names from *ntp.conf* and resolving their ip addresses(?), but that something's not exactly right with the config.

*/var/log/syslog*also contains interations of these messages (contiguously):

> 
03/10/2007 12:34:55 AM	localhost	ntpd[12437]	couldn't unlink /var/log/ntpstats/loopstats: Permission denied
03/10/2007 12:34:55 AM	localhost	ntpd[12437]	couldn't unlink /var/log/ntpstats/peerstats: Permission denied
03/10/2007 12:35:59 AM	localhost	ntpd[12437]	can't open /var/log/ntpstats/loopstats.20070310: Permission denied
03/10/2007 12:35:59 AM	localhost	ntpd[12437]	can't open /var/log/ntpstats/peerstats.20070310: Permission denied


If I then go to the aforementioned */var/log/ntpstats*, I find the following files (excerpted):

> 
...
-rw-r--r-- 1 ntp ntp 33176 2007-03-09 14:38 loopstats.20070309
-rw-r--r-- 2 ntp ntp 24869 2007-03-10 00:14 loopstats.20070310
-rw-r--r-- 2 ntp ntp 24869 2007-03-10 00:14 loopstats
...
-rw-r--r-- 1 ntp ntp 45132 2007-03-09 14:38 peerstats.20070309
-rw-r--r-- 2 ntp ntp 32545 2007-03-10 00:14 peerstats.20070310
-rw-r--r-- 2 ntp ntp 32545 2007-03-10 00:14 peerstats
...


Lastly, if I look in *loopstats* and *peerstats*, I find lots of this sort of thing:

> ... begin *loopstats* excerpt
54169 3914.627 0.000000000 388.408997 0.000003304 0.000109 6
54169 3980.661 0.000000000 388.408997 0.000002861 0.000095 6
54169 4043.687 0.000000000 388.408997 0.000002478 0.000082 6

... begin *peerstats* excerpt
54169 3721.546 127.127.1.0 9014 0.000000000 0.000000000 0.000015000 0.000003815
54169 3785.568 127.127.1.0 9014 0.000000000 0.000000000 0.000960000 0.000003815
54169 3848.597 127.127.1.0 9014 0.000000000 0.000000000 0.000945000 0.000003815


So, all the files seem to be there but I can't find any instances of *ntpd* adjusting my system time.  Can anyone please help me unsnarl this?

Cheers & thanks,
Ric

---

### Post by jpiers on 2008-06-10
Is it the first time you experience that error?

---

### Post by Phrawm48 on 2008-06-10
"Is it the first time you experience that error?"

Thanks for asking but I "fixed" the problem several months ago by upgrading to 7.04.  It works the way I assumed it ought...

Cheers & thanks 'gain,
Ric
SFO

---

