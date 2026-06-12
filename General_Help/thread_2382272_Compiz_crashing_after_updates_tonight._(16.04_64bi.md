---
title: "Compiz crashing after updates tonight. (16.04 64bit)"
date: 2018-01-11
forum: General Help
---

### Post by jimnms on 2018-01-11
I installed updates tonight (looked like just the 4.13 Kernel).  After rebooting, I noticed it took a lot longer than usual to get to the desktop after logging in, and then as soon as I tried to click an icon on the left side, a message box popped up informing me that compiz crashed and asked me to report it and send logs.  I chose to send the log, but I don't know if it got sent because compiz kept crashing over and over.

After a clean boot or after it recovers from crashing, I can click anything at the top right system tray area without a crash, but as soon as the mouse moves over any icon on the left side of the screen it crashes immediately.  I tried booting to the previous 4.10 kernel, but it still crashes.

This is what installed according the apt history log:
```
Start-Date: 2018-01-10  21:20:27
Commandline: aptdaemon role='role-commit-packages' sender=':1.386'
Install: linux-image-4.13.0-26-generic:amd64 (4.13.0-26.29~16.04.2, automatic), linux-headers-4.13.0-26:amd64 (4.13.0-26.29~16.04.2, automatic), linux-image-extra-4.13.0-26-generic:amd64 (4.13.0-26.29~16.04.2, automatic), linux-headers-4.13.0-26-generic:amd64 (4.13.0-26.29~16.04.2, automatic)
Upgrade: linux-libc-dev:amd64 (4.4.0-108.131, 4.4.0-109.132), linux-image-generic-hwe-16.04:amd64 (4.10.0.42.44, 4.13.0.26.46), linux-generic-hwe-16.04:amd64 (4.10.0.42.44, 4.13.0.26.46), linux-headers-generic-hwe-16.04:amd64 (4.10.0.42.44, 4.13.0.26.46)
End-Date: 2018-01-10  21:21:58
```

These are the errors showing up in syslog:
```
Jan 10 21:27:17 ubook kernel: [  242.324861] compiz[1855]: segfault at 0 ip 00007f580cd70986 sp 00007ffc54860540 error 4 in i965_dri.so[7f580c798000+82d000]
Jan 10 21:28:24 ubook kernel: [  309.413982] compiz[2304]: segfault at 0 ip 00007f83463da986 sp 00007ffe2791e7e0 error 4 in i965_dri.so[7f8345e02000+82d000]
Jan 10 21:31:33 ubook whoopsie[1041]: [21:31:33] Not online; processing later (/var/crash/_usr_bin_compiz.1000.crash).
Jan 10 21:31:37 ubook kernel: [  501.897435] compiz[2878]: segfault at 0 ip 00007fea9b4cf986 sp 00007fffeb208620 error 4 in i965_dri.so[7fea9aef7000+82d000]
Jan 10 21:32:10 ubook kernel: [  535.004251] compiz[2935]: segfault at 0 ip 00007fe184755986 sp 00007ffd580be4c0 error 4 in i965_dri.so[7fe18417d000+82d000]
Jan 10 21:32:42 ubook kernel: [  567.253863] compiz[2961]: segfault at 0 ip 00007ff37baeb986 sp 00007ffcefc72cf0 error 4 in i965_dri.so[7ff37b513000+82d000]
Jan 10 21:33:32 ubook compiz: pam_ecryptfs: seteuid error
Jan 10 21:33:37 ubook kernel: [  622.842729] compiz[2988]: segfault at 0 ip 00007f5676a79986 sp 00007ffd8dd0e060 error 4 in i965_dri.so[7f56764a1000+82d000]
Jan 10 21:34:03 ubook kernel: [  648.381177] compiz[3029]: segfault at 0 ip 00007fccc3aeb986 sp 00007fff440589f0 error 4 in i965_dri.so[7fccc3513000+82d000]
Jan 10 21:37:25 ubook kernel: [  850.395295] compiz[3053]: segfault at 0 ip 00007fd06faeb986 sp 00007ffd941bc3a0 error 4 in i965_dri.so[7fd06f513000+82d000]
Jan 10 21:38:42 ubook kernel: [  927.070989] compiz[3104]: segfault at 0 ip 00007f1d43086986 sp 00007fff1f7218a0 error 4 in i965_dri.so[7f1d42aae000+82d000]
Jan 10 21:44:28 ubook kernel: [  284.841546] compiz[1843]: segfault at 0 ip 00007f154ee7f986 sp 00007ffe953f1370 error 4 in i965_dri.so[7f154e8a7000+82d000]
Jan 10 21:46:11 ubook kernel: [  387.351275] compiz[2117]: segfault at 0 ip 00007fe938755986 sp 00007ffe6423ccf0 error 4 in i965_dri.so[7fe93817d000+82d000]
Jan 10 21:49:54 ubook kernel: [  609.928974] compiz[2188]: segfault at 0 ip 00007fc08b086986 sp 00007ffe34cbbaf0 error 4 in i965_dri.so[7fc08aaae000+82d000]
Jan 10 22:08:13 ubook kernel: [  537.926392] compiz[1668]: segfault at 0 ip 00007f9ee36d4986 sp 00007ffc23063ff0 error 4 in i965_dri.so[7f9ee30fc000+82d000]
Jan 10 22:09:03 ubook kernel: [  587.978088] compiz[2087]: segfault at 0 ip 00007f5539138986 sp 00007ffd74922110 error 4 in i965_dri.so[7f5538b60000+82d000]
```

I'm not certain of the system specs.  It's an old (~2008) HP notebook that someone gave me.  It has an Intel Core2 Duo and Intel graphics.  I installed Ubuntu on it and tried to find it a home, but no one wanted it.  I began to make use of it and now I'm using it every day.

---

### Post by kostkon on 2018-01-11
You could try the following:

Press CTRL+ALt+T to open a new terminal window, or if that's not possible, CTRL+ALT+F4 to enter a TTY session and give the following command to reset Compiz:
```
rm -rf ~/.compiz-1 ~/.config/compiz-1
```
then either logout if you are still on the desktop, or
```
setsid unity
```
and CTRL+ALT+F7 if you are in a TTY session.

---

### Post by monkeybrain20122 on 2018-01-11
Do you have Nvidia driver 387? Maybe [this]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1742095") and also[ here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1742302").

