---
title: "Adept not opening"
date: 2007-02-08
forum: General Help
---

### Post by BWF89 on 2007-02-08
It seems like every other day when I go into Adept whether it's to update something or install something I get the message that I can't make changes with Adept because some other program is using it. And tells me to close the program and try again.

It doesn't matter if I log out and log back in, or even reboot or shutdown the computer and log back in.  Theres no rhyme or reason to it. I'll just go to log in sometime and it'll just work and sometimes it won't.

Why is this happening, and how can I find out what other program is using Adept?

---

### Post by taurus on 2007-02-08
```
ps -A
```
And look in that list.

---

### Post by BWF89 on 2007-02-09
> **taurus said:**
> ```
ps -A
```
And look in that list.
I entered that and got this. I don't see anything relating to apt-get or Adept in there. And now that were on the process what is the command for terminating a running app via Konsole?
```
PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 migration/0
    3 ?        00:00:00 ksoftirqd/0
    4 ?        00:00:00 watchdog/0
    5 ?        00:00:00 events/0
    6 ?        00:00:00 khelper
    7 ?        00:00:00 kthread
    9 ?        00:00:00 kblockd/0
   10 ?        00:00:00 kacpid
   11 ?        00:00:00 kacpi_notify
   88 ?        00:00:00 kseriod
  120 ?        00:00:00 pdflush
  121 ?        00:00:00 pdflush
  122 ?        00:00:00 kswapd0
  123 ?        00:00:00 aio/0
 1724 ?        00:00:00 khubd
 1747 ?        00:00:00 khpsbpkt
 1760 ?        00:00:00 knodemgrd_0
 1845 ?        00:00:00 kjournald
 1920 ?        00:00:00 logd
 2066 ?        00:00:00 udevd
 2784 ?        00:00:00 shpchpd
 2959 ?        00:00:00 kpsmoused
 3022 ?        00:00:00 kgameportd
 3286 ?        00:00:00 dhclient3
 3616 tty1     00:00:00 getty
 3617 tty2     00:00:00 getty
 3618 tty3     00:00:00 getty
 3619 tty4     00:00:00 getty
 3620 tty5     00:00:00 getty
 3621 tty6     00:00:00 getty
 3824 ?        00:00:00 acpid
```

---

### Post by taurus on 2007-02-09
Run this command from a terminal again and see what's the output.

```
sudo apt-get update
```

---

### Post by BWF89 on 2007-02-10
I got
```
Ign http://us.archive.ubuntu.com edgy-backports/multiverse Translation-en_US
Hit http://archive.ubuntu.com edgy Release
Hit http://us.archive.ubuntu.com edgy Release
Hit http://us.archive.ubuntu.com edgy-updates Release
Hit http://us.archive.ubuntu.com edgy-backports Release
Hit http://archive.ubuntu.com edgy/universe Packages
Hit http://us.archive.ubuntu.com edgy/main Packages
Hit http://archive.ubuntu.com edgy/multiverse Packages
Hit http://us.archive.ubuntu.com edgy/restricted Packages
Hit http://us.archive.ubuntu.com edgy/main Sources
Hit http://us.archive.ubuntu.com edgy/restricted Sources
Hit http://us.archive.ubuntu.com edgy/universe Packages
Hit http://us.archive.ubuntu.com edgy/universe Sources
Hit http://us.archive.ubuntu.com edgy-updates/main Packages
Hit http://us.archive.ubuntu.com edgy-updates/restricted Packages
Hit http://us.archive.ubuntu.com edgy-updates/main Sources
Hit http://us.archive.ubuntu.com edgy-updates/restricted SourcesA
Get:8 http://security.ubuntu.com edgy-security/main Packages [62.2kB]
Hit http://us.archive.ubuntu.com edgy-backports/main Packages
Hit http://us.archive.ubuntu.com edgy-backports/restricted Packages
Hit http://us.archive.ubuntu.com edgy-backports/universe Packages
Hit http://us.archive.ubuntu.com edgy-backports/multiverse Packages
Hit http://us.archive.ubuntu.com edgy-backports/main Sources
Hit http://us.archive.ubuntu.com edgy-backports/restricted Sources
Hit http://us.archive.ubuntu.com edgy-backports/universe Sources
Hit http://us.archive.ubuntu.com edgy-backports/multiverse Sources
Get:9 http://security.ubuntu.com edgy-security/restricted Packages [5689B]
Get:10 http://security.ubuntu.com edgy-security/main Sources [12.3kB]
Get:11 http://security.ubuntu.com edgy-security/restricted Sources [923B]
Get:12 http://security.ubuntu.com edgy-security/universe Packages [31.9kB]
Get:13 http://security.ubuntu.com edgy-security/universe Sources [3432B]
Fetched 168kB in 1s (101kB/s)
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
```
So I setup the root account. Ran "dpkg --configure -a". Ran Adept, and it worked.

But when I figured I'd test it out and download the package "abuse-sfx" it said it couldn't run because "There was an error committing changes. Or commit would break changes". So I decided to just click "Fetch Updates" at the top of and it goes through all the repos like it usually does but than nothing happened. I wanted to see if this problem was just with the Abuse game or went into other things as well so I tried to install "openclipart-openoffice.org" package and got the same message.

---

### Post by BWF89 on 2007-02-14
bump

---

