---
title: "force time sync on Ubuntu machine with Windows local machine or use NTP"
date: 2017-03-23
forum: General Help
---

### Post by kubanc on 2017-03-23
Hello.

Is it possible to force sync time on Ubuntu client with the time on some Windows machine which is on the same network.

I know there is command in CMD (net time \\server /set  /y OR w32tm /resync) to sync time on local Windows machine with the other machine on the network.

So, is it possible that I could do a cron job that would call a script which would sync time on Ubuntu with other Windows machine?

I have also tried with NTP but as I can see the Ubuntu machine is 50s behind the time on the machine that I have putten inside the ntp.conf.

**/etc/ntp.conf**
```
# /etc/ntp.conf, configuration for ntpd; see ntp.conf(5) for help

driftfile /var/lib/ntp/ntp.drift

# Enable this if you want statistics to be logged.
statsdir /var/log/ntpstats/

statistics loopstats peerstats clockstats
filegen loopstats file loopstats type day enable
filegen peerstats file peerstats type day enable
filegen clockstats file clockstats type day enable

# Specify one or more NTP servers.

# Use servers from the NTP Pool Project. Approved by Ubuntu Technical Board
# on 2011-02-08 (LP: #104525). See http://www.pool.ntp.org/join.html for
# more information.
#pool 0.ubuntu.pool.ntp.org iburst
#pool 1.ubuntu.pool.ntp.org iburst
#pool 2.ubuntu.pool.ntp.org iburst
#pool 3.ubuntu.pool.ntp.org iburst
pool 192.168.200.71 iburst

# Use Ubuntu's ntp server as a fallback.
#pool ntp.ubuntu.com

# Access control configuration; see /usr/share/doc/ntp-doc/html/accopt.html for
# details.  The web page <http://support.ntp.org/bin/view/Support/AccessRestrictions>
# might also be helpful.
#
# Note that "restrict" applies to both servers and clients, so a configuration
# that might be intended to block requests from certain clients could also end
# up blocking replies from your own upstream servers.

# By default, exchange time with everybody, but don't allow configuration.
restrict -4 default kod notrap nomodify nopeer noquery limited
restrict -6 default kod notrap nomodify nopeer noquery limited

# Local users may interrogate the ntp server more closely.
restrict 127.0.0.1
restrict ::1

# Needed for adding pool entries
restrict source notrap nomodify noquery

# Clients from this (example!) subnet have unlimited access, but only if
# cryptographically authenticated.
#restrict 192.168.123.0 mask 255.255.255.0 notrust


# If you want to provide time to your local subnet, change the next line.
# (Again, the address is an example only.)
#broadcast 192.168.123.255

# If you want to listen to time broadcasts on your local subnet, de-comment the
# next lines.  Please do this only if you trust everybody on the network!
#disable auth
#broadcastclient

#Changes recquired to use pps synchonisation as explained in documentation:
#http://www.ntp.org/ntpfaq/NTP-s-config-adv.htm#AEN3918

#server 127.127.8.1 mode 135 prefer    # Meinberg GPS167 with PPS
#fudge 127.127.8.1 time1 0.0042        # relative to PPS for my hardware

#server 127.127.22.1                   # ATOM(PPS)
#fudge 127.127.22.1 flag3 1            # enable PPS API

```

**timedatectl**
```

      Local time: &#269;et 2017-03-23 10:41:27 CET
  Universal time: &#269;et 2017-03-23 09:41:27 UTC
        RTC time: &#269;et 2017-03-23 19:44:17
       Time zone: Europe/Ljubljana (CET, +0100)
 Network time on: no
NTP synchronized: yes
 RTC in local TZ: no

```

**ntpstat:**
```

unsynchronised
   polling server every 8 s

```

**sudo ntpq -c lpeer**
```

     remote           refid      st t when poll reach   delay   offset  jitter
==============================================================================
 192.168.200.71  .POOL.          16 p    -   64    0    0.000    0.000   0.000

```

**tail -f /var/log/syslog**
```

Mar 23 10:36:26 tnm-VirtualBox ntpd[5733]: Soliciting pool server 192.168.200.71
Mar 23 10:37:30 tnm-VirtualBox ntpd[5733]: Soliciting pool server 192.168.200.71
Mar 23 10:38:35 tnm-VirtualBox ntpd[5733]: Soliciting pool server 192.168.200.71

```

[B]sudo service ntpstatus
[/B]```

&#9679; ntp.service - LSB: Start NTP daemon
   Loaded: loaded (/etc/init.d/ntp; bad; vendor preset: enabled)
   Active: active (running) since &#269;et 2017-03-23 10:36:25 CET; 11min ago
     Docs: man:systemd-sysv-generator(8)
  Process: 5093 ExecStop=/etc/init.d/ntp stop (code=exited, status=0/SUCCESS)
  Process: 5723 ExecStart=/etc/init.d/ntp start (code=exited, status=0/SUCCESS)
   CGroup: /system.slice/ntp.service
           &#9492;&#9472;5733 /usr/sbin/ntpd -p /var/run/ntpd.pid -g -u 121:129

mar 23 10:36:26 tnm-VirtualBox ntpd[5733]: Soliciting pool server 192.168.200.71
mar 23 10:37:30 tnm-VirtualBox ntpd[5733]: Soliciting pool server 192.168.200.71
mar 23 10:38:35 tnm-VirtualBox ntpd[5733]: Soliciting pool server 192.168.200.71
mar 23 10:39:42 tnm-VirtualBox ntpd[5733]: Soliciting pool server 192.168.200.71
mar 23 10:40:48 tnm-VirtualBox ntpd[5733]: Soliciting pool server 192.168.200.71
mar 23 10:41:54 tnm-VirtualBox ntpd[5733]: Soliciting pool server 192.168.200.71
mar 23 10:43:00 tnm-VirtualBox ntpd[5733]: Soliciting pool server 192.168.200.71
mar 23 10:44:07 tnm-VirtualBox ntpd[5733]: Soliciting pool server 192.168.200.71
mar 23 10:46:05 tnm-VirtualBox ntpd[5733]: Soliciting pool server 192.168.200.71
mar 23 10:47:11 tnm-VirtualBox ntpd[5733]: Soliciting pool server 192.168.200.71

```

---

### Post by TheFu on 2017-03-23
Go the other way.  Run NTP on Unix and let Windows sync to it. THAT is definitely supported.  Windows has "issues" maintaining time, IME.  Unix time "just works" - anything off more than 0.25s is a complete failure.

[http://blog.jdpfu.com/2010/01/16/solved-clock-time-loss-under-windows7-and-vista](http://blog.jdpfu.com/2010/01/16/solved-clock-time-loss-under-windows7-and-vista)

Virtualization inside a VM has multiple considerations.  Some hypervisors have great solutions for the problem. Others only set the HW clock at boot and expect the client OS to manage time using the normal, expected, methods, for the OS.

If Windows can support NTPd as a service, then you should be able to point any client at it.  OTOH, the +/- 5 min is close enough attitude from MSFT (read their time/domain specs) is a sure sign that their idea of time is less than good-enough for Unix systems.

---

### Post by SeijiSensei on 2017-03-23
I agree with TheFu.  Make the Linux machine the ntpd host.  Also, once you have synchronized it with remote NTP servers, use the hwclock utility to set the time on the machine's hardware clock:
```
sudo hwclock --systohc
```

---

