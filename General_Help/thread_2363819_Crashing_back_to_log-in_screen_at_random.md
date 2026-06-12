---
title: "Crashing back to log-in screen at random"
date: 2017-06-14
forum: General Help
---

### Post by SagaciousKJB on 2017-06-14
I'm really not sure what's going on, but after doing "apt-get dist-upgrade" a few days ago my system has randomly crashed back to the login-screen. I've been trying to find the instances of this in syslog, but it seems to have a lot of different causes. More often than not the line in syslog begins with "traps" talks about some kind of "general protection" and then mentions libc, but there are other instances where it seems to be something to do with X.

Anyway what happens is that my screen will simply go black and show a terminal, usually with the last line of syslog posted, and then lightDM will start up again and I can log back in.

```
kenny@AMD:~$ grep traps /var/log/syslog
Jun 14 09:36:46 AMD kernel: [243546.673836] traps: SHCLIP[9375] general protection ip:7f4df47b210d sp:7f4db54bea30 error:0 in libc-2.19.so[7f4df4776000+1be000]
kenny@AMD:~$ grep traps /var/log/syslog
Jun 14 09:36:46 AMD kernel: [243546.673836] traps: SHCLIP[9375] general protection ip:7f4df47b210d sp:7f4db54bea30 error:0 in libc-2.19.so[7f4df4776000+1be000]
kenny@AMD:~$ grep libc-2.1.9 /var/log/syslog
kenny@AMD:~$ grep libc /var/log/syslog
Jun 14 09:36:46 AMD kernel: [243546.673836] traps: SHCLIP[9375] general protection ip:7f4df47b210d sp:7f4db54bea30 error:0 in libc-2.19.so[7f4df4776000+1be000]
Jun 14 12:48:50 AMD colord: plugin /usr/lib/x86_64-linux-gnu/colord-plugins/libcd_plugin_sane.so not loaded: plugin refused to load
Jun 14 12:48:50 AMD colord: loaded plugin libcd_plugin_camera.so
Jun 14 12:48:50 AMD colord: loaded plugin libcd_plugin_scanner.so
kenny@AMD:~$ grep SCHLIP /var/log/syslog
kenny@AMD:~$ grep traps /var/log/syslog
syslog       syslog.1     syslog.2.gz  syslog.3.gz  syslog.4.gz  syslog.5.gz  syslog.6.gz  syslog.7.gz  
kenny@AMD:~$ grep traps /var/log/syslog1
grep: /var/log/syslog1: No such file or directory
kenny@AMD:~$ grep traps /var/log/syslog.1 
Display all 662 possibilities? (y or n)
kenny@AMD:~$ grep traps /var/log/syslog.1 
kenny@AMD:~$ grep traps /var/log/syslog.1
kenny@AMD:~$ zcat /var/log/syslog.2.gz | grep traps
kenny@AMD:~$ zcat /var/log/syslog.3.gz | grep traps
Jun 11 13:53:36 AMD kernel: [144655.319108] traps: VirtualBox[17564] general protection ip:7fb4ac0d310d sp:7ffe776480d0 error:0 in libc-2.19.so[7fb4ac097000+1be000]
Jun 12 00:14:00 AMD kernel: [36850.795793] traps: VirtualBox[3912] general protection ip:7f1d0a1b510d sp:7ffc7cc39820 error:0 in libc-2.19.so[7f1d0a179000+1be000]
kenny@AMD:~$ zcat /var/log/syslog.4.gz | grep traps
kenny@AMD:~$ zcat /var/log/syslog.5.gz | grep traps
kenny@AMD:~$ zcat /var/log/syslog.6.gz | grep traps
kenny@AMD:~$ zcat /var/log/syslog.6.gz | grep segfault
kenny@AMD:~$ zcat /var/log/syslog.5.gz | grep segfault
kenny@AMD:~$ zcat /var/log/syslog.4.gz | grep segfault
Jun 10 19:59:04 AMD kernel: [80142.318317] SHCLIP[27519]: segfault at a ip 00007f694a6597c2 sp 00007f692808d7b0 error 4 in libc-2.19.so[7f694a5db000+1be000]
kenny@AMD:~$ zcat /var/log/syslog.3.gz | grep segfault
Jun 11 13:53:48 AMD kernel: [144667.528387] LogForward[386]: segfault at 7fd33401cd00 ip 00007fcfa93c7b46 sp 00007fcf8103cd80 error 4 in libmythbase-0.28.so.0.28.0[7fcfa92a1000+1f8000]
Jun 11 13:55:02 AMD kernel: [144741.808255] chrome[19447]: segfault at 968 ip 00007f2578e53d0d sp 00007ffe5d000fd0 error 4 in libX11.so.6.3.0[7f2578e2c000+130000]
Jun 11 13:55:03 AMD kernel: [144742.481544] chrome[19497]: segfault at 968 ip 00007f08c034ad0d sp 00007ffdf78d3550 error 4 in libX11.so.6.3.0[7f08c0323000+130000]
Jun 11 13:58:29 AMD kernel: [144948.281471] chrome[20721]: segfault at 968 ip 00007f617a044d0d sp 00007fffd7f30ad0 error 4 in libX11.so.6.3.0[7f617a01d000+130000]

```

