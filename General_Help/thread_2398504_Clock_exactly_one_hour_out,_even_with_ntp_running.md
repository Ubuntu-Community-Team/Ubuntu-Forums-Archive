---
title: "Clock exactly one hour out, even with ntp running"
date: 2018-08-13
forum: General Help
---

### Post by SB9784 on 2018-08-13
Runing Ubuntu 18.04, I can see that my clock is out by one hour (it states both UTC and my local timezone as being one hour ahead). I can see that the NTP daemon is running fine and I've checked my BIOS and the clock is correct there. Here are some outputs to demonstrate what's going on:

```
$ timedatectl
                       Local time: Mon 2018-08-13 12:52:26 BST
                  Universal time: Mon 2018-08-13 11:52:26 UTC
                         RTC time: Mon 2018-08-13 11:52:26
                        Time zone: Europe/London (BST, +0100)
       System clock synchronized: yes
systemd-timesyncd.service active: yes
                 RTC in local TZ: no

```

(the time is actually 11:52 BST / 10:52 UTC).

```
$ sudo systemctl status ntp -l
&#9679; ntp.service - Network Time Service
   Loaded: loaded (/lib/systemd/system/ntp.service; enabled; vendor preset: enabled)
   Active: active (running) since Mon 2018-08-13 12:47:51 BST; 6min ago
     Docs: man:ntpd(8)
 Main PID: 4510 (ntpd)
    Tasks: 2 (limit: 4915)
   CGroup: /system.slice/ntp.service
           &#9492;&#9472;4510 /usr/sbin/ntpd -p /var/run/ntpd.pid -g -u 124:130


Aug 13 12:52:35 fruitmachine ntpd[4510]: Soliciting pool server 85.199.214.99
Aug 13 12:53:18 fruitmachine ntpd[4510]: Soliciting pool server 176.58.109.199
Aug 13 12:53:18 fruitmachine ntpd[4510]: Soliciting pool server 178.79.162.34
Aug 13 12:53:22 fruitmachine ntpd[4510]: Soliciting pool server 130.159.196.118
Aug 13 12:53:23 fruitmachine ntpd[4510]: Soliciting pool server 2a03:b980:123:2::a
Aug 13 12:53:25 fruitmachine ntpd[4510]: Soliciting pool server 2001:67c:1560:8003::c7
Aug 13 12:54:24 fruitmachine ntpd[4510]: Soliciting pool server 129.250.35.251
Aug 13 12:54:25 fruitmachine ntpd[4510]: Soliciting pool server 109.74.206.120
Aug 13 12:54:28 fruitmachine ntpd[4510]: Soliciting pool server 2a02:ac00:2:1::5
Aug 13 12:54:28 fruitmachine ntpd[4510]: Soliciting pool server 134.0.16.1

```

If I stop the NTP daemon, and then run ntpdate manually, I get the following error:

```
$ sudo ntpdate pool.ntp.org
13 Aug 12:55:26 ntpdate[10017]: no server suitable for synchronization found
$ sudo ntpdate ntp.ubuntu.com
13 Aug 12:57:10 ntpdate[10157]: no server suitable for synchronization found

```

This is a dual-boot machine, and interestingly I noticed the same problem when I booted into Windows the other day for the first time in a while.

---

### Post by Impavidus on 2018-08-13
When you write that the time is correct in BIOS, do you mean correct in local time or UTC?

It appears your UTC clock displays local time, making it 1 hour ahead, and local time changed as expected. That's a common problem when dual booting Linux and Windows. The problem is that Linux assumes the RTC time is set to UTC, but Windows assumes the RTC time is set to local time. It works best if all are set to UTC, but all on local works most of the time well enough. See this thread: [https://ubuntuforums.org/showthread.php?t=2321876](https://ubuntuforums.org/showthread.php?t=2321876)

---

### Post by SB9784 on 2018-08-14
Yep, this fixed it. I followed the instructions in the answer at [https://superuser.com/questions/975717/does-windows-10-support-utc-as-bios-time](https://superuser.com/questions/975717/does-windows-10-support-utc-as-bios-time) to change Windows 10 to use RTC as UTC and now the Linux clock is fine (although I've had to disable internet updates in Windows, but I can live with that).

---

