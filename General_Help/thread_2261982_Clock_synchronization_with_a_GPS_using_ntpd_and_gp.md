---
title: "Clock synchronization with a GPS using ntpd and gpsd"
date: 2015-01-22
forum: General Help
---

### Post by alfredo7 on 2015-01-22
Hi everyone

We are trying to use a GPS as a time source for synchronizing various notebooks (each notebook has its own GPS). The GPS is connected through USB and we are using the gpsd deamon to send the time and date information to the ntpd deamon. When we applied ntpq &#8211;p command, we can see the clock source apparently is the GPS, but this happen only when there is an internet connection. 

Running ntpq -p with an internet connection

```
remote           refid      st t when poll reach   delay   offset  jitter
==============================================================================
*SHM(0)          .NMEA.           0 l    4   16   17    0.000   -1.187   0.678
 SHM(1)          .PPS.            0 l    -   16    0    0.000    0.000   0.000
 juniperberry.ca 192.93.2.20      2 u   78  128  377  154.856    0.442   2.138
```

Running ntpq -p without an internet connection

```
remote           refid      st t when poll reach   delay   offset  jitter
==============================================================================
 SHM(0)          .NMEA.           0 l    -   16    0    0.000    0.000   0.000
 SHM(1)          .PPS.            0 l    -   16    0    0.000    0.000   0.000
+juniperberry.ca 192.93.2.20      2 u   78  128  377  154.856    0.442   2.138
```


We don&#8217;t know why this is happening, is necessary maintain an internet connection to fulfill the synchronization?
Any help will be appreciated

---

### Post by HermanAB on 2015-01-22
No it is not necessary to have an internet connection, but configuring ntpd to work properly is a black art with little helpful information anywhere.

When we needed to synch time to a GPS, we eventually gave up and wrote a little program that read the GPS and used the date command to set the clocks instead of using gpsd and ntpd.  So, good luck with your quest...

---

### Post by SeijiSensei on 2015-01-22
Is 192.93.2.20 in the list of servers in ntp.conf?  What if you delete that entry so it doesn't try to connect to a remote time server.

---

### Post by tgalati4 on 2015-01-22
Understand that ntpd uses network latency to determine local clock offsets from the master ntp pool clock.  Using gps as a source doesn't provide this latency.  What you could do is write a cronjob to syncronize one computer every hour with gps, designate that computer as the local "master" and point all of the other computers to it to syncronize their clocks.

What are your timing requirements?  What is the Use Case for these notebooks?  Why can't each notebook just use an hourly gps update?  You could calculate hourly drift for each notebook and add those values to a drift file as a backup for when gps sync fails.

It's not easy to incorporate gps into the standard ntp protocol.  ntp was written way before gps was even thought of.

A certified chronometer is +6 to -4 seconds per day.  That's +250 ms to -167 ms of drift per hour allowable.  With a drift file and a decent internet connection, *ntpd* can get to within a few ms (3 to 8 ms) of the master.  So if you connect the notebooks for several hours to the internet and develop a decent drift file, then you could probably go for several days before exceeding chronometer performance.

Here's a time study I did in 2008:

[ATTACH=CONFIG]259425[/ATTACH]

The chart shows how this particular computer went from 9 ms of error to less than 3 ms in 20,000 seconds (5.5 hours).  The longer you stay connected, the better the drift file can compensate for temperature and systematic variations.  It would be interesting to add gps data to the mix to see how it drifts from the *ntp* daemon.

---

### Post by alfredo7 on 2015-01-26
Hello SeijiSensei

The server 192.93.2.20 is not in the list of servers in ntp.conf.However we added the lines     
         IPV4: restrict default ignore
         IPv6: restrict -6 default ignore

to the ntp.conf file to block all connections, and also we have the gps address as an exception, leaving it as the only ntp connection alternative.

We would like to know if you know any way to test if the pc clock is actually synchroniced with the gps.

Thanks for your help

---

