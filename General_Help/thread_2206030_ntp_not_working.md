---
title: "ntp not working"
date: 2014-02-17
forum: General Help
---

### Post by stephenbbb on 2014-02-17
scb@scb-desktop:~$ sudo ntpdate north-america.pool.ntp.org
[sudo] password for scb: 
17 Feb 10:35:40 ntpdate[2827]: no server suitable for synchronization found

scb@scb-desktop:~$ sudo ntpdate ntp.ubuntu.com
17 Feb 10:36:55 ntpdate[2848]: no server suitable for synchronization found

scb@scb-desktop:~$ uname -a
Linux scb-desktop 3.2.0-58-generic #88-Ubuntu SMP Tue Dec 3 17:40:43 UTC 2013 i686 athlon i386 GNU/Linux
scb@scb-desktop:~$ date
Mon Feb 17 10:40:33 EST 2014

the datetime is wrong and it won't fix it.

---

### Post by Dave_L on 2014-02-17
Maybe it's just a temporary situation.

Can you ping those servers:
```
ping ntp.ubuntu.com
```

Does the debug option give any more useful information?
```
sudo ntpdate -d ntp.ubuntu.com
```

You could try some other servers from the lists here: [http://support.ntp.org/bin/view/Servers/WebHome](http://support.ntp.org/bin/view/Servers/WebHome)

---

### Post by SeijiSensei on 2014-02-17
The official Ubuntu NTP servers are 0.ubuntu.pool.ntp.org through 3.ubuntu.pool.ntp.org.  All of these use "round-robin" DNS and resolve to multiple addresses:

```

Seiji@GhostWorld:~$ host 0.ubuntu.pool.ntp.org
0.ubuntu.pool.ntp.org has address 173.44.32.10
0.ubuntu.pool.ntp.org has address 198.199.100.18
0.ubuntu.pool.ntp.org has address 199.7.177.206
0.ubuntu.pool.ntp.org has address 162.210.196.6

```

---

### Post by buzzingrobot on 2014-02-17
The NTP servers and protocol have very recently been leveraged for some huge DDOS attacks.  Maybe that accounts for some of the servers lack of availability.

---

### Post by Dave_L on 2014-02-17
> **buzzingrobot said:**
> The NTP servers and protocol have very recently been leveraged for some huge DDOS attacks.  Maybe that accounts for some of the servers lack of availability.

Could that also affect the accuracy of the ntpdate results?

---

### Post by buzzingrobot on 2014-02-17
> **Dave_L said:**
> Could that also affect the accuracy of the ntpdate results?

I don't know.  I don't know what happens if an intelligible response isn't received from the time servers. I'd think it would simply continue with the last good response, but maybe not,

---

### Post by SeijiSensei on 2014-02-17
Works for me using the first server for 0.ubuntu.pool.ntp.org:

```
Seiji@GhostWorld:~$ sudo ntpdate 173.44.32.10
17 Feb 10:01:14 ntpdate[17930]: adjust time server 173.44.32.10 offset 0.002600 sec

```

If I run it against 0.ubuntu.pool.ntp.org, I unsurprisingly get a different server but a similar result.

---

