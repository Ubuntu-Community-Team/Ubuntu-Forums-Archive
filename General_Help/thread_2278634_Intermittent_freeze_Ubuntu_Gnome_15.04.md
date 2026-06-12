---
title: "Intermittent freeze Ubuntu Gnome 15.04"
date: 2015-05-18
forum: General Help
---

### Post by welwyn2006 on 2015-05-18
I have a dual boot system, Win 7 and Ubuntu Gnome 15.04. Ubuntu intermittently freezes where the only resolve is the power button. I have tried all the suggested special key stokes to no avail only the power button resolves the problem, sometimes the mouse is there and able to move other times not but the mouse buttons never work. Sometimes it will not wake up from sleep, the problem seems totally random
Things I have tried
1. Fresh install of Ubuntu, I have a 64bit system but I have tried fresh install of both 32 and 64 bit.
2 Using nouveau driver or propriety tested nvidia driver.
3. Running solely Win 7 for a week doing the same work I would normally do on Ubuntu, no problems at all.
4. Installed  Ubuntu on a different part on the hard drive.
5. Installed Ubuntu on an external bootable hard drive.

My system is an Asus ET2410 23.6 All in One i5 2,5 Ghz with 6GB RAM.

I have been so pleased with Ubuntu over many years please do not let this end our relationship,

John

---

### Post by Gregg_Coleshill on 2015-10-10
John,

Did you find a solution? I have started having the same (or similar) problem the last couple of days. My system is not dual boot, just straight Ubuntu-gnome 15.04 and has been entirely stable for a long time, no recent changes. It just suddenly freezes intermittently and I get no response from mouse or keyboard at all only way to free it up is to hard power off and on again.

Machine is a Clevo W150HRM I7 2.00GHz with 8gb ram so I'm pretty sure it's not running out of resources!!

---

### Post by P-I H on 2015-10-18
I had the same problem on Ubuntu Wily with Unity. It is possible to move the cursor but nothing is clickable and the keyboard doesn't work.
However in my case the proprietary driver 352.41 from Nvidia works OK. My graphic card is GTX 660.
I get these faults in syslog
```
Oct 15 10:34:30 pi-GA-MA770-UD3-test kernel: [  757.934288] nouveau E[   PFIFO][0000:01:00.0] SCHED_ERROR [ CTXSW_TIMEOUT ]
Oct 15 10:34:30 pi-GA-MA770-UD3-test kernel: [  757.934296] nouveau E[   PFIFO][0000:01:00.0] PGRAPH engine fault on channel 5, recovering...

```
when you search for "pfifo pgraph" you will find this bug report
[https://bugs.freedesktop.org/show_bug.cgi?id=90453](https://bugs.freedesktop.org/show_bug.cgi?id=90453)

---

