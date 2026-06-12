---
title: "Time sync Question"
date: 2018-06-05
forum: General Help
---

### Post by echotech2 on 2018-06-05
Ubuntu 16.04

```
 systemctl status systemd-timesyncd.service
&#9679; systemd-timesyncd.service - Network Time Synchronization
   Loaded: loaded (/lib/systemd/system/systemd-timesyncd.service; enabled; vendor preset: enabled
  Drop-In: /lib/systemd/system/systemd-timesyncd.service.d
           &#9492;&#9472;disable-with-time-daemon.conf
   Active: inactive (dead)
Condition: start condition failed at Tue 2018-06-05 10:38:12 EDT; 36min ago
           ConditionFileIsExecutable=!/usr/sbin/ntpd was not met
```

  Time & Date is set to "Automatically from the internet"

  Is Something wrong here?  e.g.: Active: Inactive (dead) and Condition: Start condition failed.

---

### Post by nlee2 on 2018-06-05
ConditionFileIsExecutable=!/usr/sbin/ntpd was not met

What is the output of 
ls -la /usr/sbin/ntpd
which ntpd

---

### Post by echotech2 on 2018-06-05
As requested:

```
 ls -la /usr/sbin/ntpd
-rwxr-xr-x 1 root root 734480 Feb 14 09:56 /usr/sbin/ntpd

```

```
which ntpd
/usr/sbin/ntpd

```

---

### Post by nlee2 on 2018-06-05
What is the output of

systemctl status ntpd

If ntpd service is enabled and active and you would like to run systemd-timesyncd, you should remove ntpd.

---

### Post by echotech2 on 2018-06-05
```
systemctl status ntpd
&#9679; ntpd.service
   Loaded: not-found (Reason: No such file or directory)
   Active: inactive (dead)

```

  I'm not quite sure what you mean?

---

### Post by nlee2 on 2018-06-05
Sorry. Should read

systemctl status ntp

To remove

apt remove ntp
systemctl start systemd-timesyncd.service
systemctl status systemd-timesyncd.service

---

### Post by echotech2 on 2018-06-05
```
&#9679; systemd-timesyncd.service - Network Time Synchronization
   Loaded: loaded (/lib/systemd/system/systemd-timesyncd.service; enabled; vendor preset: enabled)
  Drop-In: /lib/systemd/system/systemd-timesyncd.service.d
           &#9492;&#9472;disable-with-time-daemon.conf
   Active: active (running) since Tue 2018-06-05 14:09:34 EDT; 24s ago
     Docs: man:systemd-timesyncd.service(8)
 Main PID: 20375 (systemd-timesyn)
   Status: "Synchronized to time server 91.189.89.198:123 (ntp.ubuntu.com)."
   CGroup: /system.slice/systemd-timesyncd.service
           &#9492;&#9472;20375 /lib/systemd/systemd-timesyncd

Jun 05 14:09:34 scamper systemd[1]: Starting Network Time Synchronization...
Jun 05 14:09:34 scamper systemd[1]: Started Network Time Synchronization.
Jun 05 14:09:34 scamper systemd-timesyncd[20375]: Synchronized to time server 91.189.89.198:123 (ntp.ubuntu.com).

```

  Thanks. Followed your directions and all is working.

---

