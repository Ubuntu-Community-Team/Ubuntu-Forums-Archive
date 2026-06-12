---
title: "Strange Clock Problems"
date: 2008-02-21
forum: General Help
---

### Post by TimMcE on 2008-02-21
I'm running Ubuntu 7.10, and I've run into a rather odd little problem with the clock.  Basically, the longer my computer is left on, the more disjointed the time becomes.  If I just use it for a day and shut down at night, it's usually fine (though not always), but I tend to leave my machine running for a week or more at a time.

Usually the date is ok, unless it's around midnight.  Sometimes the clock goes forward, sometimes it goes back.  I tried setting it to sync with internet servers with no joy.

One of the things I found rather odd is that if I try to type the proper time in, it will take the hours and seconds happily enough, but it keeps setting the minutes back to what they were.

For example, if it shows the time as 19:**15**:32, and I try to set it to 21:40:00, it will take it for a second or two, and then the time will change to 21:**15**:00.  Even using the little arrow keys beside the minute value doesn't work.  The only way I can get it to take is to type in the proper minute number, then hit Close quickly before it changes the number back.  After that I'm usually ok for a couple days before it starts acting up again.

Lastly, I've rebooted into Windows on occasion when this has been happening, and the Windows time will show the correct time, but when I boot back into Ubuntu, it's still wrong.

Anyone have any ideas as to what might be going on?

---

### Post by Sam Lars on 2008-02-22
I've noticed some issues between Windows/Linux times, too.
It seems that it's resetting alright on boot, but then drifting?  What do you get from

```
cat /var/log/syslog | grep ntp
```

Another possibility is the CMOS battery?  I doubt it, since you say it's not always in the same direction, but it's possible.

---

### Post by TimMcE on 2008-02-22
Tried
```
cat /var/log/syslog | grep ntp
```
And it doesn't display anything.  I just drops to the next line.  I tried sudo but that didn't help either.  I don't think it's a battery issue, since the computer keeps time just fine when it's switched off, the problem only arises after it's been left on for a while.

---

### Post by Sam Lars on 2008-02-22
Are you sure that you have internet time set up?

---

### Post by TimMcE on 2008-02-23
Oh right. :P  Forgot to switch that back on after the last time I had to adjust the clock.  Now I get
```

Feb 22 21:48:30 tim-desktop ntpd[31139]: ntpd 4.2.4p0@1.1472-o Thu Oct  4 20:58:45 UTC 2007 (1)
Feb 22 21:48:30 tim-desktop ntpd[31144]: precision = 1.000 usec
Feb 22 21:48:30 tim-desktop ntpd[31144]: Listening on interface #0 wildcard, 0.0.0.0#123 Disabled
Feb 22 21:48:30 tim-desktop ntpd[31144]: Listening on interface #1 wildcard, ::#123 Disabled
Feb 22 21:48:30 tim-desktop ntpd[31144]: Listening on interface #2 vmnet8, fe80::250:56ff:fec0:8#123 Enabled
Feb 22 21:48:30 tim-desktop ntpd[31144]: Listening on interface #3 lo, ::1#123 Enabled
Feb 22 21:48:30 tim-desktop ntpd[31144]: Listening on interface #4 vmnet1, fe80::250:56ff:fec0:1#123 Enabled
Feb 22 21:48:30 tim-desktop ntpd[31144]: Listening on interface #5 eth0, fe80::217:31ff:fe00:15c5#123 Enabled
Feb 22 21:48:30 tim-desktop ntpd[31144]: Listening on interface #6 lo, 127.0.0.1#123 Enabled
Feb 22 21:48:30 tim-desktop ntpd[31144]: Listening on interface #7 eth0, 10.1.0.24#123 Enabled
Feb 22 21:48:30 tim-desktop ntpd[31144]: Listening on interface #8 vmnet1, 172.16.186.1#123 Enabled
Feb 22 21:48:30 tim-desktop ntpd[31144]: Listening on interface #9 vmnet8, 172.16.223.1#123 Enabled
Feb 22 21:48:30 tim-desktop ntpd[31144]: kernel time sync status 0040
Feb 22 21:48:30 tim-desktop ntpd[31144]: frequency initialized -66.430 PPM from /var/lib/ntp/ntp.drift

```

