---
title: "just installed dual boot with windows 8, a few questions"
date: 2013-01-06
forum: General Help
---

### Post by LLCoolJeff on 2013-01-06
Ok so after spending a few weeks reading about the issue in my spare time, I felt safe enough to try installing a dual boot with windows 8.

1. made ubuntu 12.10 usb stick
2. restarted > tried ubuntu > went to install
3. installer did not detect windows > used terminal to force ubiquity to recognize it ( $ WINOSDATA=true ubiquity )
4. went through recommended installation
5. upon reboot, secureboot would not boot ubuntu (Secure Boot failed with *ACCESS DENIED* or something like that)
6. turned off secureboot, ubuntu booted normally, windows boot failed with the error ( error: can't find command 'drivemap' error: invalid EFI file path.  Press any key to continue...)
7. booted ubuntu, downloaded boot-repair and did the recommended repair
8. Can now boot both OS's

My question is regarding secureboot, when I used the liveUSB version, it obviously passed secureboot, because it booted ubuntu liveUSB. Why then after the install would it not recognize ubuntu and force me to turn secureboot off?

I would like to turn it back on if possible, but it's not the end of the world if I cannot. Any ideas? Hopefully my list there will help anyone who is debating dual booting with windows 8

---