This is my apt log...
[https://paste.ubuntu.com/24859660/](https://paste.ubuntu.com/24859660/)

Here is my dmesg output

[https://paste.ubuntu.com/24859706/](https://paste.ubuntu.com/24859706/)

---

### Post by SagaciousKJB on 2017-06-14
Anyone?  Is this not enough information? I'd really appreciate some help.

---

### Post by QIII on 2017-06-14
Please be patient.  We are all volunteers from around the globe who spend time as we have it.

If you have not had any response in 12 hours, feel free to bump your thread.

---

### Post by SagaciousKJB on 2017-06-16
> **QIII said:**
> Please be patient.  We are all volunteers from around the globe who spend time as we have it.

If you have not had any response in 12 hours, feel free to bump your thread.

I'm still sitting here with no idea what more to do and experiencing random system crashes.  I tried to make a script to roll-back the packages I updated, but then I found an even more interesting problem because it claimed that half the packages that I upgraded from "could not be found".

At this point I'm basically going to have to fresh install just to fix this minor problem.  Sorry if I seem a little impatient, I'm just trying to stay on top of this, the more it's seen the more chances someone will help.

It might help to know for sure what to look for in syslog too.  So far I keep seeing mentions of VirtualBox and it seems like it's only happening when it's open.

```
Jun 16 13:36:54 AMD kernel: [175854.151760] traps: VirtualBox[4703] general protection ip:7fc71de6310d sp:7ffc4d371450 error:0 in libc-2.19.so[7fc71de27000+1be000]
```

I tried running dpkg-configure on it so that it would rebuild the modules it runs incase it had something to do with that, but I think it has something to do with this libc upgrade since I don't often see that package upgraded much and I know it forms the basis for pretty much everything compiled and built by source on my computer so it would make sense that it would effect multiple applications as well.

I mean, maybe I should try loading back up on the previous kernel?

---

### Post by SagaciousKJB on 2017-06-17
More segfaults...

```
Jun 17 10:54:07 AMD kernel: [76604.427138] Qt bearer threa[4115]: segfault at 7f8a069a8a50 ip 00007f8b34ee4b84 sp 00007f8a075f55e0 error 4 in l
ibQt5Network.so.5.2.1[7f8b34e50000+13c000]

```

```
Jun 17 10:54:09 AMD kernel: [76606.839037] chrome[22383]: segfault at 968 ip 00007fccf3d2ed0d sp 00007fff376f9770 error 4 in libX11.so.6.3.0[7f
ccf3d07000+130000]

```

This time no VirtualBox was open. I'm trying running on the previously installed kernel to see if that makes a difference.

---

### Post by SagaciousKJB on 2017-06-18
Still crashing. Could someone at least tell me how to revert these packages?

---

### Post by deadflowr on 2017-06-18
Which nvidia driver did you install?
I only know you have the nvidia driver because a quick look at the dmesg-pastebin output shows the tell tale "NVIDIA taints kernel" output, which only shows when you install the closed source nvidia drivers.

(No worries about the taint kernel message as that has to do with the fact that the driver is closed source and the kernel devs cannot do anything about it, sort of an armchair explanation)

---

### Post by SagaciousKJB on 2017-06-18
> **deadflowr said:**
> Which nvidia driver did you install?
I only know you have the nvidia driver because a quick look at the dmesg-pastebin output shows the tell tale "NVIDIA taints kernel" output, which only shows when you install the closed source nvidia drivers.

(No worries about the taint kernel message as that has to do with the fact that the driver is closed source and the kernel devs cannot do anything about it, sort of an armchair explanation)

Whoops sorry! I thought I added that in my first post, but it was too long and I had to re-write it.

I'm using the 173 drivers because I have a super old GeForce 7950 GT and I run two X screens for a tv-out. I've tried the 304 driver and I couldn't get the dual X screen functionality to work so I stuck to the 173. The only reason I have two X screens is because I have MythTV rigged to a remote control and it's the only way I can get it to execute on the right screen.  ...just figured you'd ask.

---

