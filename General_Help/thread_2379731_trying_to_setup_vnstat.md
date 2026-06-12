---
title: "trying to setup vnstat"
date: 2017-12-08
forum: General Help
---

### Post by jgw on 2017-12-08
I have just installed vnstat and vnstati and am now trying to set it up.  Here is what I have so far:

greg@movies:~$ vnstat --iflist
Available interfaces: tun0 (10 Mbit) enp2s0 (100 Mbit) lo 

greg@movies:~$ vnstat -u -i enp2s0
Error: Unable to create database backup "/var/lib/vnstat/.enp2s0".

I then went and check /var/lib/vnstat/.enp2s0 and found, in the vnstat file:
/var/lib/vnstat/enp2s0
/var/lib/vnstat/tun0
/var/lib/vnstat/.enp2s0
/var/lib/vnstat/.tun0

Everytime I run the vnstat -u -i enp2s0 I get the same unable to create message and, I think, it may add another line.  I also notice that the file has listed available interfaces with a '.' and without a '.'.   I am currently stopped as I never have seen the "a new database has been created" notification" so I thought I had better stop and get a bit of help before I did something bad.

I also did:
greg@movies:~$ systemctl status vnstat
&#9679; vnstat.service - vnStat network traffic monitor
   Loaded: loaded (/lib/systemd/system/vnstat.service; enabled; vendor preset: e
   Active: active (running) since Fri 2017-12-08 15:23:42 PST; 39min ago
     Docs: man:vnstatd(1)
           man:vnstat(1)
           man:vnstat.conf(5)
 Main PID: 2899 (vnstatd)
   CGroup: /system.slice/vnstat.service
           &#9492;&#9472;2899 /usr/sbin/vnstatd -n

Dec 08 15:23:42 movies systemd[1]: Started vnStat network traffic monitor.
lines 1-11/11 (END)

reg@movies:~$ ls /var/lib/vnstat/
enp2s0  tun0



Thank you...........

---

### Post by deadflowr on 2017-12-09
> Everytime I run the vnstat -u -i enp2s0 I get the same unable to create message
It's caused by having an already existing database setup. Most likely created via root.
Remove the old files (perhaps just clear out the enp2s0 and tun0 files in the /var/lib/vnstat directory)
Either remove them or move them somewhere outside that directory.
Then it should run without any problems.

---

### Post by again? on 2017-12-09
You need to create the database as root.
```
**sudo** vnstat -u -i enp2s0
```

---

### Post by jgw on 2017-12-09
Thank you for the replies.  I followed both suggestions and just did a vnstate -u -i enp2s0 and it seemed to work (no error message)vnstat -u -i wlan0.  The file contents are now:
enp2s0
.enp2s0

I suspect I should now do a vnstat -u -i tun0?  (which, in theory, will collect data wilst on, and off, the vpn?)

---

### Post by jgw on 2017-12-10
I continue to mess with vnstat.  Now I have a new problem.  When I do a status request I am told Unable to create database backup "/var/lib/vnstat".  The permissions are; owner-nobody, group-vnstat.  I also tried to making vnstat the owner and myself as group, neither worked.  In each case I also changed the 4 documents;enp2so, tun0, .enp2so, and .tun0 permissions as well and then checked to make sure they all took.  I also noted that vnstat was not auto starting with boot so I put it in the boot programs with "sudo /etc/init.d/vnstat start"  (I guess I could have also used "systemctl start vnstat".  I used "systemctl status vnstat" for the status report.  I also tried the status with a sudo in front - it made no difference.

Thoughts?

---

### Post by again? on 2017-12-10
It's been a few years since I used vnstat and it appears to require more setting up under systemd.
I installed vnstat and vnstati a few days ago in response to your other [thread]("https://ubuntuforums.org/showthread.php?t=2379626").
vnstat created the initial database but doesn't look like it's being updated.
```
**[COLOR="#008000"]glen@GU17:~$[/COLOR] vnstat -d**

 enp3s0  /  daily

         day         rx      |     tx      |    total    |   avg. rate
     ------------------------+-------------+-------------+---------------
      08/12/17         8 KiB |       4 KiB |      12 KiB |    0.00 kbit/s
      11/12/17         0 KiB |       0 KiB |       0 KiB |    0.00 kbit/s
     ------------------------+-------------+-------------+---------------
     estimated        --     |      --     |      --     |

**[COLOR="#008000"]glen@GU17:~$[/COLOR] systemctl status vnstat**
&#9679; vnstat.service - vnStat network traffic monitor
   Loaded: loaded (/lib/systemd/system/vnstat.service; enabled; vendor preset: enabled)
   Active: active (running) since Sun 2017-12-10 14:30:08 AWST; 21h ago
     Docs: man:vnstatd(1)
           man:vnstat(1)
           man:vnstat.conf(5)
 Main PID: 1012 (vnstatd)
    Tasks: 1 (limit: 4915)
   CGroup: /system.slice/vnstat.service
           &#9492;&#9472;1012 /usr/sbin/vnstatd -n

Dec 11 00:35:14 GU17 vnstatd[1012]: Error: Unable to create database backup "/var/lib/vnstat/.enp3s0".
Dec 11 00:35:14 GU17 vnstatd[1012]: Error: Unable to create database backup "/var/lib/vnstat/.enp3s0".
Dec 11 00:35:14 GU17 vnstatd[1012]: Error: Unable to create database backup "/var/lib/vnstat/.enp3s0".
Dec 11 05:40:15 GU17 vnstatd[1012]: Error: Unable to create database backup "/var/lib/vnstat/.enp3s0".
Dec 11 05:40:15 GU17 vnstatd[1012]: Error: Unable to create database backup "/var/lib/vnstat/.enp3s0".
Dec 11 05:40:15 GU17 vnstatd[1012]: Error: Unable to create database backup "/var/lib/vnstat/.enp3s0".
Dec 11 10:50:16 GU17 vnstatd[1012]: Error: Unable to create database backup "/var/lib/vnstat/.enp3s0".
Dec 11 10:50:16 GU17 vnstatd[1012]: Error: Unable to create database backup "/var/lib/vnstat/.enp3s0".
Dec 11 10:50:16 GU17 vnstatd[1012]: Error: Unable to create database backup "/var/lib/vnstat/.enp3s0".
Warning: Journal has been rotated since unit was started. Log output is incomplete or unavailable.

```

Currently trying the fix from [HERE]("https://bugs.launchpad.net/ubuntu/+source/vnstat/+bug/1285706/comments/1").
Rebooted and watched a youtube vid to get some data.
Appears to be working. 
No "*Error: Unable to create database backup*" warnings.
```
**[COLOR="#008000"]glen@GU17:~$[/COLOR] systemctl status vnstat**
&#9679; vnstat.service - vnStat network traffic monitor
   Loaded: loaded (/lib/systemd/system/vnstat.service; enabled; vendor preset: enabled)
   Active: active (running) since Mon 2017-12-11 11:55:48 AWST; 2min 14s ago
     Docs: man:vnstatd(1)
           man:vnstat(1)
           man:vnstat.conf(5)
 Main PID: 1009 (vnstatd)
    Tasks: 1 (limit: 4915)
   CGroup: /system.slice/vnstat.service
           &#9492;&#9472;1009 /usr/sbin/vnstatd -n

Dec 11 11:55:48 GU17 systemd[1]: Started vnStat network traffic monitor.

**[COLOR="#008000"]glen@GU17:~$[/COLOR] vnstat**
Database updated: Mon Dec 11 12:00:49 2017

   enp3s0 since 08/12/17

          rx:  109.79 MiB      tx:  3.37 MiB      total:  113.16 MiB

   monthly
                     rx      |     tx      |    total    |   avg. rate
     ------------------------+-------------+-------------+---------------
       Dec '17    109.79 MiB |    3.37 MiB |  113.16 MiB |    1.06 kbit/s
     ------------------------+-------------+-------------+---------------
     estimated       332 MiB |       9 MiB |     341 MiB |

   daily
                     rx      |     tx      |    total    |   avg. rate
     ------------------------+-------------+-------------+---------------
      08/12/17         8 KiB |       4 KiB |      12 KiB |    0.00 kbit/s
         today    109.78 MiB |    3.37 MiB |  113.15 MiB |   21.43 kbit/s
     ------------------------+-------------+-------------+---------------
     estimated       218 MiB |       6 MiB |     224 MiB |
```
Current permissions....
```
**[COLOR="#008000"]glen@GU17:~$[/COLOR] ls -al /var/lib/vnstat**
total 16
drwxr-xr-x  2 vnstat vnstat 4096 Dec  8 06:48 .
drwxr-xr-x 84 root   root   4096 Dec 10 12:42 ..
-rw-r--r--  1 vnstat vnstat 2792 Dec 11 12:25 enp3s0
-rw-r--r--  1 vnstat vnstat 2792 Dec 11 12:25 .enp3s0
```
Will monitor and get back to you.

---

### Post by jgw on 2017-12-11
Thank you for the reply. 

I am wondering, is there a better program for getting this info?  

My reason for wanting to do this is that I am considering switching my isp and that service sets a monthly limit.  I thought that limit (400gb) should be enough but wanted to make sure before I committed.

---

### Post by again? on 2017-12-11
There are probably other methods but not that I have used and can recommend.
Did you try setting the correct permissions. [https://bugs.launchpad.net/ubuntu/+source/vnstat/+bug/1285706/comments/1](https://bugs.launchpad.net/ubuntu/+source/vnstat/+bug/1285706/comments/1)

It worked for me.
```
**[COLOR="#008000"]glen@GU17:~$[/COLOR] vnstat**
Database updated: Tue Dec 12 04:45:52 2017

   enp3s0 since 08/12/17

          rx:  1.52 GiB      tx:  159.38 MiB      total:  1.68 GiB

   monthly
                     rx      |     tx      |    total    |   avg. rate
     ------------------------+-------------+-------------+---------------
       Dec '17      1.52 GiB |  159.38 MiB |    1.68 GiB |   15.00 kbit/s
     ------------------------+-------------+-------------+---------------
     estimated      4.35 GiB |     453 MiB |    4.79 GiB |

   daily
                     rx      |     tx      |    total    |   avg. rate
     ------------------------+-------------+-------------+---------------
     yesterday      1.49 GiB |  157.22 MiB |    1.65 GiB |  160.00 kbit/s
         today     29.73 MiB |    2.15 MiB |   31.88 MiB |   15.22 kbit/s
     ------------------------+-------------+-------------+---------------
     estimated       146 MiB |      10 MiB |     156 MiB |
```

If you can't get the data base to work you could still use live mode.
You can run in background terminal using...
```
vnstat -l -i enp2s0
```
When you stop the command using ctrl+c it will show a summary.
Should be able to do some rough estimates from that info.
```
**[COLOR="#008000"]glen@GU17:~$[/COLOR] vnstat -l -i enp3s0**
Monitoring enp3s0...    (press CTRL-C to stop)

   rx:        1 kbit/s     1 p/s          tx:        1 kbit/s     1 p/s


 enp3s0  /  traffic statistics

                           rx         |       tx
--------------------------------------+------------------
  bytes                     1.67 MiB  |         379 KiB
--------------------------------------+------------------
          max             886 kbit/s  |      101 kbit/s
      average           16.22 kbit/s  |     3.60 kbit/s
          min               0 kbit/s  |        0 kbit/s
--------------------------------------+------------------
  packets                       2304  |            2298
--------------------------------------+------------------
          max                 89 p/s  |          57 p/s
      average                  2 p/s  |           2 p/s
          min                  0 p/s  |           0 p/s
--------------------------------------+------------------
  time                 14.07 minutes
```

---

### Post by jgw on 2017-12-11
Thanks for the reply.

Permissions: The permissions are; owner-nobody, group-vnstat. I also tried to making vnstat the owner and myself as group, neither worked. In each case I also changed the 4 documents;enp2so, tun0, .enp2so, and .tun0 permissions as well and then checked to make sure they all took

---

### Post by again? on 2017-12-11
You need to edit 2 files.
**1)** /etc/vnstat.conf ...changing DaemonUser and DaemonGroup from "" to "vnstat".
```
**[COLOR="#008000"]glen@GU17:~$[/COLOR] cat /etc/vnstat.conf **
# vnStat 1.15 config file
##

# default interface
Interface "eth0"

# location of the database directory
DatabaseDir "/var/lib/vnstat"

# locale (LC_ALL) ("-" = use system locale)
Locale "-"

# on which day should months change
MonthRotate 1

# date output formats for -d, -m, -t and -w
# see 'man date' for control codes
DayFormat    "%x"
MonthFormat  "%b '%y"
TopFormat    "%x"

# characters used for visuals
RXCharacter       "%"
TXCharacter       ":"
RXHourCharacter   "r"
TXHourCharacter   "t"

# how units are prefixed when traffic is shown
# 0 = IEC standard prefixes (KiB/MiB/GiB/TiB)
# 1 = old style binary prefixes (KB/MB/GB/TB)
UnitMode 0

# output style
# 0 = minimal & narrow, 1 = bar column visible
# 2 = same as 1 except rate in summary and weekly
# 3 = rate column visible
OutputStyle 3

# used rate unit (0 = bytes, 1 = bits)
RateUnit 1

# try to detect interface maximum bandwidth, 0 = disable feature
# MaxBandwidth will be used as fallback value when enabled
BandwidthDetection 1

# maximum bandwidth (Mbit) for all interfaces, 0 = disable feature
# (unless interface specific limit is given)
MaxBandwidth 1000

# interface specific limits
#  example 8Mbit limit for eth0 (remove # to activate):
#MaxBWeth0 8

# how many seconds should sampling for -tr take by default
Sampletime 5

# default query mode
# 0 = normal, 1 = days, 2 = months, 3 = top10
# 4 = exportdb, 5 = short, 6 = weeks, 7 = hours
QueryMode 0

# filesystem disk space check (1 = enabled, 0 = disabled)
CheckDiskSpace 1

# database file locking (1 = enabled, 0 = disabled)
UseFileLocking 1

# how much the boot time can variate between updates (seconds)
BootVariation 15

# log days without traffic to daily list (1 = enabled, 0 = disabled)
TrafficlessDays 1


# vnstatd
##

# switch to given user when started as root (leave empty to disable)
DaemonUser "[COLOR="#FF0000"]vnstat[/COLOR]"

# switch to given user when started as root (leave empty to disable)
DaemonGroup "[COLOR="#FF0000"]vnstat[/COLOR]"

# how often (in seconds) interface data is updated
UpdateInterval 30

# how often (in seconds) interface status changes are checked
PollInterval 5

# how often (in minutes) data is saved to file
SaveInterval 5

# how often (in minutes) data is saved when all interface are offline
OfflineSaveInterval 30

# how often (in minutes) bandwidth detection is redone when
# BandwidthDetection is enabled (0 = disabled)
BandwidthDetectionInterval 5

# force data save when interface status changes (1 = enabled, 0 = disabled)
SaveOnStatusChange 1

# enable / disable logging (0 = disabled, 1 = logfile, 2 = syslog)
UseLogging 2

# create dirs if needed (1 = enabled, 0 = disabled)
CreateDirs 1

# update ownership of files if needed (1 = enabled, 0 = disabled)
UpdateFileOwner 1

# file used for logging if UseLogging is set to 1
LogFile "/var/log/vnstat/vnstat.log"

# file used as daemon pid / lock file
PidFile "/var/run/vnstat/vnstat.pid"


# vnstati
##

# title timestamp format
HeaderFormat "%x %H:%M"

# show hours with rate (1 = enabled, 0 = disabled)
HourlyRate 1

# show rate in summary (1 = enabled, 0 = disabled)
SummaryRate 1

# layout of summary (1 = with monthly, 0 = without monthly)
SummaryLayout 1

# transparent background (1 = enabled, 0 = disabled)
TransparentBg 0

# image colors
CBackground     "FFFFFF"
CEdge           "AEAEAE"
CHeader         "606060"
CHeaderTitle    "FFFFFF"
CHeaderDate     "FFFFFF"
CText           "000000"
CLine           "B0B0B0"
CLineL          "-"
CRx             "92CF00"
CTx             "606060"
CRxD            "-"
CTxD            "-"
```

**2)** /lib/systemd/system/vnstat.service ...changing User from "vnstat" to "root".
```
**[COLOR="#008000"]glen@GU17:~$[/COLOR] cat /lib/systemd/system/vnstat.service**
[Unit]
Description=vnStat network traffic monitor
Documentation=man:vnstatd(1) man:vnstat(1) man:vnstat.conf(5)
After=network.target

[Service]
ExecStart=/usr/sbin/vnstatd -n
ExecReload=/bin/kill -HUP $MAINPID
User=[COLOR="#FF0000"]root[/COLOR]

[Install]
WantedBy=multi-user.target
```
Delete database...
```
sudo vnstat --force --delete -i enp2s0
```

Reboot and create database...
```
sudo vnstat -u -i enp2s0
```

---

### Post by jgw on 2017-12-23
thanks for all the help!  Apologize for not getting back to this and Merry Christmas and have a prosperous and successful New Year!

Anyway, I checked my files and they are all as suggested.  

Here is some info:
&#9679; vnstat.service - vnStat network traffic monitor
   Loaded: loaded (/lib/systemd/system/vnstat.service; enabled; vendor preset: enabled)
   Active: active (running) since Tue 2017-12-12 08:45:00 PST; 1 weeks 4 days ago
     Docs: man:vnstatd(1)
           man:vnstat(1)
           man:vnstat.conf(5)
 Main PID: 955 (vnstatd)
   CGroup: /system.slice/vnstat.service
           &#9492;&#9472;955 /usr/sbin/vnstatd -n

Warning: Journal has been rotated since unit was started. Log output is incomplete or unavailable.

greg@movies:~$  ls -al /var/lib/vnstat
total 20
drwxrwxr-x  2 vnstat vnstat 4096 Dec 12 08:59 .
drwxr-xr-x 76 root   root   4096 Dec  8 15:23 ..
-rw-r--r--  1 vnstat vnstat 2792 Dec 12 08:59 enp2s0
-rw-rw-r--  1 vnstat vnstat 2792 Dec 23 09:23 tun0
-rw-rw-r--  1 vnstat vnstat 2792 Dec 23 09:23 .tun0

I stopped and started vnstat and a few minites later:
reg@movies:~$ vnstat

                      rx      /      tx      /     total    /   estimated
 tun0:
       Dec '17     76.35 GiB  /    5.70 GiB  /   82.05 GiB  /  113.58 GiB
     yesterday      1.02 GiB  /   93.05 MiB  /    1.11 GiB
         today     85.36 MiB  /    4.94 MiB  /   90.30 MiB  /     225 MiB

 enp2s0:
       Dec '17        87 KiB  /      52 KiB  /     139 KiB  /       0 KiB
     12/12/2017         0 KiB  /       0 KiB  /       0 KiB
         today        87 KiB  /      52 KiB  /     139 KiB  /      --    

From this I am assuming that vnstat continues working as I have rebooted my machine several times in the time frame (over a week) vnstat says it ran.  The problem is that something happened to stop the logging, ie. Warning: Journal has been rotated since unit was started. Log output is incomplete or unavailable.

I checked the vnstat site and see that their latest and greatest is 1.18  Perhaps I should update mine although synaptic has 1.14 is the latest it has available?  (suspect I should just leave it alone:
greg@movies:~$ vnstat --version
vnStat 1.14 by Teemu Toivola <tst at iki dot fi>

Anyway, now I have vnstat apparently running and starting on reboot but it is not dealing with its log/accumulations properly.

Thoughts?

---

### Post by again? on 2017-12-23
I think the log warning message is related to systemd and vnstat should function normally.
Do you get any messages if you run...
```
sudo vnstat -u -i enp2s0
```

I have had vnstat running for a couple of weeks now.

---

### Post by jgw on 2017-12-23
Here is what happened (there were no errors and I threw in a plain vnstat just for the heck of it):
greg@movies:~$ sudo vnstat -u -i enp2s0
[sudo] password for greg: 
greg@movies:~$ vnstat

                      rx      /      tx      /     total    /   estimated
 tun0:
       Dec '17     79.81 GiB  /    5.80 GiB  /   85.61 GiB  /  117.03 GiB
     yesterday      1.02 GiB  /   93.05 MiB  /    1.11 GiB
         today      3.54 GiB  /  101.33 MiB  /    3.64 GiB  /    5.39 GiB

 enp2s0:
       Dec '17      3.75 GiB  /  252.95 MiB  /    3.99 GiB  /    5.46 GiB
     12/12/2017         0 KiB  /       0 KiB  /       0 KiB
         today      3.75 GiB  /  252.95 MiB  /    3.99 GiB  /    5.90 GiB

---

### Post by jgw on 2018-01-10
Thank you for all the help!  I also apologize for having taken so long to get back to this (got busy, busy, busy)

I don't really know why or how but, now, it seems to be working and giving me my monthly total - pretty slick

Thanks again....................

---

