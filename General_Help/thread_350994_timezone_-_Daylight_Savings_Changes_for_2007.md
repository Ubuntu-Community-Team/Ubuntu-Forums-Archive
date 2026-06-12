---
title: "timezone - Daylight Savings Changes for 2007"
date: 2007-02-01
forum: General Help
---

### Post by mungewell on 2007-02-01
Hi all,
Due to that meddling George W Bush  :-) the date on which Daylight Saving Time starts and ends is changing this year (2007) for people in North America.

I was attempting to confirm that the change has made its way onto my system, but:

1) Can't find a way of dumping the contents of the appropriate timezone file from /usr/share/zoneinfo/... in a readable form.

2) The package which provides these ('base/locales' for Dapper) was last changed on Tue, 16 May 2006. which suggests that it might be out of date.....

Can anyone confirm whether I have an excuse for being late to work when the clocks change?
Simon

---

### Post by emarkay on 2007-02-01
Interesting - also I haven't looked, but Indiana moved some timezones last October, too.  
Just a "heads-up"!

---

### Post by mungewell on 2007-02-01
In typical fashion answering my own post...... * PANIC * the clocks will be wrong!

I believe that the timezone data is derived from files posted here:
[ftp://elsie.nci.nih.gov/pub/](ftp://elsie.nci.nih.gov/pub/)

Locales 2.3.18 appears to use 2006g, latest is 2007a.

Since 2007a is wrong (for Edmonton) is highly likely that 2006g isn't right either.

Have raised bug.
[https://launchpad.net/ubuntu/+source/langpack-locales/+bug/82698](https://launchpad.net/ubuntu/+source/langpack-locales/+bug/82698)

Simon.

---

### Post by compudude86 on 2007-03-05
apparently,
this is a MAJOR ISSUE in the world of information technology, as most systems rely on the proper time for several tasks and interfacing with other computers. i would think there would be a patch out for either ubuntu or linux, as MS already has patches out for their OS. if they don't, its gonna cause problems for everyone whos implemented ubuntu/linux in their server environments. afaik, daylight savings time starts march 11th. so i think thats 6 days. hopefully if a patch hasnt been released, we will see one soon.

---

### Post by tubasoldier on 2007-03-05
daylight savings time is rediculous in and of itself. Benjamin Franklin suggested it as a joke.

---

### Post by compudude86 on 2007-03-05
yes it is a joke, and i have no clue why we still use it. and as far as the fix, go to your console, run *zdump -v /etc/localtime | grep 2007* and read the output. if it looks like this,
```
/etc/localtime  Sun Mar 11 07:59:59 2007 UTC = Sun Mar 11 01:59:59 2007 CST isdst=0 gmtoff=-21600
/etc/localtime  Sun Mar 11 08:00:00 2007 UTC = Sun Mar 11 03:00:00 2007 CDT isdst=1 gmtoff=-18000
/etc/localtime  Sun Nov  4 06:59:59 2007 UTC = Sun Nov  4 01:59:59 2007 CDT isdst=1 gmtoff=-18000
/etc/localtime  Sun Nov  4 07:00:00 2007 UTC = Sun Nov  4 01:00:00 2007 CST isdst=0 gmtoff=-21600

```

then you are good. as long as it has that mar 11 in there, it is up to date.

---

