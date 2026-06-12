---
title: "NTP shows large negative frequency and time is off"
date: 2008-02-19
forum: General Help
---

### Post by fowie on 2008-02-19
I have been running my Gutsy installation for a few months, two days ago I noticed the time was off by 1/2 hour.  I checked and NTP is set up, time zone is correct, but the time would not sync.  I switched off NTP and set the time manually and the time got off by about 2-3 hours, so it could be my battery, but I never switch off my computer.  I turned NTP back on and it would not keep time.  If I run 
```

ntptime

```
I get:
```

ntp_gettime() returns code 5 (ERROR)
  time cb6615f9.48b2a000  Tue, Feb 19 2008 19:59:05.283, (.283976),
  maximum error 16384000 us, estimated error 16384000 us
ntp_adjtime() returns code 5 (ERROR)
  modes 0x0 (),
  offset 0.000 us, frequency -150.880 ppm, interval 1 s,
  maximum error 16384000 us, estimated error 16384000 us,
  status 0x40 (UNSYNC),
  time constant 4, precision 1.000 us, tolerance 512 ppm,

```
I get a feeling that the frequency -150.880ppm is bad, any ideas how to fix this?

---

### Post by jpkotta on 2008-02-23
I'm having similar issues.  I joined this thread:
[http://ubuntuforums.org/showthread.php?p=4389917](http://ubuntuforums.org/showthread.php?p=4389917)

---

