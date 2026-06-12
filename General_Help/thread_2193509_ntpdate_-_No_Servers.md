---
title: "ntpdate - No Servers"
date: 2013-12-13
forum: General Help
---

### Post by echotech2 on 2013-12-13
Ubuntu 13.10, all updates.

  I'm not sure how to fix this:
 
dave@scamper:~$ ntpdate
13 Dec 06:45:34 ntpdate[23690]: no servers can be used, exiting

  (if it needs fixing, lol)

  --Dave

---

### Post by ian-weisser on 2013-12-13
That error usually means that ntpdate cannot find a reliable server. Since there are *lots* of reliable NTP servers on the internet, that usually means that your system is being blocked from seeing them (by a firewall or proxy), or you have told NTP to ignore them (by editing the config file).

Are you behind a proxy? Or on a network that provides an NTP server?

Have you changed any of the settings in the /etc/ntp.conf file?

---

### Post by efflandt on 2013-12-13
There may not be any /etc/ntp.conf by default, in which case you would need to include ntp server(s) on the **ntpdate** command line.

**ntpdate-debian** command uses /etc/default/ntpdate, which by default polls ntp.ubuntu.com (unless you changed that file or also had /etc/ntp.conf properly configured). Even if properly configured either ntpdate command needs root access:```
efflandt@xps8100-1204:~$ sudo ntpdate
13 Dec 21:25:23 ntpdate[9429]: no servers can be used, exiting
efflandt@xps8100-1204:~$ sudo ntpdate-debian
13 Dec 21:25:38 ntpdate[9432]: step time server 91.189.89.199 offset -1.103506 sec
```

---

### Post by ian-weisser on 2013-12-14
> **efflandt said:**
> Even if properly configured either ntpdate command needs root access

Oh! Great catch!

---

### Post by echotech2 on 2013-12-14
Thanks for the replies.  Using sudo didn't work.

dave@scamper:~$ sudo ntpdate
[sudo] password for dave: 
14 Dec 06:03:39 ntpdate[27536]: no servers can be used, exiting

and

dave@scamper:~$ sudo ntpdate-debian
[sudo] password for dave: 
14 Dec 06:18:04 ntpdate[27667]: the NTP socket is in use, exiting


  I am using a caching proxy (Polipo -  [http://www.pps.univ-paris-diderot.fr/~jch/software/polipo/](http://www.pps.univ-paris-diderot.fr/~jch/software/polipo/) ) and it is set up as "Network Proxy", "Apply System-Wide".  I was thinking (Note: caffeine level is being adjusted and may not have reached optimum level yet...)  maybe Polipo isn't passing whatever protocol ntpdate uses, but I have been using Polipo for several years without any apparent problems.

ntp.conf:

# /etc/ntp.conf, configuration for ntpd; see ntp.conf(5) for help
driftfile /var/lib/ntp/ntp.drift
# Enable this if you want statistics to be logged.
#statsdir /var/log/ntpstats/
statistics loopstats peerstats clockstats
filegen loopstats file loopstats type day enable
filegen peerstats file peerstats type day enable
filegen clockstats file clockstats type day enable
# Specify one or more NTP servers.
# Use servers from the NTP Pool Project. Approved by Ubuntu Technical Board
# on 2011-02-08 (LP: #104525). See [http://www.pool.ntp.org/join.html](http://www.pool.ntp.org/join.html) for
# more information.
server 0.ubuntu.pool.ntp.org
server 1.ubuntu.pool.ntp.org
server 2.ubuntu.pool.ntp.org
server 3.ubuntu.pool.ntp.org
# Use Ubuntu's ntp server as a fallback.
server ntp.ubuntu.com
# Access control configuration; see /usr/share/doc/ntp-doc/html/accopt.html for
# details.  The web page <http://support.ntp.org/bin/view/Support/AccessRestrictions>
# might also be helpful.
# Note that "restrict" applies to both servers and clients, so a configuration
# that might be intended to block requests from certain clients could also end
# up blocking replies from your own upstream servers.
# By default, exchange time with everybody, but don't allow configuration.
restrict -4 default kod notrap nomodify nopeer noquery
restrict -6 default kod notrap nomodify nopeer noquery


--Dave

---

### Post by echotech2 on 2013-12-16
OK, I bypassed the Polipo proxy ("Network Proxy"=None, clicked "Apply System-Wide") and I get the same output.

dave@scamper:~$ sudo ntpdate
[sudo] password for dave: 
16 Dec 06:26:50 ntpdate[3576]: no servers can be used, exiting

and

dave@scamper:~$ sudo ntpdate-debian
16 Dec 06:27:36 ntpdate[3578]: the NTP socket is in use, exiting

  Does this mean that my clock is not syncing with ANY time server?

  --Dave

---

### Post by echotech2 on 2013-12-19
I say, I say.  Methinks this could use a a slight nudge.

---

### Post by Lars Noodén on 2013-12-19
You have [ntpd](http://manpages.ubuntu.com/manpages/saucy/en/man8/ntpd.8.html) running already.  It is using the NTP socket already, making it unavailable to ntpdate.

```

service ntp status

```

It synchronizes the clock for you, doing so continuously in the background.  You can track its progress in syslog.

```

sudo grep ntpd /var/log/syslog

```

If you look in the older, compressed syslogs you can use zgrep instead.

If you really want to run ntpdate, then you have to pause ntpd.

```

sudo service ntp stop
sudo ntpdate *3.ubuntu.pool.ntp.org*
sudo service ntp start

```

You can point ntpdate at whichever time server you want, not just one from Ubuntu's pool.  If you want to use whatever is in /etc/ntp.conf, then use [ntpdate-debian](http://manpages.ubuntu.com/manpages/saucy/en/man8/ntpdate-debian.8.html) instead.  However, unless your clock is somehow off by a huge amount, ntpd will take care of the adjustment for you automatically in the background.

---

### Post by philinux on 2013-12-19
Minor point. You dont need sudo for this.

```
grep ntpd /var/log/syslog
```  :P

---

### Post by Lars Noodén on 2013-12-19
> **philinux said:**
> Minor point. You dont need sudo for this.

Thanks.  My system is a little more customized, I should have tried a generic machine.  If you are a member of the group adm sudo is not needed.  Since that is often parceled out along with full sudo access, I guess sudo is not needed.

---

### Post by philinux on 2013-12-19
> **Lars Noodén said:**
> Thanks.  My system is a little more customized, I should have tried a generic machine.  If you are a member of the group adm sudo is not needed.  Since that is often parceled out along with full sudo access, I guess sudo is not needed.

Yeah mines a straight vanilla ubuntu install.

---

### Post by echotech2 on 2013-12-20
Thanks all, I was just mainly wondering if the time was being kept correct.  

dave@scamper:~$ service ntp status
 * NTP server is running

---

