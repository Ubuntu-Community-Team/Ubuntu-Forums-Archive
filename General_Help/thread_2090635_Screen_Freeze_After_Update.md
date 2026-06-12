---
title: "Screen Freeze After Update"
date: 2012-12-03
forum: General Help
---

### Post by colmeweb on 2012-12-03
Hey, I'm running 12.04 on a toshiba satellite and I ran an update a few days ago. Now my screen half freezes every once and a while. Everything stops, except the mouse still moves around. I can't change/move anything or shut down. I have to do a hard shutdown and restart to do anything. I let it sit last time for 30 minutes and nothing happened. Has anybody out there had the same problem or a solution? 

Thanks

---

### Post by 2F4U on 2012-12-03
Do you remember what packages were updated? Did you look into the system log files? Does the freezing happen when particular applications are running or specific actions are performed?

---

### Post by colmeweb on 2012-12-03
The only package I remember was the new kernel and the files that go with it. I haven't looked into the system log. I will check that in the morning.

---

### Post by colmeweb on 2012-12-06
Ok, so I have done some trial and error and have discovered that my screen only freezes when I am online and going from one webpage to another quickly, mostly when I am reading the news. It happens in  both firefox and chromium.

---

### Post by colmeweb on 2012-12-15
So I have just copied a system log after the freeze happened again, but I'm not sure where to start putting it up here. Can anyone give me a readout of the first few lines of the start-up so that I can post what happened before it.

---

### Post by colmeweb on 2012-12-17
So there have been some changes. First I upgraded from 12.04 to 12.10 in hopes that it would solve the problem. It didn't Next I started using an xfce desktop to see if that did anything, and it actually did. Whatever is causing this happened again, but unlike in unity where everything but the mouse freezez in xfce only the video player froze. Everything ells is still going.

This is the system log output from the last freeze before today. I bolded the section where I restarted the computer.

```
Dec 15 20:21:36 colin-Satellite kernel: [29169.171045] [UFW BLOCK] IN=wlan0 OUT= MAC=00:1b:9e:6b:56:a9:20:aa:4b:53:cd:51:08:00 SRC=160.7.234.16 DST=192.168.1.107 LEN=48 TOS=0x00 PREC=0x20 TTL=112 ID=16922 PROTO=UDP SPT=24806 DPT=51413 LEN=28 
Dec 15 20:21:36 colin-Satellite kernel: [29169.212763] [UFW BLOCK] IN=wlan0 OUT= MAC=00:1b:9e:6b:56:a9:20:aa:4b:53:cd:51:08:00 SRC=160.7.234.16 DST=192.168.1.107 LEN=48 TOS=0x00 PREC=0x20 TTL=113 ID=16923 PROTO=UDP SPT=24806 DPT=51413 LEN=28 
Dec 15 20:21:36 colin-Satellite kernel: [29169.212802] [UFW BLOCK] IN=wlan0 OUT= MAC=00:1b:9e:6b:56:a9:20:aa:4b:53:cd:51:08:00 SRC=160.7.234.16 DST=192.168.1.107 LEN=48 TOS=0x00 PREC=0x20 TTL=113 ID=16924 PROTO=UDP SPT=24806 DPT=51413 LEN=28 
Dec 15 20:21:36 colin-Satellite kernel: [29169.462332] [UFW BLOCK] IN=wlan0 OUT= MAC=00:1b:9e:6b:56:a9:20:aa:4b:53:cd:51:08:00 SRC=160.7.234.16 DST=192.168.1.107 LEN=48 TOS=0x00 PREC=0x20 TTL=113 ID=16926 PROTO=UDP SPT=24806 DPT=51413 LEN=28 
[B]Dec 15 20:21:38 colin-Satellite kernel:Dec 15 20:22:47 colin-
Satellite kernel: imklog 5.8.6, log source = /proc/kmsg started.
Dec 15 20:22:47 colin-Satellite rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="636" x-info="http://www.rsyslog.com"] start
Dec 15 20:22:47 colin-Satellite rsyslogd: rsyslogd's groupid changed to 103
Dec 15 20:22:47 colin-Satellite rsyslogd: rsyslogd's userid changed to 101
Dec 15 20:22:47 colin-Satellite rsyslogd-2039: Could not open output pipe '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]
Dec 15 20:22:47 colin-Satellite kernel: [    0.000000] Initializing cgroup subsy[/B]
```

And here is the code for what is happeneing right now. This time I bolded everything right before it started.