---

### Post by Sam Lars on 2008-02-23
That looks much better.  After  a while, it should say that it's synchronized to some server.  If it's fixed, you can change the title to solved.

---

### Post by jpkotta on 2008-02-23
I doubt it's fixed.   I've been having the same problem lately, and it's because ntpd isn't synching for some reason.  This is what it should look like:
```

[jpkotta@gauss ~](0)$ zgrep ntp  /var/log/syslog*.gz | tail
/var/log/syslog.6.gz:Feb 16 12:03:42 gauss ntpd[5801]: synchronized to 128.105.39.11, stratum 2
/var/log/syslog.6.gz:Feb 16 12:23:02 gauss ntpd[5801]: synchronized to 91.189.94.4, stratum 2
/var/log/syslog.6.gz:Feb 16 13:19:08 gauss ntpd[5801]: synchronized to 128.105.39.11, stratum 2
/var/log/syslog.6.gz:Feb 16 14:09:23 gauss ntpd[5801]: synchronized to 132.246.168.148, stratum 2
/var/log/syslog.6.gz:Feb 16 14:35:08 gauss ntpd[5801]: synchronized to 128.105.39.11, stratum 2
/var/log/syslog.6.gz:Feb 16 14:56:37 gauss ntpd[5801]: synchronized to 132.246.168.148, stratum 2
/var/log/syslog.6.gz:Feb 16 17:51:40 gauss ntpd[5801]: synchronized to 91.189.94.4, stratum 2
/var/log/syslog.6.gz:Feb 16 18:17:16 gauss ntpd[5801]: synchronized to 132.246.168.148, stratum 2
/var/log/syslog.6.gz:Feb 16 20:51:04 gauss ntpd[5801]: synchronized to 91.189.94.4, stratum 2
/var/log/syslog.6.gz:Feb 16 21:24:34 gauss ntpd[5801]: synchronized to 132.246.168.148, stratum 2

```

ntpdate still works, but ntpd won't.  And my clock really sucks, apparently, because it loses about an hour a day.  This is only on one of my machines, which happens to be the only 64-bit one.

---

### Post by Sam Lars on 2008-02-23
So jpkotta, do you have ntpd set up correctly to look at the right servers?  Also, do you suspect your battery?

---

### Post by VictorR on 2008-02-23
As far as I know if your selected "Keep synchronized with Internet servers" in Time and Date settings it synchronizes itself only on startup. That is why it keeps the correct time, when you switch your box off every night.
It needs some extra tricks to make it really synchronized, like using cron for launching ntpdate from time to time. By default it should run ntpd daemon to calculate time drift and correct time when the drift is too big. But it does not work often for some reasons. In my daemon.log file I see it cannot synchronize with NTP servers. There was discussion about this earlier, but the whole topic is still unclear for me.

---

### Post by Sam Lars on 2008-02-23
You may be right, but I seem to have it staying synchronized always...
What servers are you looking for?

---

