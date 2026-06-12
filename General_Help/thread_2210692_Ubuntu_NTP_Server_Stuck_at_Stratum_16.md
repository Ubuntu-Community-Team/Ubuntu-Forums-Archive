---
title: "Ubuntu NTP Server Stuck at Stratum 16?"
date: 2014-03-12
forum: General Help
---

### Post by zach14 on 2014-03-12
We use an Ubuntu installation as the time server for our local network. All was working fine until a few days ago, when a glitch in our content filter was blocking the ability for our time server to sync with external sources. We fixed the problem with that and the time is syncing correctly, but even after 48 hours, the box still considers itself as a stratum 16, which means our other machines will not sync with it.

Here's the output of ntpq -c lpeer:


    
```
netadmin@Timesync:~$ ntpq -c lpeer
     remote           refid      st t when poll reach   delay   offset  jitter
==============================================================================
 Timesync        .BCST.          16 u    -   64    0    0.000    0.000   0.001
+fairy.mattnordh 164.244.221.197  2 u  633 1024  377   17.227   -0.086   0.104
+twist.pathennes 128.4.1.1        2 u  667 1024  377   28.542    1.313   0.987
-vimo.dorui.net  209.51.161.238   2 u 1693 1024  376   29.278    1.434   0.266
*ntp2.eecs.wsu.e .GPS.            1 u  734 1024  377   94.854    0.511   2.746
-louie.udel.edu  128.175.60.175   2 u  659 1024  377   28.961   -2.346   2.619
-otc2.psu.edu    128.118.2.33     2 u  670 1024  377   50.277    3.215   0.231
-dns3.cit.cornel 192.5.41.209     2 u  654 1024  377   39.155   -2.245   0.599
```

Is there anything else we are missing?

---

### Post by Lars Noodén on 2014-03-12
How far out of sync is it?  Have you tried stopping ntpd temporarily and then starting it with -g to force a synchronization?

```

sudo service ntp stop
sudo /usr/sbin/ntpd -g
sudo service ntpd restart

```

---

### Post by zach14 on 2014-03-12
The clock itself appears perfect - is there a way to determine how out of sync it is?

We've rebooted the server a few times in an attempt to get it working again. Here's the output from your suggested commands:

```

netadmin@Timesync:~$ sudo /etc/init.d/ntp stop
[sudo] password for netadmin:
 * Stopping NTP server ntpd                                              [ OK ]
netadmin@Timesync:~$ sudo /usr/sbin/ntpd -g
netadmin@Timesync:~$ sudo /etc/init.d/ntp start
 * Starting NTP server ntpd                                              [ OK ]
netadmin@Timesync:~$ ntpq -c lpeer
     remote           refid      st t when poll reach   delay   offset  jitter
==============================================================================
 Timesync        .BCST.          16 u    -   64    0    0.000    0.000   0.001
 15.185.186.215  198.153.152.52   2 u   10   64    1   79.662   -5.008   0.001
 linode.appus.or 66.220.9.122     2 u   15   64    1   88.320    2.439   0.001
 equinox.nj.us.s 64.246.132.14    2 u   14   64    1   29.893   -0.504   0.001
 lttleman.deekay 164.244.221.197  2 u   13   64    1   17.815   -2.725   0.001
 louie.udel.edu  128.175.60.175   2 u   12   64    1   28.869   -2.315   0.001
*otc2.psu.edu    128.118.2.33     2 u    1   64    1   50.308    2.671   0.071
 dns3.cit.cornel 128.118.25.12    2 u   10   64    1   39.829   -3.300   0.001


```

---

### Post by Lars Noodén on 2014-03-12
Have you changed /etc/ntp.conf at all from the defaults?

---

### Post by zach14 on 2014-03-12
Mark this thread as solved.  Apparently broadcast stratums are supposed to be 16, which is normal.  Our server was actually working - the machine I was trying to sync was the problem (chalk up another problem to crappy Windoze NTP/W32Time).

Thank you for the help Lars!

---

### Post by Jay_E on 2014-06-05
There are many pages at ntp.org including how to read ntpq output.

The broadcast entry has liitle to do with your question:"How far off am I?"
The answer is in the "offset column - measured in milliseconds.

The entry with an "*" in the FIRST column is the server that is most reliable from your location - and has been picked.
In your first example
*ntp2.eecs.wsu.e .GPS.            1 u  734 1024  377   94.854    0.511   2.746

the offset of 0.511 mean that your clock is off by 0.000511 seconds.
The bcast entry means that you are broadcasting on your local net
Your clock is set at stratum 16 so it won't think it ius better than the others.
   (Hey - 0 delay and 0 jitter from myself. Easy to delude oneself.)

in the 2nd example,
*otc2.psu.edu    128.118.2.33     2 u    1   64    1   50.308    2.671   0.071
You are off by 2.761 milliseconds. Not bad at all. you must have a well-balanced internet connection.

Have fun,
Jay

---

