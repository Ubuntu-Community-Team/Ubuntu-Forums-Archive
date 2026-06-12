---
title: "Problems with System time"
date: 2007-04-01
forum: General Help
---

### Post by dreadlord_chris on 2007-04-01
OK, first off, this is not a Daylight Savings issue - my box correctly adjusted for DST at the proper time.

Nor is this a CMOS battery issue - already checked.

This problem started yesterday.

Yesterday I noticed that my sys monitor app (gkrellm) was showing the time as 7 hours in the future - it was 9pm here but showing 4am the next morning. So I open the KDE Control Center and go to Date & Time. It shows the correct Time Zone (Los Angeles) - but the time shown is incorrect (+7 hours). So I set the correct time, click Apply & OK. Gkrellm still shows the incorrect time. I then add the Clock applet to my panel - it shows the correct time.

Also, timestamps in Kopete show the incorrect time (same time shown by gkrellm) - as do the filesystem timestamps when creating or modifying files.

And now things get weird.....

So now I have 2 clocks on my desktop showing 2 different times!?!

I go back Time & Date settings - it's reverted back (err forward) to the wrong time again!

This time I mark "Set time & date automatically", click apply - and the time is adjusted to the correct time. But still the 2 clocks are different. And if/when I re-open the Time & Date settings it's once again jumped 7 hours ahead.

Searched the forums for Time related issues - mostly all I could find were DST problems. Although there was a couple hints that maybe UTC was the problem. It was suggested to turn off UTC. Mine was already set to off, but I figured what the heck, so I turned it on. This made no difference.

This appears to be wrong:
```

chris@HAL421:~$ zdump -v /etc/localtime
/etc/localtime  Fri Dec 13 20:45:52 1901 UTC = Fri Dec 13 20:45:52 1901 UTC isdst=0 gmtoff=0
/etc/localtime  Sat Dec 14 20:45:52 1901 UTC = Sat Dec 14 20:45:52 1901 UTC isdst=0 gmtoff=0
/etc/localtime  Mon Jan 18 03:14:07 2038 UTC = Mon Jan 18 03:14:07 2038 UTC isdst=0 gmtoff=0
/etc/localtime  Tue Jan 19 03:14:07 2038 UTC = Tue Jan 19 03:14:07 2038 UTC isdst=0 gmtoff=0
chris@HAL421:~$ zdump -v PDT
PDT  Fri Dec 13 20:45:52 1901 UTC = Fri Dec 13 20:45:52 1901 PDT isdst=0 gmtoff=0
PDT  Sat Dec 14 20:45:52 1901 UTC = Sat Dec 14 20:45:52 1901 PDT isdst=0 gmtoff=0
PDT  Mon Jan 18 03:14:07 2038 UTC = Mon Jan 18 03:14:07 2038 PDT isdst=0 gmtoff=0
PDT  Tue Jan 19 03:14:07 2038 UTC = Tue Jan 19 03:14:07 2038 PDT isdst=0 gmtoff=0
chris@HAL421:~$

```

Any ideas?

---

### Post by acormack on 2007-04-01
I think you have ticked the box to use Grenwich Mean Time (UTC)  so you are displayong +7 hours from your real time zone.

---

### Post by Omnicef on 2007-04-01
My problem is very similiar. Except...... It is wrong when I am not connected to the internet and is correct when I am connected to the internet. Do you experience this as well?

---

### Post by dreadlord_chris on 2007-04-01
> **Omnicef said:**
> My problem is very similiar. Except...... It is wrong when I am not connected to the internet and is correct when I am connected to the internet. Do you experience this as well?

No, I have a direct connection - so, it's always on...

---

### Post by dreadlord_chris on 2007-04-01
> **acormack said:**
> I think you have ticked the box to use Grenwich Mean Time (UTC)  so you are displayong +7 hours from your real time zone.

uh....
[quote=dreadlord_chris]
Searched the forums for Time related issues - mostly all I could find were DST problems. Although there was a couple hints that maybe UTC was the problem. It was suggested to turn off UTC. Mine was already set to off, but I figured what the heck, so I turned it on. This made no difference.
[/quote]

Also, there is no box to tick for UTC - I had to manually edit /etc/default/rcS

---

### Post by dreadlord_chris on 2007-04-01
OK, I fixed it.

seems somehow my /etc/localtime file up and disappeared??

So I booted into the LiveCD, mounted my root partition, and copied the file over from the CD...

All back to fine now....

---

### Post by krazyd on 2007-08-13
Hmm, seems that you have come across the [Year 2038 Problem]("http://en.wikipedia.org/wiki/Year_2038_problem"). Not sure how you tripped it, but with that date, this is definitely your problem.

---

