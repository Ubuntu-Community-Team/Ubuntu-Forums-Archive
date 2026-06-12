---
title: "Ubuntu won't shutdown"
date: 2008-02-01
forum: General Help
---

### Post by aaargh486 on 2008-02-01
Whenever I try to shut my PC down, it does every task in /etc/rc0.d except for S70halt.
This means that pulling the plug is not dangerous, only really annoying and not very elegant. I have experimented a lot with the init system (11 second boot rulez) but I have not yet tampered with the shutdown system. Strangely enough, reboot goes just fine.

The contents of /etc/rc0.d are
```

total 8
lrwxrwxrwx 1 root root   13 2007-12-01 17:11 K01gdm -> ../init.d/gdm
lrwxrwxrwx 1 root root   16 2007-12-01 17:11 K16dhcdbd -> ../init.d/dhcdbd
lrwxrwxrwx 1 root root   20 2007-12-01 17:11 K18consolekit -> ../init.d/consolekit
lrwxrwxrwx 1 root root   20 2007-12-01 17:11 K25hwclock.sh -> ../init.d/hwclock.sh
lrwxrwxrwx 1 root root   26 2007-12-01 17:11 K59mountoverflowtmp -> ../init.d/mountoverflowtmp
lrwxrwxrwx 1 root root   22 2007-12-01 18:10 K85wpa-ifupdown -> ../init.d/wpa-ifupdown
-rw-r--r-- 1 root root  355 2007-10-04 13:17 README
lrwxrwxrwx 1 root root   18 2007-12-01 17:11 S20sendsigs -> ../init.d/sendsigs
lrwxrwxrwx 1 root root   17 2007-12-01 17:11 S30urandom -> ../init.d/urandom
lrwxrwxrwx 1 root root   22 2007-12-01 17:11 S31umountnfs.sh -> ../init.d/umountnfs.sh
lrwxrwxrwx 1 root root   18 2007-12-01 17:11 S40umountfs -> ../init.d/umountfs
lrwxrwxrwx 1 root root   20 2007-12-01 17:11 S60umountroot -> ../init.d/umountroot
lrwxrwxrwx 1 root root   14 2007-12-01 17:11 S70halt -> ../init.d/halt

```

All scripts are executed and finished, even S60umountroot (I tested it with strategically placed echo's).
But it doesn't even start S70halt (also tested with an echo on the first line).
I get no error messages, nothing at all, it just won't stop.
As rebooting goes fine, here are the contents of my rc6.d folder.

```
total 4
lrwxrwxrwx 1 root root  13 2007-12-01 17:11 K01gdm -> ../init.d/gdm
lrwxrwxrwx 1 root root  16 2007-12-01 17:11 K16dhcdbd -> ../init.d/dhcdbd
lrwxrwxrwx 1 root root  20 2007-12-01 17:11 K18consolekit -> ../init.d/consolekit
lrwxrwxrwx 1 root root  20 2007-12-01 17:11 K25hwclock.sh -> ../init.d/hwclock.sh
lrwxrwxrwx 1 root root  26 2007-12-01 17:11 K59mountoverflowtmp -> ../init.d/mountoverflowtmp
lrwxrwxrwx 1 root root  22 2007-12-01 18:10 K85wpa-ifupdown -> ../init.d/wpa-ifupdown
-rw-r--r-- 1 root root 353 2007-10-04 13:17 README
lrwxrwxrwx 1 root root  17 2007-12-01 18:07 S20makedev -> ../init.d/makedev
lrwxrwxrwx 1 root root  18 2007-12-01 17:11 S20sendsigs -> ../init.d/sendsigs
lrwxrwxrwx 1 root root  17 2007-12-01 17:11 S30urandom -> ../init.d/urandom
lrwxrwxrwx 1 root root  22 2007-12-01 17:11 S31umountnfs.sh -> ../init.d/umountnfs.sh
lrwxrwxrwx 1 root root  18 2007-12-01 17:11 S40umountfs -> ../init.d/umountfs
lrwxrwxrwx 1 root root  20 2007-12-01 17:11 S60umountroot -> ../init.d/umountroot
lrwxrwxrwx 1 root root  16 2007-12-01 17:11 S90reboot -> ../init.d/reboot

```

I don't get this at all. It's a very strange problem. 

Any blinding insights?

Thanks in advance, Kasper.

---

### Post by aaargh486 on 2008-02-01
Nothing?
Please give me some suggestions, I don't know what to do.

---