### Post by VictorR on 2008-02-23
Here is the last ntpd output i can see in the log:
```

Feb 24 10:17:45 ubuntu-desktop ntpd[28205]: ntpd 4.2.4p0@1.1472-o Thu Oct  4 20:58:45 UTC 2007 (1)
Feb 24 10:17:45 ubuntu-desktop ntpd[28206]: precision = 1.000 usec
Feb 24 10:17:45 ubuntu-desktop ntpd[28206]: Listening on interface #0 wildcard, 0.0.0.0#123 Disabled
Feb 24 10:17:45 ubuntu-desktop ntpd[28206]: Listening on interface #1 wildcard, ::#123 Disabled
Feb 24 10:17:45 ubuntu-desktop ntpd[28206]: Listening on interface #2 lo, ::1#123 Enabled
Feb 24 10:17:45 ubuntu-desktop ntpd[28206]: Listening on interface #3 eth0, fe80::20c:76ff:fece:eeb5#123 Enabled
Feb 24 10:17:45 ubuntu-desktop ntpd[28206]: Listening on interface #4 lo, 127.0.0.1#123 Enabled
Feb 24 10:17:45 ubuntu-desktop ntpd[28206]: Listening on interface #5 eth0, 192.168.0.1#123 Enabled
Feb 24 10:17:45 ubuntu-desktop ntpd[28206]: Listening on interface #6 ppp0, 118.90.106.223#123 Enabled
Feb 24 10:17:45 ubuntu-desktop ntpd[28206]: kernel time sync status 0040
Feb 24 10:17:45 ubuntu-desktop ntpd[28206]: frequency initialized 0.410 PPM from /var/lib/ntp/ntp.drift
Feb 24 10:17:45 ubuntu-desktop ntpd[28206]: configure: keyword "nz.pool.ntp.org" unknown, line ignored
Feb 24 10:17:47 ubuntu-desktop ntpd_initres[28249]: host name not found: ntp.per.nml.csiro.au
Feb 24 10:17:47 ubuntu-desktop ntpd_initres[28249]: couldn't resolve `ntp.per.nml.csiro.au', giving up on it
Feb 24 10:17:48 ubuntu-desktop ntpd_initres[28249]: host name not found: ntp.nml.csiro.au
Feb 24 10:17:48 ubuntu-desktop ntpd_initres[28249]: couldn't resolve `ntp.nml.csiro.au', giving up on it
Feb 24 10:17:48 ubuntu-desktop ntpd_initres[28249]: host name not found: ntp.mel.nml.csiro.au
Feb 24 10:17:48 ubuntu-desktop ntpd_initres[28249]: couldn't resolve `ntp.mel.nml.csiro.au', giving up on it
Feb 24 10:17:48 ubuntu-desktop ntpd_initres[28249]: host name not found: time.esec.com.au
Feb 24 10:17:48 ubuntu-desktop ntpd_initres[28249]: couldn't resolve `time.esec.com.au', giving up on it
Feb 24 10:22:03 ubuntu-desktop ntpd[28206]: synchronized to 202.135.38.18, stratum 2
Feb 24 10:22:03 ubuntu-desktop ntpd[28206]: kernel time sync status change 0001

```
I have removed those particular unreacheable servers from the list of servers now and left only
ntp.ubuntu.com
nz.pool.ntp.org
au.pool.ntp.org

Don't know which one is 202.135.38.18, but I tried to ping nz.pool.ntp.org and succeed.

I also read some more info I googled today about the topic, and found one explanation, that ntpd prevents sudden time changes, which can cause, for example, odd timestamps. Maybe this can lead to time drift, even if everything seems to be allright.

---

### Post by Sam Lars on 2008-02-23
The pools are just lists of servers.  You will connect randomly to one of them.
It says that it's synchronized.  That doesn't keep the clock from drifting?
Yes, if your clock is more that like a month or two off, it won't change the time, and it tries to calculate your drift so that it can compensate.

---

### Post by TimMcE on 2008-02-23
> **Sam Lars said:**
> That looks much better.  After  a while, it should say that it's synchronized to some server.  If it's fixed, you can change the title to solved.
Well, I tried cat /var/log/syslog | grep ntp again this morning, and it's back to not displaying anything, despite the clock still saying it's synchronizing with internet servers.  I'm going to try fiddling around with using different servers, just in case the ones I've picked are the ones causing problems.

---

### Post by VictorR on 2008-02-23
I switched my box off last night because of bad weather and possible power cut-off, so I cannot say for sure my clock drifted too much. I will leave it for tomorrow and check with another computer, how much it went off.

---

### Post by Sam Lars on 2008-02-23
TimMcE, it may not do any more as far as the log goes for a while.  If it stays synchronized, then it should be working fine.  If you set your server to pool.ntp.org, it will have a much better selection from which to find a good server.

---

### Post by jpkotta on 2008-02-23
> **Sam Lars said:**
> So jpkotta, do you have ntpd set up correctly to look at the right servers?  Also, do you suspect your battery?

I had it looking at the default (ntp.ubuntu.com) and some servers close to me (ntp1.cs.wisc.edu and one in Canada).  I've since purged ntpd and reinstalled.  Here is my /etc/ntp.conf:
```

