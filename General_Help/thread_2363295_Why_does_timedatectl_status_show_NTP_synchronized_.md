---
title: "Why does timedatectl status show NTP synchronized is no ?"
date: 2017-06-08
forum: General Help
---

### Post by suaro on 2017-06-08
I'm using Ubuntu 16.04.2 LTS and trying to determine why the status command is indicating NTP synchronized is set to no?
Hoping someone can point me in the right direction 

[FONT=courier new]# timedatectl status[/FONT]
[FONT=courier new]      Local time: Thu 2017-06-08 12:44:51 UTC[/FONT]
[FONT=courier new]  Universal time: Thu 2017-06-08 12:44:51 UTC[/FONT]
[FONT=courier new]        RTC time: Thu 2017-06-08 12:47:28[/FONT]
[FONT=courier new]       Time zone: Etc/UTC (UTC, +0000)[/FONT]
[FONT=courier new] Network time on: yes[/FONT]
[FONT=courier new]**NTP synchronized: no    <<<**[/FONT]
[FONT=courier new] RTC in local TZ: no[/FONT]

[FONT=courier new]Below seems to indicate my time is sync'd:

[/FONT][FONT=courier new]# ntpq -c lpeer[/FONT]
[FONT=courier new]     remote           refid      st t when poll reach   delay   offset  jitter[/FONT]
[FONT=courier new]==============================================================================[/FONT]
[FONT=courier new] 0.ubuntu.pool.n .POOL.          16 p    -   64    0    0.000    0.000   0.000[/FONT]
[FONT=courier new] 1.ubuntu.pool.n .POOL.          16 p    -   64    0    0.000    0.000   0.000[/FONT]
[FONT=courier new] 2.ubuntu.pool.n .POOL.          16 p    -   64    0    0.000    0.000   0.000[/FONT]
[FONT=courier new] 3.ubuntu.pool.n .POOL.          16 p    -   64    0    0.000    0.000   0.000[/FONT]
[FONT=courier new] ntp.ubuntu.com  .POOL.          16 p    -   64    0    0.000    0.000   0.000[/FONT]
**[FONT=courier new]*time-c.nist.gov .NIST.           1 u   94  256  377    5.267   -0.092   4.271[/FONT]**
[FONT=courier new]-45.33.91.95 (eq 209.51.161.238   2 u    1  256  377    7.254    3.792   3.403[/FONT]
[FONT=courier new]+helium.constant 128.59.0.245     2 u  102  256  377    7.171   -1.196   4.650[/FONT]
[FONT=courier new]+97-127-86-33.mp .PPS.            1 u  100  256  377   31.419   -1.918   5.092[/FONT]
[FONT=courier new]+ntp.your.org    .CDMA.           1 u  186  256  377   20.197   -0.006   4.839[/FONT]


[FONT=courier new]# ntpstat[/FONT]
[FONT=courier new]synchronised to NTP server (129.6.15.30) at stratum 2[/FONT]
[FONT=courier new]   time correct to within 16 ms[/FONT]
[FONT=courier new]   polling server every 256 s[/FONT]


Checking to see if I'm overlooking anything. 


Thank you

---

### Post by #&amp;thj^% on 2017-06-08
Odd?
```
apt policy ntp
```
Mine shows;
```
apt policy ntp
ntp:
  Installed: 1:4.2.8p10+dfsg-1ubuntu1
  Candidate: 1:4.2.8p10+dfsg-1ubuntu1
  Version table:
 *** 1:4.2.8p10+dfsg-1ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu artful/main amd64 Packages
        100 /var/lib/dpkg/status

```
And:
```
$ timedatectl status
      Local time: Thu 2017-06-08 09:30:25 MDT
  Universal time: Thu 2017-06-08 15:30:25 UTC
        RTC time: Thu 2017-06-08 15:30:24
       Time zone: America/Denver (MDT, -0600)
 Network time on: yes
**NTP synchronized: yes**
 RTC in local TZ: no

```
 

The system clock runs in the kernel and after getting its initial time from the hardware clock it will then synchronize with an NTP server to become up to date.

We can manually synchronize the hardware clock to the system clock if required, this would generally only be required if there was no NTP server available.


By default NTP uses UDP port 123, so if you are connecting over the Internet to an external NTP server ensure that outbound UDP 123 traffic is allowed out to the NTP server specified in your configuration. Normally by default all outbound traffic is allowed so this should not be a problem. Public NTP servers on the Internet should already be configured to accept inbound NTP traffic.

If you are instead running your own local NTP server within your own network you will need to ensure that your servers can connect inbound to the NTP server on UDP port 123,

---

### Post by suaro on 2017-06-08
Thanks. I have the correct ntp libraries (same as yours) and sync is working and confirmed from network trace.  No problem with outbound connections to time servers. 
Curious to know why two different commands are showing different things:

ntpstat shows correct information:

[COLOR=#000000][FONT=&quot]# ntpstat[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]synchronised to NTP server (129.6.15.30) at stratum 2[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]time correct to within 16 ms[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]polling server every 256 s

However [/FONT][/COLOR][COLOR=#000000][FONT=&quot]timedatectl status doesn't seem to agree. 
No biggie. [/FONT][/COLOR]

---

### Post by #&amp;thj^% on 2017-06-08
I too find it Curious. :)
Well give this a shot:
```
timedatectl set-ntp true 

```
As Root.
As Shown here:
```
$ sudo timedatectl set-ntp true 
[sudo] password for me: 
me@me-750-417c:~$ timedatectl status
      Local time: Thu 2017-06-08 11:10:57 MDT
  Universal time: Thu 2017-06-08 17:10:57 UTC
        RTC time: Thu 2017-06-08 17:10:56
       Time zone: America/Denver (MDT, -0600)
 Network time on: yes
NTP synchronized: yes
 RTC in local TZ: no

```

---

