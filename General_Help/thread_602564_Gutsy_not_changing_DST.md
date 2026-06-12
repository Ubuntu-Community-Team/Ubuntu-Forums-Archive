---
title: "Gutsy not changing DST"
date: 2007-11-04
forum: General Help
---

### Post by jimbren on 2007-11-04
I've got two laptops, one running Kubuntu Feisty and the other running Kubuntu Gutsy.  The Feisty laptop has correctly changed the system time for today's "fall back" Daylight Savings Time change, but the Gutsy laptop has not.

Odd thing is, both show the same data regarding when DST changes are supposed to take place. 

From Feisty (working):
```
jim@sasychica:~$ zdump -v /etc/localtime |grep 2007
/etc/localtime  Sun Mar 11 09:59:59 2007 UTC = Sun Mar 11 01:59:59 2007 PST isdst=0 gmtoff=-28800
/etc/localtime  Sun Mar 11 10:00:00 2007 UTC = Sun Mar 11 03:00:00 2007 PDT isdst=1 gmtoff=-25200
/etc/localtime  Sun Nov  4 08:59:59 2007 UTC = Sun Nov  4 01:59:59 2007 PDT isdst=1 gmtoff=-25200
/etc/localtime  Sun Nov  4 09:00:00 2007 UTC = Sun Nov  4 01:00:00 2007 PST isdst=0 gmtoff=-28800

```

and from Gutsy (not working):
```
jim@ingsoc:~$ zdump -v /etc/localtime |grep 2007
/etc/localtime  Sun Mar 11 09:59:59 2007 UTC = Sun Mar 11 01:59:59 2007 PST isdst=0 gmtoff=-28800
/etc/localtime  Sun Mar 11 10:00:00 2007 UTC = Sun Mar 11 03:00:00 2007 PDT isdst=1 gmtoff=-25200
/etc/localtime  Sun Nov  4 08:59:59 2007 UTC = Sun Nov  4 01:59:59 2007 PDT isdst=1 gmtoff=-25200
/etc/localtime  Sun Nov  4 09:00:00 2007 UTC = Sun Nov  4 01:00:00 2007 PST isdst=0 gmtoff=-28800

```

Is anyone else having a similar issue?

I realize that I can manually change the system time or run nptdate and synchronize the time with a remote time server, but I'm wondering why Gutsy hasn't corrected the time on it's own--particularly since 6.10 was the official release during the last DST change, and it went off flawlessly.

thanks,

jimbo

---

### Post by phobos512 on 2007-11-04
Yeah I've got the same issue.  I'm still very new @ Ubuntu, but I looked in the time and data menu under Administration and update was set to manual.  I changed it to network update and it required me to download the package to do so.  Oh and look at that while I was typing it updated.  How odd.  Maybe you just have to wait for an update to come through, this took about 10 minutes to do it automatically...

---

### Post by jimbren on 2007-11-05
Thanks for the tip.  I got lazy and ended up syncing through nptdate and a time server, but it would be nice to know for the future.

Thanks,

jimbo

---

### Post by strange_cathect on 2007-11-11
I had a similar problem.  I went into Synaptic and then did a complete reinstall of the "ntpdate" package.  After the install the time corrected itself.  Must be some hiccup in the upgrade to Ubuntu 7.

---