# /etc/ntp.conf, configuration for ntpd

driftfile /var/lib/ntp/ntp.drift

# Enable this if you want statistics to be logged.
#statsdir /var/log/ntpstats/

statistics loopstats peerstats clockstats
filegen loopstats file loopstats type day enable
filegen peerstats file peerstats type day enable
filegen clockstats file clockstats type day enable


# You do need to talk to an NTP server or two (or three).
server ntp.ubuntu.com 

# By default, exchange time with everybody, but don't allow configuration.
# See /usr/share/doc/ntp-doc/html/accopt.html for details.
restrict -4 default kod notrap nomodify nopeer noquery
restrict -6 default kod notrap nomodify nopeer noquery

# Local users may interrogate the ntp server more closely.
restrict 127.0.0.1
restrict ::1

# Clients from this (example!) subnet have unlimited access,
# but only if cryptographically authenticated
#restrict 192.168.123.0  mask  255.255.255.0 notrust

# If you want to provide time to your local subnet, change the next line.
# (Again, the address is an example only.)
#broadcast 192.168.123.255

# If you want to listen to time broadcasts on your local subnet,
# de-comment the next lines. Please do this only if you trust everybody
# on the network!
#disable auth
#broadcastclient
server ntp1.cs.wisc.edu
server 0.us.pool.ntp.org
server 1.us.pool.ntp.org
server 2.us.pool.ntp.org
server 3.us.pool.ntp.org
server pool.ntp.org

```

I think the servers work, because ntpdate works.  I suppose it could be my battery, but a) my motherboard is less than a year old and b) shouldn't ntpd take care of that anyway?  Shouldn't it resynch every few hours, thus compensating for a bad battery?  I mean, the clock is still running, just not very well, and ntpd isn't synching at all.

BTW: here are the logs:
```
23 Feb 13:52:14 ntpd[19161]: logging to file /var/log/ntp.log
23 Feb 13:52:14 ntpd[19161]: precision = 1.000 usec
23 Feb 13:52:14 ntpd[19161]: Listening on interface #0 wildcard, 0.0.0.0#123 Disabled
23 Feb 13:52:14 ntpd[19161]: Listening on interface #1 lo, 127.0.0.1#123 Enabled
23 Feb 13:52:14 ntpd[19161]: Listening on interface #2 eth0, 192.168.0.5#123 Enabled
23 Feb 13:52:14 ntpd[19161]: Listening on interface #3 vmnet1, 172.16.155.1#123 Enabled
23 Feb 13:52:14 ntpd[19161]: Listening on interface #4 vmnet8, 172.16.198.1#123 Enabled
23 Feb 13:52:14 ntpd[19161]: kernel time sync status 0040
23 Feb 13:52:14 ntpd[19161]: frequency initialized 0.000 PPM from /var/lib/ntp/ntp.drift
23 Feb 13:52:14 ntpd[19161]: getaddrinfo: "::1" invalid host address, ignored
23 Feb 19:17:22 ntpd[19161]: ntpd exiting on signal 15
23 Feb 19:17:28 ntpd[1033]: logging to file /var/log/ntp.log
23 Feb 19:17:28 ntpd[1033]: precision = 1.000 usec
23 Feb 19:17:28 ntpd[1033]: Listening on interface #0 wildcard, 0.0.0.0#123 Disabled
23 Feb 19:17:28 ntpd[1033]: Listening on interface #1 lo, 127.0.0.1#123 Enabled
23 Feb 19:17:28 ntpd[1033]: Listening on interface #2 eth0, 192.168.0.5#123 Enabled
23 Feb 19:17:28 ntpd[1033]: Listening on interface #3 vmnet1, 172.16.155.1#123 Enabled
23 Feb 19:17:28 ntpd[1033]: Listening on interface #4 vmnet8, 172.16.198.1#123 Enabled
23 Feb 19:17:28 ntpd[1033]: kernel time sync status 0040
23 Feb 19:17:28 ntpd[1033]: frequency initialized 0.000 PPM from /var/lib/ntp/ntp.drift
23 Feb 19:17:28 ntpd[1033]: getaddrinfo: "::1" invalid host address, ignored

