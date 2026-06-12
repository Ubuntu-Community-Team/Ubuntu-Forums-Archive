---
title: "Random Reboots with Ubuntu 14.04 while memtest86+ runs for days"
date: 2015-12-28
forum: General Help
---

### Post by ladiko on 2015-12-28
We have almost 200 machines which all runs the same system except for minor differences in package versions (like linux-image-3.13.0-70-generic or linux-image-3.13.0-74-generic). One machine reboots randomly within 30 minutes. I tried to start the kernel with loglevel=7 but neither kern.log nor syslog shows anything interesting. When i select memtest86+ from grub, the machine runs for days without issues.

```
user@machine:~$ last | grep -Pom1 "\S+ \S+ +\d+ \d+:\d+(?= - crash)"
Mon Dec 28 14:26
user@machine:~$ sudo grep -P "Dec 28 +14:26:" /var/log/kern.log > kern.log
user@machine:~$ sudo grep -P "Dec 28 +14:26:" /var/log/syslog > syslog
```


kern.log: [http://pastebin.com/wFSvVtf2](http://pastebin.com/wFSvVtf2)
syslog: [http://pastebin.com/6uDLfnDw](http://pastebin.com/6uDLfnDw)

Any idea on how to further enhance debugging / logging?

---

### Post by ian-weisser on 2015-12-28
Please describe the reboot.
Is it like a complete power cycle, including POST, manufacturer logo, GRUB, Ubuntu Splash, and Login Screen?
Or is it a shorter version, *only* the Login Screen?

The logs you posted seem like the former. Did the reboot really happen at 14:26?
Do you have logs from *before* the reboot? Syslog should include pre-restart logs.

The description so far smells like hardware to me.

---

### Post by ladiko on 2015-12-29
It's a full power cycle with POST, Grub etc. Last evening i bootet the ubuntu 14.04.3 Desktop ISO and when i came back this morning, it also restarted to the normal system. I restartet to the ISO ~ 16:30, so it seems like the last shutdown of the normal system was "[COLOR=#000000][FONT=Ubuntu Mono]Mon Dec 28 16:24:55 2015 - down". Within 30 Minutes it restarted. The machine is a kiosk system with a web application (electron browser based on chromium) running in full screen. It seems like if i kill the application, the machine doesnt reboot. Therefor could it be related to the graphics card?

[/FONT][/COLOR]I also think it's the hardware, but what is memtest86+ based on? It never rebooted within days while Ubuntu restarts within an hour.

```
user@machine:~$ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.13.0-74-generic root=/dev/sda1 ro quiet splash vt.handoff=7 loglevel=7

user@machine:~$ last -F -n 50
user     pts/10       192.168.1.167    Tue Dec 29 10:09:03 2015   still logged in
user     pts/0        :0.0             Tue Dec 29 10:07:38 2015   still logged in
user     tty1                          Tue Dec 29 09:59:41 2015   still logged in
reboot   system boot  3.13.0-74-generi Tue Dec 29 09:59:37 2015 - Tue Dec 29 10:28:16 2015  (00:28)
user     tty1                          Mon Dec 28 17:08:34 2015 - down                      (16:35)
reboot   system boot  3.13.0-74-generi Mon Dec 28 17:08:30 2015 - Tue Dec 29 09:44:28 2015  (16:35)
user     tty1                          Mon Dec 28 17:07:18 2015 - crash                     (00:01)
reboot   system boot  3.13.0-74-generi Mon Dec 28 17:07:13 2015 - Tue Dec 29 09:44:28 2015  (16:37)
user     pts/3        192.168.1.167    Mon Dec 28 16:24:55 2015 - down                      (00:22)
user     pts/3        192.168.1.167    Mon Dec 28 16:24:04 2015 - Mon Dec 28 16:24:52 2015  (00:00)
user     pts/3        192.168.1.167    Mon Dec 28 16:15:16 2015 - Mon Dec 28 16:24:01 2015  (00:08)
user     pts/3        192.168.1.167    Mon Dec 28 15:51:55 2015 - Mon Dec 28 16:15:13 2015  (00:23)
user     pts/3        192.168.1.167    Mon Dec 28 15:51:19 2015 - Mon Dec 28 15:51:49 2015  (00:00)
user     pts/3        192.168.1.167    Mon Dec 28 15:46:14 2015 - Mon Dec 28 15:51:14 2015  (00:05)
user     tty2                          Mon Dec 28 15:37:09 2015 - down                      (01:10)
user     tty1                          Mon Dec 28 14:29:16 2015 - down                      (02:18)
reboot   system boot  3.13.0-74-generi Mon Dec 28 14:29:11 2015 - Mon Dec 28 16:47:45 2015  (02:18)
user     pts/10       192.168.1.167    Mon Dec 28 14:26:53 2015 - crash                     (00:02)
user     tty1                          Mon Dec 28 14:26:21 2015 - crash                     (00:02)
reboot   system boot  3.13.0-74-generi Mon Dec 28 14:26:17 2015 - Mon Dec 28 16:47:45 2015  (02:21)
user     tty1                          Mon Dec 28 14:18:55 2015 - crash                     (00:07)
reboot   system boot  3.13.0-74-generi Mon Dec 28 14:18:51 2015 - Mon Dec 28 16:47:45 2015  (02:28)
user     pts/10       :0.0             Mon Dec 28 14:16:29 2015 - down                      (00:01)
user     tty1                          Mon Dec 28 14:15:44 2015 - down                      (00:02)
reboot   system boot  3.13.0-74-generi Mon Dec 28 14:15:40 2015 - Mon Dec 28 14:18:21 2015  (00:02)
user     pts/1        :0.0             Mon Dec 28 14:14:39 2015 - crash                     (00:01)
user     tty1                          Mon Dec 28 14:14:28 2015 - crash                     (00:01)
reboot   system boot  3.13.0-74-generi Mon Dec 28 14:14:24 2015 - Mon Dec 28 14:18:21 2015  (00:03)
user     tty3                          Mon Dec 28 14:09:17 2015 - crash                     (00:05)
user     tty1                          Mon Dec 28 14:07:38 2015 - crash                     (00:06)
reboot   system boot  3.13.0-74-generi Mon Dec 28 14:07:34 2015 - Mon Dec 28 14:18:21 2015  (00:10)
user     pts/10       192.168.1.167    Mon Dec 28 14:00:33 2015 - crash                     (00:07)
user     tty1                          Mon Dec 28 14:00:03 2015 - crash                     (00:07)
reboot   system boot  3.13.0-74-generi Mon Dec 28 14:00:00 2015 - Mon Dec 28 14:18:21 2015  (00:18)
user     pts/0        :0.0             Mon Dec 28 13:58:25 2015 - crash                     (00:01)
user     pts/10       pc192-168-1-167  Mon Dec 28 13:50:32 2015 - crash                     (00:09)
user     tty1                          Mon Dec 28 13:50:19 2015 - crash                     (00:09)
reboot   system boot  3.13.0-74-generi Mon Dec 28 13:50:15 2015 - Mon Dec 28 14:18:21 2015  (00:28)
user     pts/0        192.168.1.167    Mon Dec 28 13:42:20 2015 - down                      (00:07)
user     tty1                          Mon Dec 28 13:42:17 2015 - down                      (00:07)
reboot   system boot  3.13.0-74-generi Mon Dec 28 13:42:13 2015 - Mon Dec 28 13:49:45 2015  (00:07)
user     pts/0        192.168.1.167    Mon Dec 28 13:40:20 2015 - crash                     (00:01)
user     tty1                          Mon Dec 28 13:40:17 2015 - crash                     (00:01)
reboot   system boot  3.13.0-74-generi Mon Dec 28 13:40:13 2015 - Mon Dec 28 13:49:45 2015  (00:09)
user     pts/0        192.168.1.167    Mon Dec 28 13:39:12 2015 - down                      (00:00)
user     tty1                          Mon Dec 28 13:36:46 2015 - down                      (00:02)
reboot   system boot  3.13.0-74-generi Mon Dec 28 13:36:42 2015 - Mon Dec 28 13:39:43 2015  (00:03)
user     pts/3        :0.0             Mon Dec 28 13:34:55 2015 - down                      (00:01)
user     tty1                          Mon Dec 28 13:34:47 2015 - down                      (00:01)
reboot   system boot  3.13.0-74-generi Mon Dec 28 13:34:43 2015 - Mon Dec 28 13:36:12 2015  (00:01)


wtmp begins Sun Dec  1 10:30:26 2013
```

I updated  the syslog and kern.log to the full files starting with the first entry of Dec 28.

---

