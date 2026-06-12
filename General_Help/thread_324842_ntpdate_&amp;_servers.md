---
title: "ntpdate &amp; servers?"
date: 2006-12-24
forum: General Help
---

### Post by AlliumPorrum on 2006-12-24
Hi!

I'm running ntpdate in cron to be sure that the system clock is always on time. But now I noticed that ntpdate won't work, it just always says: "no servers can be used, exiting". How can I change the server(s) that ntpdate tries to use by default?

---

### Post by fragos on 2006-12-24
There's no need to set up a cron job.  Right click the date in the upper applet bar and select "Adjust Date & Time."  Click "Keep clock synchronized with Internet servers:" and the the "Select Servers" button.  There's a long list of ntp servers, with country info, to select from and you may want more than one for backup purposes.  If you like you can manually add them as well.  A complete GUI interface which will actually set the cron job for you.  You may want to delete your cron entry before going GUI.

---

### Post by dcstar on 2006-12-24
> **AlliumPorrum said:**
> Hi!

I'm running ntpdate in cron to be sure that the system clock is always on time. But now I noticed that ntpdate won't work, it just always says: "no servers can be used, exiting". How can I change the server(s) that ntpdate tries to use by default?
```
sudo gedit /etc/default/ntpdate
```

---

### Post by AlliumPorrum on 2006-12-25
Thanks dcstar! 

Now how do I tell the ntpdate to start using this new, updated configuration file?? I mean, I still get the same error message, so I think that I should somehow "refresh" ntpdate so that it reads these new settings?

---

### Post by AlliumPorrum on 2006-12-26
I changed the NTP server to be like this: 

 NTPSERVERS="europe.pool.ntp.org"

I rebooted the server, but still when I run ntpdate, I just get an error message:

 26 Dec 11:41:49 ntpdate[4829]: no servers can be used, exiting

Any hints what's wrong now??

---

### Post by fragos on 2006-12-26
Have you tried one of the servers Ubuntu comes pre-configured for?  I would think they are most lickley to be available to all users on the Internet.  If they do work, that will help you narrow the problem down to the server you choose to use.  If not then you more likely have a problem in your machine.

---

### Post by AlliumPorrum on 2007-01-07
I just noticed that automatic time synchronatization still does not work. What ever server I set to the /etc/default/ntpdate- file, I always get the same error: "no servers can be used, exiting". 

What's wrong with this ntp sync?? How can I make it work?

---

### Post by fragos on 2007-01-07
I used Gnome to configutre NTP and mine works.  Here's a copy of my working /etx/default/ntpdate

# servers to check.   (Separate multiple servers with spaces.)
NTPSERVERS="0.debian.pool.ntp.org 1.debian.pool.ntp.org 2.debian.pool.ntp.org 3.debian.pool.ntp.org"
#
# additional options for ntpdate
#NTPOPTIONS="-v"
NTPOPTIONS="-u"
NTPSERVERS="ntp.ubuntu.com"

---

### Post by AlliumPorrum on 2007-01-11
Thank you Fragos, but that did not help. I copied your config file as my /etc/default/ntpdate, but still same thing, when I run ntpdate I always get "no servers can be used, exiting". Any ideas??

---

### Post by Moldz on 2007-01-11
I read through the man page for ntpdate.  It *does not* use the /etc/default/ntpdate file.  The program expects the server on the command line.  For example:

```
sudo ntpdate ntp.ubuntu.com
```

Just add the server along with the command to your cron entry.

---

### Post by AlliumPorrum on 2007-01-11
That's it, thank you very much Moldz! I just wonder why everybody is talking about this /etc/default/ntpdate- file then....? There must be some use for it also?

---

### Post by fragos on 2007-01-11
True enough for ntpdate but not necessarily for ntpd.  If the GUI is used to set the parameters system time, ntpd is run.  I verfied this in dmesg.  That's not to say that what you've suggested wouldn't work as well.  I actually don't know since I use the GUI for time.

---

### Post by Ptero-4 on 2007-02-13
Which time server do I need to use (I live in Panamá, Latino America)?

---

### Post by dcstar on 2007-02-13
> **Ptero-4 said:**
> Which time server do I need to use (I live in Panamá, Latino America)?

You use whatever time server is physically closest to your Internet connection.

---