```

---

### Post by Sam Lars on 2008-02-23
Can you verify that the daemon is started but not logging anything or setting the time?

---

### Post by TimMcE on 2008-02-23
I set my servers to pool.ntp.org a few hours ago, and came back to find that I'd jumped forward a couple hours.  On a whim, I changed my time zone from North America/Vancouver to North America/Los Angeles, and within 10 minutes my clock had adjusted itself back to it's normal time.

---

### Post by Sam Lars on 2008-02-23
So it sounds like it's working as expected for you?

---

### Post by jpkotta on 2008-02-24
> **Sam Lars said:**
> Can you verify that the daemon is started but not logging anything or setting the time?

```
[jpkotta@gauss ~](1)$ ps -ef | grep ntpd
ntp       1033     1  0 Feb23 ?        00:00:00 /usr/sbin/ntpd -p /var/run/ntpd.pid -u 111:121 -g -l /var/log/ntp.log

```

---

### Post by mallow on 2008-02-24
Hi. I`ve got the same issue with my laptop. It was OK earlier, but since a couple of days my clock gets unsynchronized when I leave it running for several hours. I doubt it is a battery because it`s still on cable.

---

### Post by Sam Lars on 2008-02-24
TimMcE, can you do the same?
jpkotta, does your log show that it's synchronized to anything yet?
Mallow, is it logging that it's synchronizing?
The battery isn't the laptop battery, it's a different one.

---

### Post by VictorR on 2008-02-24
As promised I checked my computer with another one, which was just booted and synchronized. I have not noticed any difference more than a second, so I think ntpd does its job well.

I guess the problem before was because of too many NTP servers were selected, most of them were unreachable and the daemon gave up before it reached the end of this list. Now only three pool servers are left.

---

### Post by TimMcE on 2008-02-24
> **Sam Lars said:**
> TimMcE, can you do the same?
jpkotta, does your log show that it's synchronized to anything yet?
Mallow, is it logging that it's synchronizing?
The battery isn't the laptop battery, it's a different one.
According to this:
```
tim@tim-desktop:~$ ps -ef | grep ntpd
ntp       6640     1  0 09:45 ?        00:00:00 /usr/sbin/ntpd -p /var/run/ntpd.pid -u 109:121 -g
tim      13108 12928  0 12:13 pts/0    00:00:00 grep ntpd

```
The daemon seems to be up and running, and I've had no problems since I switched time zones/servers.  I'm hesitant to say it's completely fixed at this point, due to the intermittent nature of the problem (sometimes it takes 3-4 days for the clock to go screwy), but for now it seems to be working well.

---

### Post by jpkotta on 2008-02-24
It finally synched.  But it seems like it's still having problems.

```
24 Feb 10:59:04 ntpd[18671]: synchronized to 91.189.94.4, stratum 2
24 Feb 11:08:33 ntpd[18671]: time reset +568.485574 s
24 Feb 11:08:33 ntpd[18671]: kernel time sync status change 0001
24 Feb 13:51:58 ntpd[18671]: sendto(128.105.39.11) (fd=18): Invalid argument
24 Feb 13:52:07 ntpd[18671]: sendto(75.144.70.35) (fd=18): Invalid argument
24 Feb 13:58:37 ntpd[18671]: sendto(75.144.70.35) (fd=18): Invalid argument
24 Feb 13:58:43 ntpd[18671]: sendto(67.207.133.173) (fd=18): Invalid argument
24 Feb 13:58:45 ntpd[18671]: sendto(207.182.243.123) (fd=18): Invalid argument
24 Feb 13:58:47 ntpd[18671]: sendto(66.36.239.127) (fd=18): Invalid argument
24 Feb 13:58:47 ntpd[18671]: sendto(69.60.124.59) (fd=18): Invalid argument
24 Feb 13:59:14 ntpd[18671]: sendto(91.189.94.4) (fd=18): Invalid argument
24 Feb 13:59:31 ntpd[18671]: sendto(128.105.39.11) (fd=18): Invalid argument
24 Feb 13:59:42 ntpd[18671]: sendto(75.144.70.35) (fd=18): Invalid argument
24 Feb 13:59:46 ntpd[18671]: sendto(67.207.133.173) (fd=18): Invalid argument
24 Feb 13:59:51 ntpd[18671]: sendto(207.182.243.123) (fd=18): Invalid argument
24 Feb 13:59:52 ntpd[18671]: sendto(66.36.239.127) (fd=18): Invalid argument
24 Feb 13:59:53 ntpd[18671]: sendto(69.60.124.59) (fd=18): Invalid argument
24 Feb 14:00:17 ntpd[18671]: sendto(91.189.94.4) (fd=18): Invalid argument
24 Feb 14:00:37 ntpd[18671]: sendto(128.105.39.11) (fd=18): Invalid argument
24 Feb 14:00:46 ntpd[18671]: sendto(75.144.70.35) (fd=18): Invalid argument
24 Feb 14:00:49 ntpd[18671]: sendto(67.207.133.173) (fd=18): Invalid argument