```
[B]Dec 17 13:10:48 colin-Satellite wpa_supplicant[1150]: wlan0: WPA: Key negotiation completed with 20:aa:4b:53:cd:53 [PTK=CCMP GTK=TKIP]
Dec 17 13:10:48 colin-Satellite wpa_supplicant[1150]: wlan0: CTRL-EVENT-CONNECTED - Connection to 20:aa:4b:53:cd:53 completed (reauth) [id=0 id_str=]
Dec 17 13:10:48 colin-Satellite NetworkManager[885]: <info> (wlan0): supplicant interface state: 4-way handshake -> completed[/B]
Dec 17 13:10:52 colin-Satellite kernel: [ 3464.129582] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:fb:20:c9:d0:c6:82:3b:08:00 SRC=192.168.1.118 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=27805 PROTO=2 
Dec 17 13:11:01 colin-Satellite kernel: [ 3473.099448] [UFW BLOCK] IN=wlan0 OUT= MAC=00:1b:9e:6b:56:a9:20:aa:4b:53:cd:51:08:00 SRC=41.133.14.120 DST=192.168.1.107 LEN=58 TOS=0x00 PREC=0x20 TTL=41 ID=30509 PROTO=UDP SPT=51413 DPT=51413 LEN=38 
Dec 17 13:11:07 colin-Satellite kernel: [ 3478.682681] [UFW BLOCK] IN=wlan0 OUT= MAC=00:1b:9e:6b:56:a9:20:aa:4b:53:cd:51:08:00 SRC=70.49.180.241 DST=192.168.1.107 LEN=40 TOS=0x00 PREC=0x20 TTL=52 ID=0 DF PROTO=TCP SPT=51413 DPT=51860 WINDOW=0 RES=0x00 ACK RST URGP=0 
Dec 17 13:11:12 colin-Satellite kernel: [ 3483.794584] CE: hpet increased min_delta_ns to 20113 nsec
Dec 17 13:11:16 colin-Satellite kernel: [ 3487.708792] [UFW BLOCK] IN=wlan0 OUT= MAC=00:1b:9e:6b:56:a9:20:aa:4b:53:cd:51:08:00 SRC=85.75.126.205 DST=192.168.1.107 LEN=48 TOS=0x00 PREC=0x20 TTL=112 ID=412 PROTO=UDP SPT=42355 DPT=51413 LEN=28 
Dec 17 13:11:22 colin-Satellite kernel: [ 3494.538579] [UFW BLOCK] IN=wlan0 OUT= MAC=00:1b:9e:6b:56:a9:20:aa:4b:53:cd:51:08:00 SRC=101.163.13.201 DST=192.168.1.107 LEN=40 TOS=0x00 PREC=0x20 TTL=46 ID=0 DF PROTO=TCP SPT=51413 DPT=54326 WINDOW=0 RES=0x00 RST URGP=0 
Dec 17 13:11:35 colin-Satellite kernel: [ 3506.902021] [UFW BLOCK] IN=wlan0 OUT= MAC=00:1b:9e:6b:56:a9:20:aa:4b:53:cd:51:08:00 SRC=67.243.2.65 DST=192.168.1.107 LEN=58 TOS=0x00 PREC=0x20 TTL=113 ID=17468 PROTO=UDP SPT=23446 DPT=51413 LEN=38 
Dec 17 13:12:00 colin-Satellite kernel: [ 3531.751267] [UFW BLOCK] IN=wlan0 OUT= MAC=00:1b:9e:6b:56:a9:20:aa:4b:53:cd:51:08:00 SRC=82.3.44.98 DST=192.168.1.107 LEN=48 TOS=0x00 PREC=0x20 TTL=46 ID=13903 PROTO=UDP SPT=51413 DPT=51413 LEN=28 
Dec 17 13:12:01 colin-Satellite kernel: [ 3532.950324] [UFW BLOCK] IN=wlan0 OUT= MAC=00:1b:9e:6b:56:a9:20:aa:4b:53:cd:51:08:00 SRC=72.21.91.111 DST=192.168.1.107 LEN=40 TOS=0x00 PREC=0x20 TTL=57 ID=14861 DF PROTO=TCP SPT=80 DPT=41515 WINDOW=229 RES=0x00 ACK FIN URGP=0 
Dec 17 13:12:02 colin-Satellite kernel: [ 3534.094015] [UFW BLOCK] IN=wlan0 OUT= MAC=00:1b:9e:6b:56:a9:20:aa:4b:53:cd:51:08:00 SRC=190.244.122.190 DST=192.168.1.107 LEN=40 TOS=0x00 PREC=0x20 TTL=111 ID=15367 PROTO=TCP SPT=18400 DPT=53264 WINDOW=0 RES=0x00 ACK RST URGP=0 
Dec 17 13:12:16 colin-Satellite kernel: [ 3547.731777] [UFW BLOCK] IN=wlan0 OUT= MAC=00:1b:9e:6b:56:a9:20:aa:4b:53:cd:51:08:00 SRC=145.118.100.130 DST=192.168.1.107 LEN=58 TOS=0x00 PREC=0x20 TTL=112 ID=4500 PROTO=UDP SPT=15394 DPT=51413 LEN=38 
Dec 17 13:12:26 colin-Satellite kernel: [ 3558.403661] [UFW BLOCK] IN=wlan0 OUT= MAC=00:1b:9e:6b:56:a9:20:aa:4b:53:cd:51:08:00 SRC=75.70.137.0 DST=192.168.1.107 LEN=40 TOS=0x00 PREC=0x20 TTL=55 ID=9880 DF PROTO=TCP SPT=51413 DPT=59674 WINDOW=0 RES=0x00 RST URGP=0 
Dec 17 13:12:45 colin-Satellite kernel: [ 3577.511872] [UFW BLOCK] IN=wlan0 OUT= MAC=00:1b:9e:6b:56:a9:20:aa:4b:53:cd:51:08:00 SRC=81.174.173.175 DST=192.168.1.107 LEN=40 TOS=0x00 PREC=0x20 TTL=45 ID=1783 DF PROTO=TCP SPT=51413 DPT=41290 WINDOW=0 RES=0x00 ACK RST URGP=0
```


As best I can tell whatever [UFW BLOCK] is it is either causing this problem, or whatever is being blocked is causing it.

Again, any help is appreciated. 
Thanks

---