### Post by Ptero-4 on 2007-02-14
I ask b/c I know nothing about timezones and no one of the time servers is in panamá (they`re in USA and EU, no one in central america).

---

### Post by fragos on 2007-02-14
My recommendation is to choose one in the same time zone or barring that in the US.  I'm not even sure being in the same time zone matters.

---

### Post by TuxCrafter on 2007-05-02
```
sudo ntpdate -vd europe.pool.ntp.org
sudo ntpdate -vd ntp.ubuntu.com
```

```
 2 May 16:52:06 ntpdate[5008]: no server suitable for synchronization found
```

why does this not work?

---

### Post by fragos on 2007-05-02
The GUI Gnome configuration works correctly.  I never had a need to configure NTP from the command line.

---

### Post by TuxCrafter on 2007-05-02
I want to have full control and use the commandline

---

### Post by moterpent on 2007-05-08
Not sure if everyone (i.e. TuxCrafter) got the answers they were looking for but I thought I would chime in and explain what has worked for me over the years.

For those with casual time needs that prefer to simply use "ntpdate", it's a good idea to specify multiple time servers on the command line.  It is recommended that you include a minimum of three.  This will provide you with more accurate results as well as improved reliability should a server not be available.

In my case, I've been using the handy cluster of servers detailed at [http://www.pool.ntp.org](http://www.pool.ntp.org).  Their "pools" seem to be divided up various ways.  For example you can grab servers by continent (i.e. north-america, europe, oceana, asia).  There are some country pools as well.  See their site for more info.

The clever thing about pool.ntp.org is that their DNS entries randomly change (once an hour I believe).  This means that you will regularly get different time servers.

Anyway, here's an example command line that might work well for someone living in Canada:

```
ntpdate 0.ca.pool.ntp.org 1.ca.pool.ntp.org 2.ca.pool.ntp.org
```

I hope this helps.  Good luck!

---

### Post by TuxCrafter on 2007-05-08
> **moterpent said:**
> Not sure if everyone (i.e. TuxCrafter) got the answers they were looking for but I thought I would chime in and explain what has worked for me over the years.

I hope this helps.  Good luck!

Thank you for your help, i tried you command but it output this information:

sudo ntpdate 0.ca.pool.ntp.org 1.ca.pool.ntp.org 2.ca.pool.ntp.org

8 May 14:36:48 ntpdate[5788]: no server suitable for synchronization found

---

### Post by moterpent on 2007-05-08
> **TuxCrafter said:**
> Thank you for your help, i tried you command but it output this information:

sudo ntpdate 0.ca.pool.ntp.org 1.ca.pool.ntp.org 2.ca.pool.ntp.org

8 May 14:36:48 ntpdate[5788]: no server suitable for synchronization found

Are you able to ping or do a nslookup on any of the servers above?  Maybe try some of the U.S. servers?  For example:

```
nslookup 0.us.pool.ntp.org
ping 0.us.pool.ntp.org
```

Also, can you paste the output of the following command:

```
sudo ntpdate -dv 0.us.pool.ntp.org
```

---

### Post by TuxCrafter on 2007-05-08
> **moterpent said:**
> Are you able to ping or do a nslookup on any of the servers above?  Maybe try some of the U.S. servers?  For example:

```
nslookup 0.us.pool.ntp.org
ping 0.us.pool.ntp.org
```

Also, can you paste the output of the following command:

```
g
```
```

 nslookup 0.us.pool.ntp.org
Server:         192.168.1.254
Address:        192.168.1.254#53

Non-authoritative answer:
Name:   0.us.pool.ntp.org
Address: 209.151.236.226
Name:   0.us.pool.ntp.org
Address: 72.42.150.178
Name:   0.us.pool.ntp.org
Address: 208.100.0.36
Name:   0.us.pool.ntp.org
Address: 64.81.253.134
Name:   0.us.pool.ntp.org
Address: 64.34.193.47
Name:   0.us.pool.ntp.org
Address: 216.154.195.60
Name:   0.us.pool.ntp.org
Address: 66.152.175.36
Name:   0.us.pool.ntp.org
Address: 72.21.46.202
Name:   0.us.pool.ntp.org
Address: 209.234.76.2
Name:   0.us.pool.ntp.org
Address: 66.90.101.207
Name:   0.us.pool.ntp.org
Address: 64.183.187.9
Name:   0.us.pool.ntp.org
Address: 71.211.243.223

```
```

ping 0.us.pool.ntp.org
PING 0.us.pool.ntp.org (72.242.157.125) 56(84) bytes of data.
64 bytes from mail.onehop.com (72.242.157.125): icmp_seq=1 ttl=44 time=132 ms
64 bytes from onehop.onehop.com (72.242.157.125): icmp_seq=2 ttl=44 time=131 ms
64 bytes from onehop.onehop.com (72.242.157.125): icmp_seq=3 ttl=44 time=133 ms
64 bytes from onehop.onehop.com (72.242.157.125): icmp_seq=4 ttl=44 time=133 ms
64 bytes from mail.onehop.com (72.242.157.125): icmp_seq=5 ttl=44 time=135 ms
64 bytes from onehop.onehop.com (72.242.157.125): icmp_seq=6 ttl=44 time=132 ms
64 bytes from mail.onehop.com (72.242.157.125): icmp_seq=7 ttl=44 time=132 ms
64 bytes from onehop.onehop.com (72.242.157.125): icmp_seq=8 ttl=44 time=132 ms

--- 0.us.pool.ntp.org ping statistics ---
8 packets transmitted, 8 received, 0% packet loss, time 7008ms
rtt min/avg/max/mdev = 131.697/133.054/135.438/1.077 ms

```
```

ntpdate 4.2.2p4@1.1585-o Wed Mar  7 20:43:31 UTC 2007 (1)
transmit(192.83.249.31)
receive(192.83.249.31)
transmit(192.83.249.31)
transmit(207.210.77.32)
receive(207.210.77.32)
transmit(207.210.77.32)
receive(192.83.249.31)
transmit(192.83.249.31)
transmit(206.111.81.7)
receive(207.210.77.32)
transmit(207.210.77.32)
receive(192.83.249.31)
transmit(192.83.249.31)
receive(207.210.77.32)
transmit(207.210.77.32)
transmit(216.75.55.11)
receive(206.111.81.7)
transmit(206.111.81.7)
receive(207.210.77.32)
transmit(207.210.77.32)
receive(192.83.249.31)
transmit(192.83.249.31)
receive(216.75.55.11)
transmit(216.75.55.11)
transmit(138.23.180.126)
receive(206.111.81.7)
transmit(206.111.81.7)
receive(216.75.55.11)
transmit(216.75.55.11)
receive(138.23.180.126)
transmit(138.23.180.126)
transmit(72.3.133.147)
receive(206.111.81.7)
transmit(206.111.81.7)
receive(216.75.55.11)
transmit(216.75.55.11)
receive(72.3.133.147)
transmit(72.3.133.147)
receive(138.23.180.126)
transmit(138.23.180.126)
transmit(63.127.106.213)
receive(206.111.81.7)
transmit(206.111.81.7)
receive(72.3.133.147)
transmit(72.3.133.147)
receive(216.75.55.11)
transmit(216.75.55.11)
receive(138.23.180.126)
transmit(138.23.180.126)
receive(63.127.106.213)
transmit(63.127.106.213)
receive(72.3.133.147)
transmit(72.3.133.147)
transmit(72.242.157.125)
receive(63.127.106.213)
transmit(63.127.106.213)
receive(63.127.106.213)
receive: pkt.org and peer.xmt differ
receive(138.23.180.126)
transmit(138.23.180.126)
receive(72.3.133.147)
transmit(72.3.133.147)
receive(72.242.157.125)
transmit(72.242.157.125)
transmit(65.254.53.19)
receive(63.127.106.213)
transmit(63.127.106.213)
receive(63.127.106.213)
transmit(63.127.106.213)
receive(65.254.53.19)
transmit(65.254.53.19)
receive(72.242.157.125)
transmit(72.242.157.125)
transmit(75.13.24.211)
receive(65.254.53.19)
transmit(65.254.53.19)
receive(72.242.157.125)
transmit(72.242.157.125)
receive(65.254.53.19)
transmit(65.254.53.19)
receive(75.13.24.211)
transmit(75.13.24.211)
transmit(64.182.117.175)
receive(65.254.53.19)
transmit(65.254.53.19)
receive(72.242.157.125)
transmit(72.242.157.125)
receive(64.182.117.175)
transmit(64.182.117.175)
transmit(71.211.243.223)
receive(75.13.24.211)
transmit(75.13.24.211)
receive(64.182.117.175)
transmit(64.182.117.175)
receive(71.211.243.223)
transmit(71.211.243.223)
receive(75.13.24.211)
transmit(75.13.24.211)
receive(64.182.117.175)
transmit(64.182.117.175)
receive(75.13.24.211)
transmit(75.13.24.211)
receive(71.211.243.223)
transmit(71.211.243.223)
receive(64.182.117.175)
transmit(64.182.117.175)
receive(71.211.243.223)
transmit(71.211.243.223)
receive(71.211.243.223)
transmit(71.211.243.223)
server 192.83.249.31, port 123
stratum 2, precision -10, leap 00, trust 000
refid [192.83.249.31], delay 0.21387, dispersion 0.00000
transmitted 4, in filter 4
reference time:    c9eb37ba.439e4382  Tue, May  8 2007 19:54:02.264
originate timestamp: c9eb37ba.7d9c7623  Tue, May  8 2007 19:54:02.490
transmit timestamp:  c9eb37bb.41a6b50b  Tue, May  8 2007 19:54:03.256
filter delay:  0.21413  0.21387  0.21407  0.21407 
         0.00000  0.00000  0.00000  0.00000 
filter offset: -0.86043 -0.86044 -0.86043 -0.86049
         0.000000 0.000000 0.000000 0.000000
delay 0.21387, dispersion 0.00000
offset -0.860446

server 207.210.77.32, port 123
stratum 3, precision -20, leap 00, trust 000
refid [207.210.77.32], delay 0.15210, dispersion 0.00017
transmitted 4, in filter 4
reference time:    c9eb30d0.289b6d44  Tue, May  8 2007 19:24:32.158
originate timestamp: c9eb37ba.780bd802  Tue, May  8 2007 19:54:02.468
transmit timestamp:  c9eb37bb.4635f809  Tue, May  8 2007 19:54:03.274
filter delay:  0.15340  0.15297  0.15350  0.15210 
         0.00000  0.00000  0.00000  0.00000 
filter offset: -0.86846 -0.86834 -0.86884 -0.86861
         0.000000 0.000000 0.000000 0.000000
delay 0.15210, dispersion 0.00017
offset -0.868619

server 206.111.81.7, port 123
stratum 2, precision -16, leap 00, trust 000
refid [206.111.81.7], delay 0.23132, dispersion 0.00143
transmitted 4, in filter 4
reference time:    c9eb3420.d3777d0f  Tue, May  8 2007 19:38:40.826
originate timestamp: c9eb37ba.f6deca25  Tue, May  8 2007 19:54:02.964
transmit timestamp:  c9eb37bb.b8345cfe  Tue, May  8 2007 19:54:03.719
filter delay:  0.23157  0.23434  0.23921  0.23132 
         0.00000  0.00000  0.00000  0.00000 
filter offset: -0.85682 -0.85865 -0.85259 -0.85807
         0.000000 0.000000 0.000000 0.000000
delay 0.23132, dispersion 0.00143
offset -0.858076

server 216.75.55.11, port 123
stratum 2, precision -20, leap 00, trust 000
refid [216.75.55.11], delay 0.19545, dispersion 0.00079
transmitted 4, in filter 4
reference time:    c9eb36ac.8c58c93f  Tue, May  8 2007 19:49:32.548
originate timestamp: c9eb37bb.0380a36c  Tue, May  8 2007 19:54:03.013
transmit timestamp:  c9eb37bb.cf192ea5  Tue, May  8 2007 19:54:03.808
filter delay:  0.19545  0.20360  0.19559  0.19801 
         0.00000  0.00000  0.00000  0.00000 
filter offset: -0.88036 -0.87671 -0.88020 -0.88150
         0.000000 0.000000 0.000000 0.000000
delay 0.19545, dispersion 0.00079
offset -0.880362

server 138.23.180.126, port 123
stratum 2, precision -20, leap 00, trust 000
refid [138.23.180.126], delay 0.19760, dispersion 0.00229
transmitted 4, in filter 4
reference time:    c9eb3743.367967ca  Tue, May  8 2007 19:52:03.212
originate timestamp: c9eb37bb.3e3ae254  Tue, May  8 2007 19:54:03.243
transmit timestamp:  c9eb37bc.0424e592  Tue, May  8 2007 19:54:04.016
filter delay:  0.19881  0.19760  0.20538  0.21704 
         0.00000  0.00000  0.00000  0.00000 
filter offset: -0.87769 -0.87815 -0.87451 -0.86883
         0.000000 0.000000 0.000000 0.000000
delay 0.19760, dispersion 0.00229
offset -0.878153

server 72.3.133.147, port 123
stratum 2, precision -17, leap 00, trust 000
refid [72.3.133.147], delay 0.15036, dispersion 0.00159
transmitted 4, in filter 4
reference time:    c9eb366c.10a0e410  Tue, May  8 2007 19:48:28.064
originate timestamp: c9eb37bb.4836c9c0  Tue, May  8 2007 19:54:03.282
transmit timestamp:  c9eb37bc.111611ba  Tue, May  8 2007 19:54:04.066
filter delay:  0.15131  0.15036  0.15073  0.17490 
         0.00000  0.00000  0.00000  0.00000 
filter offset: -0.87165 -0.87165 -0.87174 -0.85930
         0.000000 0.000000 0.000000 0.000000
delay 0.15036, dispersion 0.00159
offset -0.871653

server 63.127.106.213, port 123
stratum 3, precision -20, leap 00, trust 000
refid [63.127.106.213], delay 0.13663, dispersion 0.00455
transmitted 4, in filter 4
reference time:    c9eb31db.d8b4d056  Tue, May  8 2007 19:28:59.846
originate timestamp: c9eb37bb.7e1a2e7f  Tue, May  8 2007 19:54:03.492
transmit timestamp:  c9eb37bc.4deb313b  Tue, May  8 2007 19:54:04.304
filter delay:  0.15367  0.19771  0.13866  0.13663 
         0.00000  0.00000  0.00000  0.00000 
filter offset: -0.87418 -0.84738 -0.86801 -0.86731
         0.000000 0.000000 0.000000 0.000000
delay 0.13663, dispersion 0.00455
offset -0.867310

server 72.242.157.125, port 123
stratum 2, precision -19, leap 00, trust 000
refid [72.242.157.125], delay 0.19519, dispersion 0.00546
transmitted 4, in filter 4
reference time:    c9eb35ff.fd655e28  Tue, May  8 2007 19:46:39.989
originate timestamp: c9eb37bb.ef2b66b6  Tue, May  8 2007 19:54:03.934
transmit timestamp:  c9eb37bc.9dd883ba  Tue, May  8 2007 19:54:04.616
filter delay:  0.19519  0.20747  0.19954  0.23575 
         0.00000  0.00000  0.00000  0.00000 
filter offset: -0.80783 -0.80173 -0.80506 -0.78741
         0.000000 0.000000 0.000000 0.000000
delay 0.19519, dispersion 0.00546
offset -0.807836

server 65.254.53.19, port 123
stratum 3, precision -20, leap 00, trust 000
refid [65.254.53.19], delay 0.15161, dispersion 0.00035
transmitted 4, in filter 4
reference time:    c9eb3713.db0d2ab5  Tue, May  8 2007 19:51:15.855
originate timestamp: c9eb37bb.dce4861c  Tue, May  8 2007 19:54:03.862
transmit timestamp:  c9eb37bc.abd9988d  Tue, May  8 2007 19:54:04.671
filter delay:  0.15315  0.15161  0.15219  0.15392 
         0.00000  0.00000  0.00000  0.00000 
filter offset: -0.87098 -0.87147 -0.87166 -0.87261
         0.000000 0.000000 0.000000 0.000000
delay 0.15161, dispersion 0.00035
offset -0.871478

server 75.13.24.211, port 123
stratum 1, precision -18, leap 00, trust 000
refid [WWVB], delay 0.20969, dispersion 0.00388
transmitted 4, in filter 4
reference time:    c9eb37a4.31f1c518  Tue, May  8 2007 19:53:40.195
originate timestamp: c9eb37bc.553bff1a  Tue, May  8 2007 19:54:04.332
transmit timestamp:  c9eb37bd.1bf023e9  Tue, May  8 2007 19:54:05.109
filter delay:  0.21196  0.25929  0.22362  0.20969 
         0.00000  0.00000  0.00000  0.00000 
filter offset: -0.86665 -0.87906 -0.87521 -0.86824
         0.000000 0.000000 0.000000 0.000000
delay 0.20969, dispersion 0.00388
offset -0.868244

server 64.182.117.175, port 123
stratum 2, precision -20, leap 00, trust 000
refid [64.182.117.175], delay 0.19337, dispersion 0.00027
transmitted 4, in filter 4
reference time:    c9eb33e5.329f7b5a  Tue, May  8 2007 19:37:41.197
originate timestamp: c9eb37bc.6a086bdf  Tue, May  8 2007 19:54:04.414
transmit timestamp:  c9eb37bd.32ae2973  Tue, May  8 2007 19:54:05.197
filter delay:  0.19606  0.19417  0.19337  0.19356 
         0.00000  0.00000  0.00000  0.00000 
filter offset: -0.86691 -0.86732 -0.86732 -0.86777
         0.000000 0.000000 0.000000 0.000000
delay 0.19337, dispersion 0.00027
offset -0.867321

server 71.211.243.223, port 123
stratum 2, precision -19, leap 00, trust 000
refid [71.211.243.223], delay 0.23026, dispersion 0.00464
transmitted 4, in filter 4
reference time:    c9eb306a.242a37ff  Tue, May  8 2007 19:22:50.141
originate timestamp: c9eb37bc.cd4b37ff  Tue, May  8 2007 19:54:04.801
transmit timestamp:  c9eb37bd.92428d43  Tue, May  8 2007 19:54:05.571
filter delay:  0.23109  0.23026  0.29391  0.23042 
         0.00000  0.00000  0.00000  0.00000 
filter offset: -0.87136 -0.87283 -0.84017 -0.87242
         0.000000 0.000000 0.000000 0.000000
delay 0.23026, dispersion 0.00464
offset -0.872831

 8 May 19:54:04 ntpdate[4621]: step time server 75.13.24.211 offset -0.868244 sec

```

```
sudo ntpdate 0.us.pool.ntp.org
 8 May 19:55:19 ntpdate[4624]: adjust time server 75.13.24.211 offset -0.016443 sec

```

Don't now why but it works now!

---

### Post by philipMac on 2007-05-08
I am still getting "no server suitable for synchronization found" for all servers I try...

---

### Post by moterpent on 2007-05-09
Nice TuxCrafter!  I'm glad it's working for you!

philipMac,

Sorry to hear your having trouble.  Can you post the output from the commands above (i.e. nslookup, ping, and ntpdate -dv)?  The same thing that TuxCrafter listed.  It will help identify where or what the problem might be.

---

### Post by TuxCrafter on 2007-05-09
> **moterpent said:**
> Nice TuxCrafter!  I'm glad it's working for you!

philipMac,

Sorry to hear your having trouble.  Can you post the output from the commands above (i.e. nslookup, ping, and ntpdate -dv)?  The same thing that TuxCrafter listed.  It will help identify where or what the problem might be.

I have done some testing and it appears ntpdate can be blocks by firewalls! I tested it on different locations, at home it works at work it doesn't. Hope this helps

---

### Post by moterpent on 2007-05-10
> **TuxCrafter said:**
> I have done some testing and it appears ntpdate can be blocks by firewalls! I tested it on different locations, at home it works at work it doesn't. Hope this helps

It's possible.  If your firewall/router etc. block outbound connections to port 123 you could most certainly have a problem.

---

### Post by dannyboy79 on 2007-05-23
you guys, if you would read  the very top of the file, /etc/default/ntpdate, it states: 
# The settings in this file are used by the program ntpdate-debian, but not
# by the upstream program ntpdate.
So therefor in order for you to get this to work, you need to run ntpdate-debian. At least that's what I do in a cron job. Just like the command that's located in /etc/network/if-up.d/ntpdate, when you open that file, it actually is using the /usr/sbin/ntpdate-debian command and not the ntpdate command. ANyway, whaty I have done is changed the setting in the /etc/default/ntpdate file from: "yes" to: "no" for the NTPDATE_USE_NTP_CONF setting, and then I just made sure I put the ntpserver I wanted it to call right there in that file, and then I added a hourly cron job to run ntpdate-debian as root. That does it.

---

### Post by ways on 2008-04-03
sudo ntpdate -u <servername>

worked for me

---

