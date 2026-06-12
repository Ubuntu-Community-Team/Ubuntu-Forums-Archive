---
title: "Can't synchronize with time servers"
date: 2007-07-24
forum: General Help
---

### Post by jordon on 2007-07-24
On Feisty, I can't synchronize my clock with any of the time servers. I can select servers, but the "Synchronize Now" button is grayed out, and after a while the clock drifts. I have ntp installed. Does anyone know how I can fix the problem?

---

### Post by jordon on 2007-07-26
Bump

---

### Post by wieman01 on 2007-07-26
Perhaps start the sync process as admin... GKSU that is. Just an idea.

---

### Post by jordon on 2007-07-26
I have to be root to change the time in the first place, but I could give it a try. How do I do it?

---

### Post by jordon on 2007-08-05
I'm still having this problem, but after some digging I've found that I can synchronize the clock to a server SERVERNAME by entering:

```
ntpdate -u SERVERNAME
```

[Apparently]("http://ubuntuforums.org/showpost.php?p=2264445&postcount=6") it's simple enough to set up a cron job that does that, but I'd like to know why the clock won't synchronize automatically in the first place.

---

### Post by Bachstelze on 2007-08-05
Is NTPD running ?

```
ps aux | grep ntpd
```

---

### Post by jordon on 2007-08-05
I think so; here's the output.

```
ntp       5600  0.0  0.0   4268  1240 ?        Ss   13:15   0:00 /usr/sbin/ntpd -p /var/run/ntpd.pid -u 110:119 -g
jordon   14929  0.0  0.0   2880   748 pts/0    R+   17:15   0:00 grep ntpd

```

---

### Post by Bachstelze on 2007-08-05
And what do you have in /etc/ntp.conf ?

---

### Post by jordon on 2007-08-05
> **HymnToLife said:**
> And what do you have in /etc/ntp.conf ?

```
# /etc/ntp.conf, configuration for ntpd

driftfile /var/lib/ntp/ntp.drift
statsdir /var/log/ntpstats/

statistics loopstats peerstats clockstats
filegen loopstats file loopstats type day enable
filegen peerstats file peerstats type day enable
filegen clockstats file clockstats type day enable


# You do need to talk to an NTP server or two (or three).

# By default, exchange time with everybody, but don't allow configuration.
# See /usr/share/doc/ntp-doc/html/accopt.html for details.
restrict default kod notrap nomodify nopeer noquery

# Local users may interrogate the ntp server more closely.
restrict 127.0.0.1 nomodify

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
server ntp.ubuntu.com 
server wuarchive.wustl.edu
server clock.psu.edu
server libra.rice.edu
```

---

### Post by jordon on 2007-08-06
Could it be that hardly any of the servers I selected responded to pings? I pinged the 18 North American NTP servers listed in the Time and Date Settings, and only 6 responded (none of which I had chosen). I've chosen one that works. The "Synchronize Now" button still doesn't work, but I'll have to wait and see if the clock will synchronize automatically.

---

### Post by jordon on 2007-08-08
The servers I've chosen (for now) are 0.us.pool.ntp.org, 1.us.pool.ntp.org, 2.us.pool.ntp.org, and 3.us.pool.ntp.org. I can set the time manually with

```
sudo ntpdate -u 0.us.pool.ntp.org
```

but I see in these lines in my daemon.log every few hours:

```
Aug  8 20:01:27 dell ntpd_initres[5792]: host name not found: 0.us.pool.ntp.org
Aug  8 20:01:27 dell ntpd_initres[5792]: couldn't resolve `0.us.pool.ntp.org', giving up on it
Aug  8 20:01:27 dell ntpd_initres[5792]: host name not found: 1.us.pool.ntp.org
Aug  8 20:01:27 dell ntpd_initres[5792]: couldn't resolve `1.us.pool.ntp.org', giving up on it
Aug  8 20:01:27 dell ntpd_initres[5792]: host name not found: 2.us.pool.ntp.org
Aug  8 20:01:27 dell ntpd_initres[5792]: couldn't resolve `2.us.pool.ntp.org', giving up on it
Aug  8 20:01:27 dell ntpd_initres[5792]: host name not found: 3.us.pool.ntp.org
Aug  8 20:01:27 dell ntpd_initres[5792]: couldn't resolve `3.us.pool.ntp.org', giving up on it
```

Any ideas, anyone?

---

### Post by wieman01 on 2007-08-09
> **jordon said:**
> The servers I've chosen (for now) are 0.us.pool.ntp.org, 1.us.pool.ntp.org, 2.us.pool.ntp.org, and 3.us.pool.ntp.org. I can set the time manually with

```
sudo ntpdate -u 0.us.pool.ntp.org
```

but I see in these lines in my daemon.log every few hours:

```
Aug  8 20:01:27 dell ntpd_initres[5792]: host name not found: 0.us.pool.ntp.org
Aug  8 20:01:27 dell ntpd_initres[5792]: couldn't resolve `0.us.pool.ntp.org', giving up on it
Aug  8 20:01:27 dell ntpd_initres[5792]: host name not found: 1.us.pool.ntp.org
Aug  8 20:01:27 dell ntpd_initres[5792]: couldn't resolve `1.us.pool.ntp.org', giving up on it
Aug  8 20:01:27 dell ntpd_initres[5792]: host name not found: 2.us.pool.ntp.org
Aug  8 20:01:27 dell ntpd_initres[5792]: couldn't resolve `2.us.pool.ntp.org', giving up on it
Aug  8 20:01:27 dell ntpd_initres[5792]: host name not found: 3.us.pool.ntp.org
Aug  8 20:01:27 dell ntpd_initres[5792]: couldn't resolve `3.us.pool.ntp.org', giving up on it
```

Any ideas, anyone?
When you ping them do you get a response?

---

### Post by jordon on 2007-08-09
> **wieman01 said:**
> When you ping them do you get a response?

Each address resolves to a random NTP server, which is supposed to work. When I tried, two of them responded to a ping, and two didn't.

---

### Post by Jason Quinn on 2008-04-17
I just had the same problem with Ubuntu 7.10 (Gusty). Had to use command line to fix. If "Syncronize Now" is grayed out because it needs su permission, that's pretty stupid. It should prompt for the superuser password instead of being grayed out.

---