---

### Post by speartip on 2018-01-11
I'm having exactly the same problem. Fine until the last updates. Now everytime I click the Unity icon in the top left corner or try and shutdown the computer, Unity crashes. Intel integrated garphics on my system, so doubt its a graphics issue.

---

### Post by monkeybrain20122 on 2018-01-11
> **speartip said:**
> I'm having exactly the same problem. Fine until the last updates. Now everytime I click the Unity icon in the top left corner or try and shutdown the computer, Unity crashes. Intel integrated garphics on my system, so doubt its a graphics issue.

If you have intel graphic it could be due to the latest mesa update which affects people with certain intel machines [https://ubuntuforums.org/showthread.php?t=2381649](https://ubuntuforums.org/showthread.php?t=2381649)

---

### Post by jimnms on 2018-01-11
That is indeed the problem.  I tried installing the -proposed fix as suggested [here](https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/1735594/comments/48), but it gets a ton of dependency errors and it doesn't install.  I've put it into low graphics mode to limp along for now until a proper fix comes along.

---

### Post by monkeybrain20122 on 2018-01-11
> **jimnms said:**
> That is indeed the problem.  I tried installing the -proposed fix as suggested [here]("https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/1735594/comments/48"), but it gets a ton of dependency errors and it doesn't install.  I've put it into low graphics mode to limp along for now until a proper fix comes along.

Upgrading mesa to 17.3.1 should fix it. [https://launchpad.net/~paulo-miguel-dias/+archive/ubuntu/pkppa](https://launchpad.net/~paulo-miguel-dias/+archive/ubuntu/pkppa)

---

### Post by speartip on 2018-01-12
> **monkeybrain20122 said:**
> If you have intel graphic it could be due to the latest mesa update which affects people with certain intel machines [https://ubuntuforums.org/showthread.php?t=2381649](https://ubuntuforums.org/showthread.php?t=2381649)

That is indeed my problem. Worth noting in my case though is that Mesa 17.2.4 causes compiz to crash on the 4.13xx & 4.10xx kernel. However I installed the 4.4.0-109 kernel, & now all is well.

---