```

---

### Post by Sam Lars on 2008-02-24
TimMcE and VictorR, good to hear, let us know how things go.
jpkotta, I found a thread about that [here]("http://ubuntuforums.org/showthread.php?t=122510").  The last post mentions IP changing, would that apply to you?

---

### Post by jpkotta on 2008-02-24
> **Sam Lars said:**
> 
jpkotta, I found a thread about that [here]("http://ubuntuforums.org/showthread.php?t=122510").  The last post mentions IP changing, would that apply to you?

Nope.  I have a DHCP server on my LAN that assigns my IP based on my MAC address, so it's always the same.  However, I looked at my modem/router, and it said it had reset or reconnected around the time of those sendto() errors.  So maybe that's it, but it doesn't seem right, since my computer shouldn't care what the gateway's address is on the internet.  

It seems like the file descriptor (18) is still open.

```
[jpkotta@gauss ntpd](1)$ sudo lsof -u ntp | grep -v mem
COMMAND   PID USER   FD   TYPE             DEVICE    SIZE    NODE NAME
ntpd    18671  ntp  cwd    DIR                9,1    4096       2 /
ntpd    18671  ntp  rtd    DIR                9,1    4096       2 /
ntpd    18671  ntp  txt    REG                9,1  469848  300695 /usr/sbin/ntpd
ntpd    18671  ntp    0u   CHR                1,3           10102 /dev/null
ntpd    18671  ntp    1u   CHR                1,3           10102 /dev/null
ntpd    18671  ntp    2u   CHR                1,3           10102 /dev/null
ntpd    18671  ntp    3u  unix 0xffff8100a90862c0         1315385 socket
ntpd    18671  ntp    5w   REG                9,1    3970 1368381 /var/log/ntp.log
ntpd    18671  ntp   16u  IPv4            1315397             UDP *:ntp 
ntpd    18671  ntp   17u  IPv4            1315399             UDP localhost:ntp 
ntpd    18671  ntp   18u  IPv4            1315400             UDP gauss.local.lan:ntp 
ntpd    18671  ntp   19u  IPv4            1315401             UDP gauss.local:ntp 
ntpd    18671  ntp   20u  IPv4            1315402             UDP gauss.local:ntp 

```

---

### Post by VictorR on 2008-02-29
Just to confirm: my computer has been running for more than 7 days now and after check with another "just synchronized" laptop I don't see any time drift. /var/log/daemon.log shows, that ntpd synchronizes from time to time to different IPs, say, 5 times per day.

The computer is connected to the Internet directly via USB modem, 24/7, I think there is no manual changes in the ntp-related config files, all done through System->Administration->Time and Date menu. All NTP servers from the default list are un-checked, three others were added and active:
ntp.ubuntu.com
nz.pool.ntp.org  (I am In NZ).
au.pool.ntp.org

---

### Post by jpkotta on 2008-03-21
Follow up:  I think it's fixed now.  I rebooted and now the clock is not drifting.  I think my motherboard is a POS (it has ESD trouble too).

---

