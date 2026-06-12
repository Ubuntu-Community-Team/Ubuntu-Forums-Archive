---
title: "Xinetd doesn't start on 20.04"
date: 2020-12-29
forum: General Help
---

### Post by Keith_Helms on 2020-12-29
I just built a Xubuntu 20.04 boot partition and tried to get xinetd and  cvspserver running like on my previous 18.04 install.   As far as I can  tell xinetd just isn't starting and I can't find any instructions  telling me to do something different for 20.04.

Under 18.04 the syslog shows the following:

```
Dec 29 15:17:56 sager-oled systemd[1]: Starting LSB: Starts or stops the xinetd daemon....
Dec 29 15:17:56 sager-oled xinetd[1282]:  * Starting internet superserver xinetd
Dec 29 15:17:56 sager-oled xinetd[1282]:    ...done.
Dec 29 15:17:56 sager-oled systemd[1]: Started LSB: Starts or stops the xinetd daemon..
Dec  29 15:17:56 sager-oled xinetd[1326]: Reading included configuration  file: /etc/xinetd.d/chargen [file=/etc/xinetd.conf] [line=14]
Dec 29  15:17:56 sager-oled xinetd[1326]: Reading included configuration file:  /etc/xinetd.d/chargen-udp [file=/etc/xinetd.d/chargen-udp] [line=28]
Dec  29 15:17:56 sager-oled xinetd[1326]: Reading included configuration  file: /etc/xinetd.d/cvspserver [file=/etc/xinetd.d/cvspserver] [line=14]
Dec  29 15:17:56 sager-oled xinetd[1326]: Reading included configuration  file: /etc/xinetd.d/daytime [file=/etc/xinetd.d/daytime] [line=12]
Dec  29 15:17:56 sager-oled xinetd[1326]: Reading included configuration  file: /etc/xinetd.d/daytime-udp [file=/etc/xinetd.d/daytime-udp]  [line=26]
Dec 29 15:17:56 sager-oled xinetd[1326]: Reading included  configuration file: /etc/xinetd.d/discard [file=/etc/xinetd.d/discard]  [line=14]
Dec 29 15:17:56 sager-oled xinetd[1326]: Reading included  configuration file: /etc/xinetd.d/discard-udp  [file=/etc/xinetd.d/discard-udp] [line=25]
Dec 29 15:17:56 sager-oled  xinetd[1326]: Reading included configuration file: /etc/xinetd.d/echo  [file=/etc/xinetd.d/echo] [line=14]
Dec 29 15:17:56 sager-oled  xinetd[1326]: Reading included configuration file:  /etc/xinetd.d/echo-udp [file=/etc/xinetd.d/echo-udp] [line=26]
Dec 29  15:17:56 sager-oled xinetd[1326]: Reading included configuration file:  /etc/xinetd.d/servers [file=/etc/xinetd.d/servers] [line=14]
Dec 29  15:17:56 sager-oled xinetd[1326]: Reading included configuration file:  /etc/xinetd.d/services [file=/etc/xinetd.d/services] [line=13]
Dec 29  15:17:56 sager-oled xinetd[1326]: Reading included configuration file:  /etc/xinetd.d/time [file=/etc/xinetd.d/time] [line=13]
Dec 29  15:17:56 sager-oled xinetd[1326]: Reading included configuration file:  /etc/xinetd.d/time-udp [file=/etc/xinetd.d/time-udp] [line=28]
Dec 29 15:17:56 sager-oled xinetd[1326]: 2.3.15.3 started with libwrap loadavg labeled-networking options compiled in.
Dec 29 15:17:56 sager-oled xinetd[1326]: Started working: 1 available service
```

Under 20.04 the syslog shows the following:

```
Dec 29 15:23:33 sager-oled systemd[1]: Starting LSB: Starts or stops the xinetd daemon....
Dec 29 15:23:33 sager-oled xinetd[1433]:  * Starting internet superserver xinetd
Dec 29 15:23:33 sager-oled xinetd[1472]: Warning: Fake start-stop-daemon called, doing nothing.
Dec 29 15:23:33 sager-oled xinetd[1433]:    ...done.
Dec 29 15:23:33 sager-oled systemd[1]: Started LSB: Starts or stops the xinetd daemon..
```

Under both releases, I added an identical file for cvs into /etc/xinetd.d called cvspserver

```
service cvspserver
{
  port = 2401
  socket_type = stream
  protocol = tcp
  user = root
  wait = no
  type = UNLISTED
  server = /usr/bin/cvs
  server_args = -f --allow-root /homedata/homedirs/cvsroot pserver
  disable = no
}
```

CVS works from the command line on 20.04 and I can checkout a project, but there is no pserver I can access from Eclipse because xinetd isn't running.  Yeah, I know there are many newer versioning tools, but I'm just using cvs to track changes for my personal use only and have been doing so on every LTS release for a dozen years.

How do I get xinetd running on 20.04?

---

### Post by Keith_Helms on 2021-01-03
ping

---

### Post by SeijiSensei on 2021-01-04
I haven't used xinetd much in quite some time, and I've never used cvspserver. That said, I installed a new copy of xinetd on my 20.04 system.  If I run "sudo systemctl status xinetd" I get this:
```

$ sudo systemctl status xinetd
&#9679; xinetd.service - LSB: Starts or stops the xinetd daemon.
     Loaded: loaded (/etc/init.d/xinetd; generated)
     Active: active (running) since Mon 2021-01-04 13:31:11 EST; 8s ago
       Docs: man:systemd-sysv-generator(8)
    Process: 168970 ExecStart=/etc/init.d/xinetd start (code=exited, status=0/SUCCESS)
      Tasks: 1 (limit: 19020)
     Memory: 1.2M
     CGroup: /system.slice/xinetd.service
             &#9492;&#9472;168982 /usr/sbin/xinetd -pidfile /run/xinetd.pid -stayalive -inetd_compat -inetd_ipv6

Jan 04 13:31:11 big-linux xinetd[168982]: Reading included configuration file: /etc/xinetd.d/discard [file=/etc/xinetd.d/discar>
Jan 04 13:31:11 big-linux xinetd[168982]: Reading included configuration file: /etc/xinetd.d/discard-udp [file=/etc/xinetd.d/di>
Jan 04 13:31:11 big-linux xinetd[168982]: Reading included configuration file: /etc/xinetd.d/echo [file=/etc/xinetd.d/echo] [li>
Jan 04 13:31:11 big-linux xinetd[168982]: Reading included configuration file: /etc/xinetd.d/echo-udp [file=/etc/xinetd.d/echo->
Jan 04 13:31:11 big-linux xinetd[168982]: Reading included configuration file: /etc/xinetd.d/servers [file=/etc/xinetd.d/server>
Jan 04 13:31:11 big-linux xinetd[168982]: Reading included configuration file: /etc/xinetd.d/services [file=/etc/xinetd.d/servi>
Jan 04 13:31:11 big-linux xinetd[168982]: Reading included configuration file: /etc/xinetd.d/time [file=/etc/xinetd.d/time] [li>
Jan 04 13:31:11 big-linux xinetd[168982]: Reading included configuration file: /etc/xinetd.d/time-udp [file=/etc/xinetd.d/time->
Jan 04 13:31:11 big-linux xinetd[168982]: 2.3.15.3 started with libwrap loadavg labeled-networking options compiled in.
Jan 04 13:31:11 big-linux xinetd[168982]: Started working: 0 available services

```
All the services in /etc/xinetd.d/ are marked "disabled" to begin with so I have no services running under xinetd.  What do you see when you run the same status command?

xinetd entries in /var/log/syslog pretty much follow what I see with "systemctl status."

---

### Post by Keith_Helms on 2021-01-04
Interesting.  I get this.  The key difference I see is that your system shows "running" while mine shows "exited" and there's that "Warning: Fake start-stop-daemon called, doing nothing." message again.

```
$ sudo systemctl status xinetd
[sudo] password for keith: 
&#9679; xinetd.service - LSB: Starts or stops the xinetd daemon.
     Loaded: loaded (/etc/init.d/xinetd; generated)
     Active: active (exited) since Mon 2021-01-04 13:32:15 MST; 51min ago
       Docs: man:systemd-sysv-generator(8)
    Process: 1435 ExecStart=/etc/init.d/xinetd start (code=exited, status=0/SUCCESS)

Jan 04 13:32:15 sager-oled systemd[1]: Starting LSB: Starts or stops the xinetd daemon....
Jan 04 13:32:15 sager-oled xinetd[1435]:  * Starting internet superserver xinetd
Jan 04 13:32:15 sager-oled xinetd[1473]: Warning: Fake start-stop-daemon called, doing nothing.
Jan 04 13:32:15 sager-oled xinetd[1435]:    ...done.
Jan 04 13:32:15 sager-oled systemd[1]: Started LSB: Starts or stops the xinetd daemon..
```

---

### Post by Keith_Helms on 2021-01-04
Aha.   I searched on "Fake start-stop-daemon called" and found this post

[https://leavingwithnothing.blogspot.com/2017/08/warning-fake-start-stop-daemon-called.html](https://leavingwithnothing.blogspot.com/2017/08/warning-fake-start-stop-daemon-called.html)

I executed the command in the post, rebooted and now xinetd is running along with the cvspserver service under it.  I can now access the cvs repository from Eclipse.

```
sudo mv /sbin/start-stop-daemon.REAL /sbin/start-stop-daemon
```

Current output from sudo systemctl status xinetd:

```
$ sudo systemctl status xinetd
[sudo] password for keith: 
&#9679; xinetd.service - LSB: Starts or stops the xinetd daemon.
     Loaded: loaded (/etc/init.d/xinetd; generated)
     Active: active (running) since Mon 2021-01-04 14:50:12 MST; 1min 5s ago
       Docs: man:systemd-sysv-generator(8)
    Process: 1439 ExecStart=/etc/init.d/xinetd start (code=exited, status=0/SUCCESS)
      Tasks: 1 (limit: 18807)
     Memory: 3.2M
     CGroup: /system.slice/xinetd.service
             &#9492;&#9472;1625 /usr/sbin/xinetd -pidfile /run/xinetd.pid -stayalive -inetd_compat -inetd_ipv6

Jan 04 14:50:12 sager-oled xinetd[1625]: Reading included configuration file: /etc/xinetd.d/discard [file=/etc/xinetd.d/discard] [line=14]
Jan 04 14:50:12 sager-oled xinetd[1625]: Reading included configuration file: /etc/xinetd.d/discard-udp [file=/etc/xinetd.d/discard-udp] [line=25]
Jan 04 14:50:12 sager-oled xinetd[1625]: Reading included configuration file: /etc/xinetd.d/echo [file=/etc/xinetd.d/echo] [line=14]
Jan 04 14:50:12 sager-oled xinetd[1625]: Reading included configuration file: /etc/xinetd.d/echo-udp [file=/etc/xinetd.d/echo-udp] [line=26]
Jan 04 14:50:12 sager-oled xinetd[1625]: Reading included configuration file: /etc/xinetd.d/servers [file=/etc/xinetd.d/servers] [line=14]
Jan 04 14:50:12 sager-oled xinetd[1625]: Reading included configuration file: /etc/xinetd.d/services [file=/etc/xinetd.d/services] [line=13]
Jan 04 14:50:12 sager-oled xinetd[1625]: Reading included configuration file: /etc/xinetd.d/time [file=/etc/xinetd.d/time] [line=13]
Jan 04 14:50:12 sager-oled xinetd[1625]: Reading included configuration file: /etc/xinetd.d/time-udp [file=/etc/xinetd.d/time-udp] [line=28]
Jan 04 14:50:12 sager-oled xinetd[1625]: 2.3.15.3 started with libwrap loadavg labeled-networking options compiled in.
Jan 04 14:50:12 sager-oled xinetd[1625]: Started working: 1 available service

```

Problem solved!

---

